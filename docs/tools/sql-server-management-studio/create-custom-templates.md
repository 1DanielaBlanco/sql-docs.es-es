---
title: "Crear plantillas personalizadas | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
helpviewer_keywords: 
  - "tql"
  - "plantillas [Transact-SQL], creación"
  - "plantillas [Transact-SQL]"
ms.assetid: 41098e78-b482-410e-bfe8-2ac10769ac4a
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Crear plantillas personalizadas
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] incorpora plantillas para muchas tareas comunes, pero el auténtico valor reside en la posibilidad de crear una plantilla personalizada para un script complejo que tenga que crear con frecuencia. En esta práctica, creará un script sencillo con unos pocos parámetros; pero las plantillas también son útiles para scripts largos y repetitivos.  
  
## Usar plantillas personalizadas  
  
#### Para crear una plantilla personalizada  
  
1.  En el Explorador de plantillas, expanda **Plantillas de SQL Server**, haga clic con el botón derecho en **Procedimiento almacenado**, seleccione **Nueva** y, después, haga clic en **Carpeta**.  
  
2.  Escriba **Custom** como nombre de la nueva carpeta de plantillas y, después, pulse ENTRAR.  
  
3.  Haga clic con el botón derecho en **Custom**, seleccione **Nueva** y después haga clic en **Plantilla**.  
  
4.  Escriba **WorkOrdersProc** como nombre de la plantilla nueva y, después, pulse **Entrar**.  
  
5.  Haga clic con el botón derecho en **WorkOrdersProc** y, después, haga clic en **Editar**.  
  
6.  En el cuadro de diálogo **Conectar al motor de base de datos** compruebe la información de conexión y, después, haga clic en **Conectar**.  
  
7.  En el Editor de consultas, escriba el siguiente script para crear un procedimiento almacenado que busque pedidos de una pieza concreta, en este caso, una cuchilla (Blade). Puede copiar y pegar el código de la ventana del tutorial.  
  
    ```  
    USE AdventureWorks20012;  
    GO  
    IF EXISTS (  
    SELECT *   
       FROM INFORMATION_SCHEMA.ROUTINES   
       WHERE SPECIFIC_NAME = 'WorkOrdersForBlade')  
       DROP PROCEDURE dbo.WorkOrdersForBlade;  
    GO  
    CREATE PROCEDURE dbo.WorkOrdersForBlade  
    AS  
    SELECT Name, WorkOrderID   
    FROM Production.WorkOrder AS WO  
    JOIN Production.Product AS Prod  
    ON WO.ProductID = Prod.ProductID  
    WHERE Name = 'Blade';  
    GO  
    ```  
  
8.  Pulse F5 para ejecutar este script y crear el procedimiento **WorkOrdersForBlade**.  
  
9. En el Explorador de objetos, haga clic con el botón derecho en el servidor y, después, en **Nueva consulta**. Se abrirá una ventana nueva del Editor de consultas.  
  
10. En el Editor de consultas, escriba **EXECUTE dbo.WorkOrdersForBlade** y, después, pulse F5 para ejecutar la consulta. Confirme que el panel **Resultados** devuelve una lista de los pedidos de trabajo relativos a cuchillas.  
  
11. Edite el script de la plantilla (el script del paso 7) y reemplace el nombre del producto (Blade) por el parámetro ***\<*product_name**, **nvarchar(50)**, **name*>***, en cuatro lugares.  
  
    > [!NOTE]  
    > Los parámetros requieren tres elementos: el nombre del parámetro que desea reemplazar, el tipo de datos del parámetro y un valor predeterminado para el parámetro.  
  
12. Ahora, el script debe tener el aspecto siguiente:  
  
    ```  
    USE AdventureWorks20012;  
    GO  
    IF EXISTS (  
    SELECT *   
       FROM INFORMATION_SCHEMA.ROUTINES   
       WHERE SPECIFIC_NAME = 'WorkOrdersFor<product_name, nvarchar(50), name>')  
       DROP PROCEDURE dbo.WorkOrdersFor<product_name, nvarchar(50), name>;  
    GO  
    CREATE PROCEDURE dbo.WorkOrdersFor<product_name, nvarchar(50), name>  
    AS  
    SELECT Name, WorkOrderID   
    FROM Production.WorkOrder AS WO  
    JOIN Production.Product AS Prod  
    ON WO.ProductID = Prod.ProductID  
    WHERE Name = '<product_name, nvarchar(50), name>';  
    GO  
    ```  
  
13. En el menú **Archivo**, haga clic en **Guardar WorkOrdersProc.sql** para guardar la plantilla.  
  
#### Para probar la plantilla personalizada  
  
1.  En el Explorador de plantillas, expanda **Procedimiento almacenado** y **Custom** y, después, haga doble clic en **WorkOrderProc**.  
  
2.  En el cuadro de diálogo **Conectarse al motor de base de datos**, rellene la información de conexión y luego haga clic en **Conectar**. Se abrirá una ventana nueva del Editor de consultas, que incluye el contenido de la plantilla **WorkOrderProc**.  
  
3.  En el menú **Consulta** , haga clic en **Especificar valores para parámetros de plantilla**.  
  
4.  En el cuadro de diálogo **Reemplazar parámetros de plantilla**, para el valor **product_name**, escriba **FreeWheel** (sobrescribiendo el contenido predeterminado) y, después, haga clic en **Aceptar** para cerrar el cuadro de diálogo **Reemplazar parámetros de plantilla** y modifique el script en el Editor de consultas.  
  
5.  Presione F5 para ejecutar la consulta y crear el procedimiento.  
  
## Siguiente tarea de la lección  
[Guardar scripts como proyectos o soluciones](../../tools/sql-server-management-studio/save-scripts-as-projects-or-solutions.md)  
  
  
  
