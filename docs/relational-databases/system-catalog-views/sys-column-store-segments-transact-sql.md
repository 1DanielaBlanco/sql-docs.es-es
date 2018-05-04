---
title: Sys.column_store_segments (Transact-SQL) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/15/2018
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- column_store_segments
- sys.column_store_segments_TSQL
- sys.column_store_segments
- column_store_segments_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_store_segments catalog view
ms.assetid: 1253448c-2ec9-4900-ae9f-461d6b51b2ea
caps.latest.revision: 20
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 1b4247266c2b6ff16529eb6468211d6b746b6a39
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="syscolumnstoresegments-transact-sql"></a>sys.column_store_segments (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

Devuelve una fila para cada segmento de columna en un índice de almacén de columnas. Hay un segmento de columna por columna por grupo de filas. Por ejemplo, una tabla con 10 grupos de filas y 34 columnas devuelve 340 filas. 
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**partition_id**|**bigint**|Indica el identificador de partición. Es único en una base de datos.|  
|**hobt_id**|**bigint**|Identificador del montón o el índice de árbol b (hobt) para la tabla que contiene este índice de almacén de columnas.|  
|**column_id**|**int**|Identificador de la columna de almacén de columnas.|  
|**segment_id**|**int**|Id. del grupo de filas. Por compatibilidad con versiones anteriores, el nombre de columna continúa llamarlo segment_id aunque éste es el identificador del grupo de filas. Se puede identificar un segmento utilizando \<hobt_id, partition_id, column_id >, < segment_id >.|  
|**version**|**int**|Versión del formato de segmento de columna.|  
|**encoding_type**|**int**|Tipo de codificación utilizado para ese segmento:<br /><br /> 1 = VALUE_BASED - no-cadena o binarios con ningún diccionario (muy similar a 4 con algunas variaciones internos)<br /><br /> 2 = VALUE_HASH_BASED - columna cadena o binarios con valores comunes de diccionario<br /><br /> 3 = STRING_HASH_BASED - columnas de cadena o binarios con valores comunes de diccionario<br /><br /> 4 = STORE_BY_VALUE_BASED - no-cadena o binarios con ningún diccionario<br /><br /> 5 = STRING_STORE_BY_VALUE_BASED - cadena o binarios con ningún diccionario<br /><br /> Todas las codificaciones de sacar partido de codificación de empaquetado de bits y longitud de ejecución siempre que sea posible.|  
|**row_count**|**int**|Número de filas del grupo de filas.|  
|**has_nulls**|**int**|1 si el segmento de la columna tiene valores NULL.|  
|**base_id**|**bigint**|Identificador del valor base si se utiliza la codificación de tipo 1.  Si no se utiliza la codificación de tipo 1, base_id se establece en -1.|  
|**magnitud**|**float**|Magnitud si se utiliza el tipo de codificación 1.  Si el tipo de codificación 1 no se está usando, magnitud se establece en -1.|  
|**primary_dictionary_id**|**int**|Un valor de 0 representa el diccionario global. Un valor de -1 indica que no hay ningún diccionario global creado para esta columna.|  
|**secondary_dictionary_id**|**int**|Un valor distinto de cero apunta al diccionario local para esta columna en el segmento actual (es decir, el grupo de filas). Un valor de -1 indica que no hay ningún diccionario local para este segmento.|  
|**min_data_id**|**bigint**|Identificador de datos mínimo en el segmento de columna.|  
|**max_data_id**|**bigint**|Identificador de datos máximo en el segmento de columna.|  
|**null_value**|**bigint**|Valor usado para representar valores NULL.|  
|**on_disk_size**|**bigint**|Tamaño del segmento en bytes.|  
  
## <a name="remarks"></a>Comentarios  
 La consulta siguiente devuelve información acerca de los segmentos de un índice de almacén de columnas.  
  
```sql  
SELECT i.name, p.object_id, p.index_id, i.type_desc,   
    COUNT(*) AS number_of_segments  
FROM sys.column_store_segments AS s   
INNER JOIN sys.partitions AS p   
    ON s.hobt_id = p.hobt_id   
INNER JOIN sys.indexes AS i   
    ON p.object_id = i.object_id  
WHERE i.type = 5 OR i.type = 6  
GROUP BY i.name, p.object_id, p.index_id, i.type_desc ;  
GO  
```  
  
## <a name="permissions"></a>Permissions  
 Todas las columnas necesitan al menos **VIEW DEFINITION** permiso en la tabla. Las columnas siguientes devuelven null a menos que el usuario también tenga **seleccione** permiso: has_nulls, base_id, magnitud, min_data_id, max_data_id y null_value.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Para obtener más información, consulte [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vea también  
 [Object Catalog Views &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  (Vistas de catálogo de objetos [Transact-SQL])  
 [Vistas de catálogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Consultar el catálogo de sistema SQL Server preguntas más frecuentes](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [Sys.ALL_COLUMNS &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.computed_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)   
 [Guía de índices de almacén de columnas](~/relational-databases/indexes/columnstore-indexes-overview.md)    
 [sys.column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md)  
  
  

