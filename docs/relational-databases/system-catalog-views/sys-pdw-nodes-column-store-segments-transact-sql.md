---
title: Sys.pdw_nodes_column_store_segments (Transact-SQL) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/28/2018
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: design
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: e2fdf8e9-1b74-4682-b2d4-c62aca053d7f
caps.latest.revision: 9
author: hirokib
ms.author: elbutter
manager: jrj
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 92eee101d27c4483207ba1be9933b750aabdea3d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="syspdwnodescolumnstoresegments-transact-sql"></a>Sys.pdw_nodes_column_store_segments (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

Contiene una fila para cada columna de un índice de almacén de columnas.  

| Nombre de columna                 | Tipo de datos  | Description                                                  |
| --------------------------- | ---------- | ------------------------------------------------------------ |
| **partition_id**            | **bigint** | Indica el identificador de partición. Es único en una base de datos.     |
| **hobt_id**                 | **bigint** | Identificador del montón o el índice de árbol b (hobt) para la tabla que contiene este índice de almacén de columnas. |
| **column_id**               | **int**    | Identificador de la columna de almacén de columnas.                                |
| **segment_id**              | **int**    | Identificador del segmento de columna. Por compatibilidad con versiones anteriores, el nombre de columna continúa llamarlo segment_id aunque éste es el identificador del grupo de filas. Se puede identificar un segmento mediante < hobt_id, partition_id, column_id >, < segment_id >. |
| **version**                 | **int**    | Versión del formato de segmento de columna.                        |
| **encoding_type**           | **int**    | Tipo de codificación utilizado para ese segmento:<br /><br /> 1 = VALUE_BASED - no-cadena o binarios con ningún diccionario (similar a 4 con algunas variaciones internos)<br /><br /> 2 = VALUE_HASH_BASED - columna cadena o binarios con valores comunes de diccionario<br /><br /> 3 = STRING_HASH_BASED - columnas de cadena o binarios con valores comunes de diccionario<br /><br /> 4 = STORE_BY_VALUE_BASED - no-cadena o binarios con ningún diccionario<br /><br /> 5 = STRING_STORE_BY_VALUE_BASED - cadena o binarios con ningún diccionario<br /><br /> Todas las codificaciones de sacar partido de codificación de empaquetado de bits y longitud de ejecución siempre que sea posible. |
| **row_count**               | **int**    | Número de filas del grupo de filas.                             |
| **has_nulls**               | **int**    | 1 si el segmento de la columna tiene valores NULL.                     |
| **base_id**                 | **bigint** | Identificador del valor base si se utiliza el tipo de codificación 1.  Si el tipo de codificación 1 no se está usando, base_id se establece en 1. |
| **magnitud**               | **float**  | Magnitud si se utiliza el tipo de codificación 1.  Si el tipo de codificación 1 no se está usando, magnitud se establece en 1. |
| **primary__dictionary_id**  | **int**    | Identificador del diccionario principal. Un valor distinto de cero apunta al diccionario local para esta columna en el segmento actual (es decir, el grupo de filas). Un valor de -1 indica que no hay ningún diccionario local para este segmento. |
| **secondary_dictionary_id** | **int**    | Identificador del diccionario secundario. Un valor distinto de cero apunta al diccionario local para esta columna en el segmento actual (es decir, el grupo de filas). Un valor de -1 indica que no hay ningún diccionario local para este segmento. |
| **min_data_id**             | **bigint** | Identificador de la mínima cantidad de datos en el segmento de columna.                       |
| **max_data_id**             | **bigint** | Identificador de datos máximo en el segmento de columna.                       |
| **null_value**              | **bigint** | Valor usado para representar valores NULL.                               |
| **on_disk_size**            | **bigint** | Tamaño del segmento en bytes.                                    |
| **pdw_node_id**             | **int**    | Identificador único de un [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] nodo. |

## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Ejemplos: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] y [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  

Unir sys.pdw_nodes_column_store_segments con otras tablas del sistema para determinar el número de segmentos de almacén de columnas por tabla lógica. 

```sql
SELECT  sm.name           as schema_nm
,       tb.name           as table_nm
,       nc.name           as col_nm
,       nc.column_id
,       COUNT(*)          as segment_count
FROM    sys.[schemas] sm
JOIN    sys.[tables] tb                   ON  sm.[schema_id]          = tb.[schema_id]
JOIN    sys.[pdw_table_mappings] mp       ON  tb.[object_id]          = mp.[object_id]
JOIN    sys.[pdw_nodes_tables] nt         ON  nt.[name]               = mp.[physical_name]
JOIN    sys.[pdw_nodes_partitions] np     ON  np.[object_id]          = nt.[object_id]
                                          AND np.[pdw_node_id]        = nt.[pdw_node_id]
                                          AND np.[distribution_id]    = nt.[distribution_id]
JOIN    sys.[pdw_nodes_columns] nc        ON  np.[object_id]          = nc.[object_id]
                                          AND np.[pdw_node_id]        = nc.[pdw_node_id]
                                          AND np.[distribution_id]    = nc.[distribution_id]
JOIN    sys.[pdw_nodes_column_store_segments] rg  ON  rg.[partition_id]         = np.[partition_id]
                                                      AND rg.[pdw_node_id]      = np.[pdw_node_id]
                                                      AND rg.[distribution_id]  = np.[distribution_id]
                                                      AND rg.[column_id]        = nc.[column_id]
GROUP BY    sm.name
,           tb.name
,           nc.name
,           nc.column_id  
ORDER BY    table_nm
,           nc.column_id
,           sm.name
```

## <a name="permissions"></a>Permissions  
 Requiere el permiso **VIEW SERVER STATE**.  

## <a name="see-also"></a>Vea también  
 [Almacenamiento de datos SQL y vistas de catálogo del almacén de datos en paralelo](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [Crear índice de almacén &#40;Transact-SQL&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md)   
 [sys.pdw_nodes_column_store_row_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-row-groups-transact-sql.md)   
 [sys.pdw_nodes_column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-dictionaries-transact-sql.md)  

  

