---
title: Sys.dm_db_incremental_stats_properties (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 11/16/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server 2014
f1_keywords:
- sys.dm_db_incremental_stats_properties
- sys.dm_db_incremental_stats_properties_TSQL
- dm_db_incremental_stats_properties
- dm_db_incremental_stats_properties_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_db_incremental_stats_properties
ms.assetid: aa0db893-34d1-419c-b008-224852e71307
caps.latest.revision: "7"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ce7ab395a01f3b1ab6d35edb3c260f1f4338044e
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmdbincrementalstatsproperties-transact-sql"></a>sys.dm_db_incremental_stats_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Devuelve propiedades de estadísticas incrementales para el objeto de base de datos especificado (tabla) en la base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. El uso de `sys.dm_db_incremental_stats_properties` (que contiene un número de partición) es similar a `sys.dm_db_stats_properties` , que se usa para estadísticas no incrementales. 
  
  Esta función se introdujo en [!INCLUDE[ssSQL14_md](../../includes/sssql14-md.md)] Service Pack 2 y [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] Service Pack 1.
  
 
## <a name="syntax"></a>Sintaxis  
  
```  
sys.dm_db_incremental_stats_properties (object_id, stats_id)  
```  
  
## <a name="arguments"></a>Argumentos  
 *object_id*  
 Es el identificador del objeto en la base de datos actual para el que se solicitaron las propiedades de una de sus estadísticas incrementales. *object_id* es **int**.  
  
 *stats_id*  
 Es el identificador de estadísticas para el *object_id*especificado. El identificador de estadísticas se puede obtener desde la vista de administración dinámica [sys.stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md) . *stats_id* es **int**.  
  
## <a name="table-returned"></a>Tabla devuelta  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|object_id|**int**|Identificador del objeto (tabla) para el que se devuelven las propiedades del objeto de estadísticas.|  
|stats_id|**int**|Identificador del objeto de estadísticas. Es único en la tabla. Para obtener más información, vea [sysno incluye la vista.stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)no incluye la vista.|
|partition_number|**int**|El número de la partición que contiene la parte de la tabla.|  
|last_updated|**datetime2**|Fecha y hora de la última actualización del objeto de estadísticas.|  
|rows|**bigint**|El número total de filas que tenía la tabla la última vez que se actualizaron las estadísticas. Si las estadísticas se filtran o corresponden a un índice filtrado, el número de filas puede ser inferior al número de filas de la tabla.|  
|rows_sampled|**bigint**|Número total de filas muestreadas para cálculos de estadísticas.|  
|pasos|**int**|Número de pasos del histograma. Para obtener más información, vea [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)no incluye la vista.|  
|unfiltered_rows|**bigint**|Número total de filas de la tabla antes de aplicar la expresión de filtro (para estadísticas filtradas). Si las estadísticas no están filtradas, unfiltered_rows es igual al valor devuelto en la columna rows.|  
|modification_counter|**bigint**|Número total de modificaciones para la columna de estadísticas iniciales (la columna en la que se ha generado el histograma) desde la última vez que se actualizaron las estadísticas.<br /><br /> Esta columna no contiene información sobre tablas optimizadas para memoria.|  
  
## <a name="remarks"></a>Comentarios  
 `sys.dm_db_incremental_stats_properties` devuelve un conjunto de filas vacío si se da alguna de las condiciones siguientes:  
  
-   `object_id` o `stats_id` es NULL.   
-   El objeto especificado no se encuentra o no corresponde a una tabla con estadísticas incrementales.  
-   El identificador de estadísticas especificado no se corresponde con las estadísticas existentes para el identificador de objeto especificado.  
-   El usuario actual no tiene permisos para ver el objeto de estadísticas.

 
 Este comportamiento permite el uso seguro de `sys.dm_db_incremental_stats_properties` cuando se aplica de manera cruzada a filas en vistas como `sys.objects` y `sys.stats`. Este método puede devolver propiedades de las estadísticas que corresponden a cada partición. Para ver las propiedades de las estadísticas combinadas en todas las particiones, use sys.dm_db_stats_properties en su lugar. 
  
## <a name="permissions"></a>Permissions  
 Necesita que el usuario tenga permisos de selección en columnas de estadísticas o posea la tabla, o que el usuario sea miembro del rol fijo de servidor `sysadmin`, del rol fijo de base de datos `db_owner` o del rol fijo de base de datos `db_ddladmin`.  
  
## <a name="examples"></a>Ejemplos  

### <a name="a-simple-example"></a>A. Ejemplo sencillo
El ejemplo siguiente devuelve las estadísticas de la tabla `PartitionTable` que se describe en el tema [Crear tablas e índices con particiones](../../relational-databases/partitions/create-partitioned-tables-and-indexes.md).

```
SELECT * FROM sys.dm_db_incremental_stats_properties (object_id('PartitionTable'), 1);
``` 

Para sugerencias adicionales de uso, consulte  [sys.dm_db_stats_properties](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-properties-transact-sql.md).
  
  
## <a name="see-also"></a>Vea también  
 [Sys.dm_db_stats_properties](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-properties-transact-sql.md)   
 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [sys.stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)   
 [Funciones y vistas de administración dinámica relacionada con objetos &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/object-related-dynamic-management-views-and-functions-transact-sql.md)   
 [Funciones y vistas de administración dinámica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)
