---
title: "Eliminar funciones definidas por el usuario | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-udf"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: db1d668a-23b7-4757-a9c5-1bd848ba7f6d
caps.latest.revision: 7
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 7
---
# Eliminar funciones definidas por el usuario
  Puede eliminar (quitar) las funciones definidas por el usuario en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]  
  
 **En este tema**  
  
-   **Antes de empezar:**  
  
     [Limitaciones y restricciones](#Restrictions)  
  
     [Seguridad](#Security)  
  
-   **Para eliminar una función definida por el usuario, usando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="Restrictions"></a> Limitaciones y restricciones  
  
-   No podrá eliminar la función si hay vistas o funciones de Transact-SQL en la base de datos que hagan referencia a esta función y que fueron creadas con SCHEMABINDING; tampoco funcionará si existen columnas calculadas o restricciones CHECK o DEFAULT que hacen referencia a la función.  
  
-   No podrá eliminar la función si existen columnas calculadas que hagan referencia a esta función y que hayan sido indizadas.  
  
###  <a name="Security"></a> Seguridad  
  
####  <a name="Permissions"></a> Permisos  
 Requiere el permiso ALTER en el esquema al que pertenece la función o el permiso CONTROL en la función.  
  
##  <a name="SSMSProcedure"></a> Usar SQL Server Management Studio  
  
#### Para eliminar un perfil definido por la función  
  
1.  Haga clic en el signo más junto a la base de datos que contenga la función que desea modificar.  
  
2.  Haga clic en el signo más junto a la carpeta **Programación** .  
  
3.  Haga clic en el signo más junto a la carpeta que contenga la función que desea modificar:  
  
    -   Table-valued Function  
  
    -   Función con valor escalar  
  
    -   Función de agregado  
  
4.  Haga clic con el botón derecho en la función que quiera eliminar y seleccione **Eliminar**.  
  
5.  En el cuadro de diálogo **Eliminar objeto** , haga clic en **Aceptar**.  
  
    > [!IMPORTANT]  
    >  Haga clic en **Mostrar dependencias** en el cuadro de diálogo **Eliminar objeto** para abrir el cuadro de diálogo **Dependencias de *nombre_función***. De este modo, mostrará todos los objetos que dependen de la función y todos los objetos de los que la función depende.  
  
##  <a name="TsqlProcedure"></a> Usar Transact-SQL  
  
#### Para eliminar un perfil definido por la función  
  
1.  En el **Explorador de objetos**, conéctese a una instancia del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  En la barra de Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue el siguiente ejemplo en la ventana de consulta y haga clic en **Ejecutar**.  
  
    ```  
    -- creates function called “Sales.ufn_SalesByStore”  
    USE AdventureWorks2012;  
    GO  
    CREATE FUNCTION Sales.ufn_SalesByStore (@storeid int)  
    RETURNS TABLE  
    AS  
    RETURN   
    (  
        SELECT P.ProductID, P.Name, SUM(SD.LineTotal) AS 'Total'  
        FROM Production.Product AS P   
        JOIN Sales.SalesOrderDetail AS SD ON SD.ProductID = P.ProductID  
        JOIN Sales.SalesOrderHeader AS SH ON SH.SalesOrderID = SD.SalesOrderID  
        JOIN Sales.Customer AS C ON SH.CustomerID = C.CustomerID  
        WHERE C.StoreID = @storeid  
        GROUP BY P.ProductID, P.Name  
    );  
    GO  
    ```  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- determines if function exists in database  
    IF OBJECT_ID (N'Sales.fn_SalesByStore', N'IF') IS NOT NULL  
    -- deletes function  
        DROP FUNCTION Sales.fn_SalesByStore;  
    GO  
    ```  
  
 Para obtener más información, vea [DROP FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/drop-function-transact-sql.md).  
  
  