---
title: "Crear una tabla (Tutorial) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "crear tablas"
ms.assetid: 653f2dd3-36a2-4bd5-8703-71a57d244661
caps.latest.revision: 17
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Crear una tabla (Tutorial)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../includes/tsql-appliesto-ss2008-all-md.md)]

Para crear una tabla, debe proporcionar un nombre para ésta además de los nombres y los tipos de datos de cada columna de la tabla. También es recomendable indicar si se permiten valores NULL en cada columna. Para crear una tabla, debe tener el permiso `CREATE TABLE` y el permiso `ALTER SCHEMA` en el esquema que contiene la tabla. El rol fijo de base de datos `db_ddladmin` tiene dichos permisos.  
  
La mayoría de las tablas tienen una clave principal, que se compone de una o varias columnas de la tabla. Una clave principal siempre es única. [!INCLUDE[ssDE](../includes/ssde-md.md)] exigirá la restricción de que el valor de la clave principal no se puede repetir en la tabla.  
  
Para obtener una lista de tipos de datos y vínculos para una descripción de cada uno, consulte [Tipos de datos &#40;Transact-SQL&#41;](../t-sql/data-types/data-types-transact-sql.md).  
  
> [!NOTE]  
> [!INCLUDE[ssDE](../includes/ssde-md.md)] se puede instalar para distinguir mayúsculas de minúsculas o no distinguir mayúsculas de minúsculas. Si se instala [!INCLUDE[ssDE](../includes/ssde-md.md)] para distinguir mayúsculas de minúsculas, los nombres de objetos siempre deben tener las mismas mayúsculas y minúsculas. Por ejemplo, una tabla denominada OrderData es diferente de la denominada ORDERDATA. Si se instala [!INCLUDE[ssDE](../includes/ssde-md.md)] para no distinguir mayúsculas de minúsculas, esos dos nombres de tablas se consideran la misma tabla y ese nombre solo se puede utilizar una vez.  
  
### Para crear una base de datos que contenga la nueva tabla  
  
-   Escriba el código siguiente en una ventana del Editor de consultas.  
  
    ```  
    USE master;  
    GO  
  
    --Delete the TestData database if it exists.  
    IF EXISTS(SELECT * from sys.databases WHERE name='TestData')  
    BEGIN  
        DROP DATABASE TestData;  
    END  
  
    --Create a new database called TestData.  
    CREATE DATABASE TestData;  
    Press the F5 key to execute the code and create the database.  
    ```  
  
### Cambie la conexión del Editor de consultas a la base de datos TestData  
  
-   En una ventana del Editor de consultas, escriba y ejecute el siguiente código para cambiar la conexión a la base de datos `TestData` .  
  
    ```  
    USE TestData  
    GO  
    ```  
  
### Para crear una tabla  
  
-   En una ventana del Editor de consultas, escriba y ejecute el siguiente código para crear una tabla sencilla denominada `Products`. Las columnas de la tabla son `ProductID`, `ProductName`, `Price`y `ProductDescription`. La columna `ProductID` es la clave principal de la tabla. `int`, `varchar(25)`, `money`y `text` son todos los tipos de datos. Solo las columnas `Price` y `ProductionDescription` pueden no tener datos cuando se inserta o cambia una fila. Esta instrucción contiene un elemento opcional (`dbo.`) denominado esquema. El esquema es el objeto de base de datos propietario de la tabla. Si es un administrador, `dbo` es el esquema predeterminado. `dbo` hace referencia al propietario de la base de datos.  
  
    ```  
    CREATE TABLE dbo.Products  
       (ProductID int PRIMARY KEY NOT NULL,  
        ProductName varchar(25) NOT NULL,  
        Price money NULL,  
        ProductDescription text NULL)  
    GO  
    ```  
  
## Siguiente tarea de la lección  
[Insertar y actualizar datos en una tabla &#40;Tutorial&#41;](../t-sql/inserting-and-updating-data-in-a-table-tutorial.md)  
  
## Vea también  
[CREATE TABLE &#40;Transact-SQL&#41;](../t-sql/statements/create-table-transact-sql.md)  
  
  
  
