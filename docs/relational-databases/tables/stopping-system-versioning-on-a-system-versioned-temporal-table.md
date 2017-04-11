---
title: "Detenci&#243;n del control de versiones en una tabla temporal con control de versiones | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "10/11/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-tables"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dddd707e-bfb1-44ff-937b-a84c5e5d1a94
caps.latest.revision: 10
author: "CarlRabeler"
ms.author: "carlrab"
manager: "jhubbard"
caps.handback.revision: 10
---
# Detenci&#243;n del control de versiones en una tabla temporal con control de versiones
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Es posible que quiera detener el control de versiones en una tabla temporal de forma temporal o permanente.   
Puede hacerlo estableciendo la cláusula **SYSTEM_VERSIONING** en **OFF**.  
  
## Valor SYSTEM_VERSIONING = OFF  
 Detenga el control de versiones del sistema si quiere realizar operaciones de mantenimiento concretas en una tabla temporal o si ya no necesita una tabla con control de versiones. Como resultado de esta operación obtendrá dos tablas independientes:  
  
-   Tabla actual con definición del período  
  
-   Tabla de historial como una tabla normal  
  
### Notas importantes  
  
-   No se produce ninguna pérdida de datos cuando se establece **SYSTEM_VERSIONING = OFF** o se quita el período **SYSTEM_TIME**.  
  
-   Si establece **SYSTEM_VERSIONING = OFF** y no quita el período **SYSTEM_TIME**, el sistema seguirá actualizando las columnas de período en cada operación de inserción y actualización. Las eliminaciones en la tabla actual serán permanentes.  
  
-   Quite el período **SYSTEM_TIME** para quitar las columnas de período completamente.  
  
-   Al establecer **SYSTEM_VERSIONING = OFF**, todos los usuarios que tengan permisos suficientes podrán modificar el esquema y el contenido de la tabla de historial o incluso eliminarla permanentemente.  
  
### Quitar permanentemente SYSTEM_VERSIONING  
 En este ejemplo se quita permanentemente SYSTEM_VERSIONING y se quitan las columnas de período completamente. La eliminación de las columnas de período es opcional.  
  
```  
ALTER TABLE dbo.Department SET (SYSTEM_VERSIONING = OFF);   
/*Optionally, DROP PERIOD if you want to revert temporal table to a non-temporal*/   
ALTER TABLE dbo.Department   
DROP PERIOD FOR SYSTEM_TIME;  
  
```  
  
### Quitar temporalmente SYSTEM_VERSIONING  
 Esta es la lista de operaciones que exigen que el control de versiones del sistema esté establecido en **OFF**:  
  
-   Eliminación de datos innecesarios del historial (**DELETE** or **TRUNCATE**)  
  
-   Eliminación de datos de la tabla actual sin control de versiones (**DELETE**, **TRUNCATE**)  
  
-   Partición **SWITCH OUT** de la tabla actual  
  
-   Partición **SWITCH IN** en la tabla de historial  
  
 En este ejemplo se detiene temporalmente SYSTEM_VERSIONING para que se puedan realizar operaciones de mantenimiento concretas. Si se detiene temporalmente el control de versiones como un requisito previo para el mantenimiento de una tabla, se recomienda encarecidamente hacerlo en una transacción para mantener la coherencia de los datos.  
  
```  
BEGIN TRAN   
ALTER TABLE dbo.Department SET (SYSTEM_VERSIONING = OFF);   
TRUNCATE TABLE [History].[DepartmentHistory]   
WITH (PARTITIONS (1,2))   
ALTER TABLE dbo.Department SET    
(   
SYSTEM_VERSIONING = ON (HISTORY_TABLE = History.DepartmentHistory)   
);   
COMMIT ;  
  
```  
  
## ¿Le ayudó este artículo? Le escuchamos  
 ¿Qué información está buscando? ¿La encontró? Escuchamos sus comentarios para mejorar el contenido. Envíe sus comentarios a [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Stopping%20System-Versioning%20on%20a%20System-Version%20Temporal%20Table%20page)  
  
## Vea también  
 [Tablas temporales](../../relational-databases/tables/temporal-tables.md)   
 [Introducción a las tablas temporales con versión del sistema](../../relational-databases/tables/getting-started-with-system-versioned-temporal-tables.md)   
 [Administración de la retención de datos históricos en las tablas temporales con versiones del sistema](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [Tablas temporales con control de versiones del sistema con tablas con optimización para memoria](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [Creación de una tabla temporal con control de versiones del sistema](../../relational-databases/tables/creating-a-system-versioned-temporal-table.md)   
 [Modificación de los datos de una tabla temporal con control de versiones del sistema](../../relational-databases/tables/modifying-data-in-a-system-versioned-temporal-table.md)   
 [Consulta de los datos de una tabla temporal con control de versiones del sistema](../../relational-databases/tables/querying-data-in-a-system-versioned-temporal-table.md)   
 [Cambiar el esquema de una tabla temporal con control de versiones del sistema](../../relational-databases/tables/changing-the-schema-of-a-system-versioned-temporal-table.md)  
  
  