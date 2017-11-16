---
title: "Optimización del procesamiento de OLTP en memoria JSON | Microsoft Docs"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: json
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9c5adb1-3209-4186-bc10-8e41a26f5e57
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 9045ebe77cf2f60fecad22672f3f055d8c5fdff2
ms.openlocfilehash: bb35a5255b35b93cd42e83bd17d9efdcf751bc84
ms.contentlocale: es-es
ms.lasthandoff: 07/31/2017

---
# <a name="optimize-json-processing-with-in-memory-oltp"></a>Optimización del procesamiento de OLTP en memoria JSON
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

SQL Server y Azure SQL Database permiten trabajar con texto en formato JSON. Para aumentar el rendimiento de las consultas que procesan datos JSON, puede almacenar documentos JSON en tablas optimizadas para memoria mediante las columnas de cadena estándar (tipo NVARCHAR). Al almacenar datos JSON en tablas con optimización para memoria, se aumenta el rendimiento de consulta gracias a que se aprovecha el acceso a los datos en memoria sin bloqueo.

## <a name="store-json-in-memory-optimized-tables"></a>Almacenamiento de datos JSON en tablas con optimización para memoria
En el ejemplo siguiente se crea una tabla `Product` con optimización para memoria con dos columnas: `Tags` y `Data`.

```sql
CREATE SCHEMA xtp;
GO
CREATE TABLE xtp.Product(
    ProductID int PRIMARY KEY NONCLUSTERED, --standard column
    Name nvarchar(400) NOT NULL, --standard column
    Price float, --standard column

    Tags nvarchar(400),--json stored in string column
    Data nvarchar(4000) --json stored in string column

) WITH (MEMORY_OPTIMIZED=ON);
```

## <a name="optimize-json-processing-with-additional-in-memory-features"></a>Optimización de procesamiento JSON con características en memoria adicionales
Las características disponibles en SQL Server y Azure SQL Database permiten integrar completamente la funcionalidad JSON con las tecnologías existentes de OLTP en memoria. Por ejemplo, puede realizar las siguientes tareas:
 - [Valide la estructura de los documentos JSON](#validate) almacenados en tablas optimizadas para memoria mediante las restricciones CHECK compiladas de forma nativa.
 - [Exponga y tipe fuertemente los valores](#computedcol) almacenados en documentos JSON mediante el uso de columnas calculadas.
 - [Indexe los valores](#index) de los documentos JSON con índices con optimización para memoria.
 - [Compile de forma nativa las consultas SQL](#compile) que usan valores de documentos JSON o que dan formato a los resultados como texto JSON.

## <a name="validate"></a> Validación de columnas JSON
SQL Server y Azure SQL Database permiten agregar restricciones CHECK compiladas de forma nativa que validan el contenido de los documentos JSON almacenados en una columna de cadena. Con las restricciones CHECK de JSON compiladas de forma nativa, puede asegurarse de que el texto JSON almacenado en las tablas con optimización para memoria tiene el formato correcto.

En el ejemplo siguiente, se crea una tabla `Product` con una columna JSON `Tags`. La columna `Tags` tiene una restricción CHECK que usa la función `ISJSON` para validar el texto JSON en la columna.

```sql
DROP TABLE IF EXISTS xtp.Product;
GO
CREATE TABLE xtp.Product(
    ProductID int PRIMARY KEY NONCLUSTERED,
    Name nvarchar(400) NOT NULL,
    Price float,

    Tags nvarchar(400)
            CONSTRAINT [Tags should be formatted as JSON]
                CHECK (ISJSON(Tags)=1),
    Data nvarchar(4000)

) WITH (MEMORY_OPTIMIZED=ON);
```

También puede agregar la restricción CHECK compilada de forma nativa a una tabla existente que contiene columnas JSON.

```sql
ALTER TABLE xtp.Product
    ADD CONSTRAINT [Data should be JSON]
        CHECK (ISJSON(Data)=1)
```

## <a name="computedcol"></a> Exposición de valores JSON mediante columnas calculadas
Las columnas calculadas permiten exponer valores del texto JSON y obtener acceso a esos valores sin capturar el valor del texto JSON y sin analizar nuevamente la estructura JSON. Los valores expuestos de esta manera están fuertemente tipados y persisten físicamente en las columnas calculadas. Acceder a los valores JSON mediante columnas calculadas persistentes es más rápido que hacerlo directamente a los valores del documento JSON.

En el ejemplo siguiente se muestra cómo exponer los dos valores siguientes de la columna `Data` JSON:
-   El país donde se fabricó un producto.
-   El costo de fabricación del producto.

En este ejemplo, las columnas calculadas `MadeIn` y `Cost` se actualizan cada vez que cambia el documento JSON almacenado en la columna `Data`.

```sql
DROP TABLE IF EXISTS xtp.Product;
GO
CREATE TABLE xtp.Product(
    ProductID int PRIMARY KEY NONCLUSTERED,
    Name nvarchar(400) NOT NULL,
    Price float,

    Data nvarchar(4000),

    MadeIn AS CAST(JSON_VALUE(Data, '$.MadeIn') as NVARCHAR(50)) PERSISTED,
    Cost   AS CAST(JSON_VALUE(Data, '$.ManufacturingCost') as float)

) WITH (MEMORY_OPTIMIZED=ON);
```

## <a name="index"></a> Indexación de valores en las columnas JSON
SQL Server y Azure SQL Database permiten indexar valores en columnas JSON mediante índices con optimización para memoria. Los valores JSON que se indexan se deben exponer y tipar fuertemente mediante el uso de columnas calculadas, tal como se describe en el ejemplo anterior.

Los valores de las columnas JSON se pueden indexar con los índices NONCLUSTERED y HASH estándar.
-   Los índices NONCLUSTERED optimizan las consultas que seleccionan rangos de filas por algún valor JSON u ordenan los resultados por valores JSON.
-   Los índices HASH optimizan las consultas que seleccionan una sola fila o algunas filas mediante la especificación de un valor exacto que se debe buscar.

En el ejemplo siguiente se crea una tabla que expone valores JSON mediante el uso de dos columnas calculadas. En el ejemplo, se crea un índice NONCLUSTERED en uno de los valores JSON y un índice HASH en el otro.

```sql
DROP TABLE IF EXISTS xtp.Product;
GO
CREATE TABLE xtp.Product(
    ProductID int PRIMARY KEY NONCLUSTERED,
    Name nvarchar(400) NOT NULL,
    Price float,

    Data nvarchar(4000),

    MadeIn AS CAST(JSON_VALUE(Data, '$.MadeIn') as NVARCHAR(50)) PERSISTED,
    Cost   AS CAST(JSON_VALUE(Data, '$.ManufacturingCost') as float) PERSISTED,

    INDEX [idx_Product_MadeIn] NONCLUSTERED (MadeIn)

) WITH (MEMORY_OPTIMIZED=ON)

ALTER TABLE Product
    ADD INDEX [idx_Product_Cost] NONCLUSTERED HASH(Cost)
        WITH (BUCKET_COUNT=20000)
```

## <a name="compile"></a> Compilación nativa de consultas JSON
Si los procedimientos, las funciones y los desencadenadores contienen consultas que usan las funciones JSON integradas, la compilación nativa aumenta el rendimiento de estas consultas y disminuye los ciclos de CPU que se requieren para ejecutarlos.

En el ejemplo siguiente, se muestra un procedimiento compilado de forma nativa que usa varias funciones JSON: **JSON_VALUE**, **OPENJSON** y **JSON_MODIFY**.

```sql
CREATE PROCEDURE xtp.ProductList(@ProductIds nvarchar(100))
WITH SCHEMABINDING, NATIVE_COMPILATION
AS BEGIN
    ATOMIC WITH (transaction isolation level = snapshot,  language = N'English')

    SELECT ProductID,Name,Price,Data,Tags, JSON_VALUE(data,'$.MadeIn') AS MadeIn
    FROM xtp.Product
        JOIN OPENJSON(@ProductIds)
            ON ProductID = value

END;

CREATE PROCEDURE xtp.UpdateProductData(@ProductId int, @Property nvarchar(100), @Value nvarchar(100))
WITH SCHEMABINDING, NATIVE_COMPILATION
AS BEGIN
    ATOMIC WITH (transaction isolation level = snapshot,  language = N'English')

    UPDATE xtp.Product
    SET Data = JSON_MODIFY(Data, @Property, @Value)
    WHERE ProductID = @ProductId;

END
```

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>Más información sobre la compatibilidad integrada de JSON en SQL Server  
Para obtener una gran cantidad de soluciones específicas, casos de uso y recomendaciones, consulte las [entradas de blog sobre la compatibilidad integrada de JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) en SQL Server y en Azure SQL Database ofrecidas por el director de programas de Microsoft Jovan Popovic.

