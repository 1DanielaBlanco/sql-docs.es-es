---
title: Relleno de una tabla con los datos jerárquicos existentes | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: ''
ms.component: tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- HierarchyID
ms.assetid: fd943d84-dbe6-4a05-912b-c88164998d80
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: e2582323d122a3b8cd8042fc028d8da73fb8a1a1
ms.sourcegitcommit: d6881107b51e1afe09c2d8b88b98d075589377de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/28/2018
---
# <a name="lesson-1-2---populating-a-table-with-existing-hierarchical-data"></a>Lección 1-2: Rellenar una tabla con los datos jerárquicos existentes
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]
Esta tarea crea una nueva tabla y la rellena con los datos de la tabla **EmployeeDemo** . Esta tarea consta de los pasos siguientes:  
  
-   Cree una nueva tabla que contenga una columna **hierarchyid** . Esta columna podría reemplazar a las columnas **EmployeeID** y **ManagerID** existentes. Sin embargo, usted conservará esas columnas. La razón de ello es porque alguna de las aplicaciones existentes podría hacer referencia a esas columnas, y también para ayudarle a entender los datos una vez realizada la transferencia. La definición de tabla especifica que **OrgNode** es la clave principal, que requiere que la columna contenga valores únicos. El índice agrupado sobre la columna **OrgNode** almacenará la fecha en secuencia **OrgNode** .  
  
-   Cree una tabla temporal que se utilizará para averiguar cuántos empleados notifican directamente a cada gerente.  
  
-   Rellene la nueva tabla con los datos de la tabla **EmployeeDemo** .  
  
### <a name="to-create-a-new-table-named-neworg"></a>Para crear una nueva tabla denominada NewOrg  
  
-   En una ventana del Editor de consultas, ejecute el siguiente código para crear una nueva tabla denominada **HumanResources.NewOrg**:  
  
    ```  
    CREATE TABLE HumanResources.NewOrg  
    (  
      OrgNode hierarchyid,  
      EmployeeID int,  
      LoginID nvarchar(50),  
      ManagerID int  
    CONSTRAINT PK_NewOrg_OrgNode  
      PRIMARY KEY CLUSTERED (OrgNode)  
    );  
    GO  
    ```  
  
### <a name="to-create-a-temporary-table-named-children"></a>Para crear una tabla temporal denominada #Elementos secundarios  
  
1.  Cree una tabla temporal denominada **#Elementos secundarios** con una columna denominada **Num** que contendrá el número de elementos secundarios de cada nodo:  
  
    ```  
    CREATE TABLE #Children   
       (  
        EmployeeID int,  
        ManagerID int,  
        Num int  
    );  
    GO  
    ```  
  
2.  Agregue un índice que acelerará significativamente la consulta que rellena la tabla **NewOrg** :  
  
    ```  
    CREATE CLUSTERED INDEX tmpind ON #Children(ManagerID, EmployeeID);  
    GO  
    ```  
  
### <a name="to-populate-the-neworg-table"></a>Para rellenar la tabla NewOrg  
  
1.  Las consultas recursivas prohíben las subconsultas con agregados. En su lugar, rellene la tabla **#Elementos secundarios** con el código siguiente, que usa el método [ROW_NUMBER ()](../../t-sql/functions/row-number-transact-sql.md) para rellenar la columna **Num** :  
  
    ```  
    INSERT #Children (EmployeeID, ManagerID, Num)  
    SELECT EmployeeID, ManagerID,  
      ROW_NUMBER() OVER (PARTITION BY ManagerID ORDER BY ManagerID)   
    FROM HumanResources.EmployeeDemo  
    GO 
    ```  
  
2.  Revise la tabla **#Elementos secundarios** . Observe cómo la columna **Num** contiene números secuenciales para cada administrador.  
  
    ```  
    SELECT * FROM #Children ORDER BY ManagerID, Num  
    GO  
  
    ```  
  
    [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  

    ```
    EmployeeID  ManagerID   Num
    1   NULL    1
    2   1   1
    16  1   2
    25  1   3
    234 1   4
    263 1   5
    273 1   6
    3   2   1
    4   3   1
    5   3   2
    6   3   3
    7   3   4
    ```


3.  Rellene la tabla **NewOrg** . Use los métodos GetRoot y ToString para concatenar los valores **Num** en formato **hierarchyid** y, después, actualice la columna **OrgNode** con los valores jerárquicos resultantes:  
  
    ```  
    WITH paths(path, EmployeeID)   
    AS (  
    -- This section provides the value for the root of the hierarchy  
    SELECT hierarchyid::GetRoot() AS OrgNode, EmployeeID   
    FROM #Children AS C   
    WHERE ManagerID IS NULL   

    UNION ALL   
    -- This section provides values for all nodes except the root  
    SELECT   
    CAST(p.path.ToString() + CAST(C.Num AS varchar(30)) + '/' AS hierarchyid),   
    C.EmployeeID  
    FROM #Children AS C   
    JOIN paths AS p   
       ON C.ManagerID = P.EmployeeID   
    )  
    INSERT HumanResources.NewOrg (OrgNode, O.EmployeeID, O.LoginID, O.ManagerID)  
    SELECT P.path, O.EmployeeID, O.LoginID, O.ManagerID  
    FROM HumanResources.EmployeeDemo AS O   
    JOIN Paths AS P   
       ON O.EmployeeID = P.EmployeeID  
    GO 
    ```  
  
4.  Una columna **hierarchyid** se entiende mejor al convertirla al formato de caracteres. Revise los datos de la tabla **NewOrg** ; para ello, ejecute el código siguiente, que contiene dos representaciones de la columna **OrgNode** :  
  
    ```  
    SELECT OrgNode.ToString() AS LogicalNode, *   
    FROM HumanResources.NewOrg   
    ORDER BY LogicalNode;  
    GO  
    ```  
  
    La columna **LogicalNode** convierte la columna **hierarchyid** en un texto más fácil de leer que representa la jerarquía. En las tareas restantes, usará el método `ToString()` para mostrar el formato lógico de las columnas **hierarchyid** .  
  
5.  Elimine la tabla temporal, que ya no se necesita:  
  
    ```  
    DROP TABLE #Children  
    GO  
    ```  
  
La tarea siguiente creará los índices para la estructura jerárquica.  
  
## <a name="next-task-in-lesson"></a>Siguiente tarea de la lección  
[Optimizar la tabla NewOrg](../../relational-databases/tables/lesson-1-3-optimizing-the-neworg-table.md)  
  
  
  
