---
title: Sys.query_store_query (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/29/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- QUERY_STORE_QUERY
- SYS.QUERY_STORE_QUERY_TSQL
- SYS.QUERY_STORE_QUERY
- QUERY_STORE_QUERY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- query_store_query catalog view
- sys.query_store_query catalog view
ms.assetid: bdee149e-7556-4fc3-8242-925dd4b7b6ac
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ef06fab57c78c83e4c38993cf0acdaf60fcc0f39
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="sysquerystorequery-transact-sql"></a>Sys.query_store_query (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Contiene información acerca de la consulta y sus estadísticas de ejecución de asociado en tiempo agregado total.  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**query_id**|**bigint**|Clave principal.|  
|**query_text_id**|**bigint**|Clave externa. Se combina con [sys.query_store_query_text &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)|  
|**context_settings_id**|**bigint**|Clave externa. Se combina con [sys.query_context_settings &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md).|  
|**object_id**|**bigint**|Identificador del objeto de base de datos que forma parte de la consulta (procedimiento almacenado, desencadenador, UDF de CLR/UDAgg, etcetera.). 0 si la consulta no se ejecuta como parte de un objeto de base de datos (consulta ad hoc).|  
|**batch_sql_handle**|**varbinary(64)**|Id. del lote de instrucciones de la consulta forma parte de. Llenan solo si la consulta hace referencia a tablas temporales o variables de tabla.|  
|**query_hash**|**binary (8)**|Hash MD5 de la consulta individual, tomando como base el árbol lógico de consulta. Incluye sugerencias del optimizador.|  
|**is_internal_query**|**bit**|La consulta era generada internamente.|  
|**query_parameterization_type**|**tinyint**|Tipo de parametrización:<br /><br /> 0: ninguno<br /><br /> 1 – usuario<br /><br /> 2-simple<br /><br /> 3 – forzada|  
|**query_parameterization_type_desc**|**nvarchar (60)**|Texto descriptivo para el tipo de la parametrización.|  
|**initial_compile_start_time**|**datetimeoffset**|Tiempo de inicio de la compilación.|  
|**last_compile_start_time**|**datetimeoffset**|Tiempo de inicio de la compilación.|  
|**last_execution_time**|**datetimeoffset**|Último tiempo de ejecución se refiere a la última hora de finalización del plan de consulta.|  
|**last_compile_batch_sql_handle**|**varbinary(64)**|Identificador del último lote SQL en el que consulta usó la última vez. Se puede proporcionar como entrada para [sys.dm_exec_sql_text &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md) para obtener el texto del lote completo.|  
|**last_compile_batch_offset_start**|**bigint**|Información que pueda proporcionarse a sys.dm_exec_sql_text junto con last_compile_batch_sql_handle.|  
|**last_compile_batch_offset_end**|**bigint**|Información que pueda proporcionarse a sys.dm_exec_sql_text junto con last_compile_batch_sql_handle.|  
|**count_compiles**|**bigint**|Estadísticas de compilación.|  
|**avg_compile_duration**|**float**|Estadísticas de compilación en microsegundos.|  
|**last_compile_duration**|**bigint**|Estadísticas de compilación en microsegundos.|  
|**avg_bind_duration**|**float**|Estadísticas de enlace en microsegundos.|  
|**last_bind_duration**|**bigint**|Estadísticas de enlace.|  
|**avg_bind_cpu_time**|**float**|Estadísticas de enlace.|  
|**last_bind_cpu_time**|**bigint**|Estadísticas de enlace.|  
|**avg_optimize_duration**|**float**|Estadísticas de optimización en microsegundos.|  
|**last_optimize_duration**|**bigint**|Estadísticas de optimización.|  
|**avg_optimize_cpu_time**|**float**|Estadísticas de optimización en microsegundos.|  
|**last_optimize_cpu_time**|**bigint**|Estadísticas de optimización.|  
|**avg_compile_memory_kb**|**float**|Recopilar estadísticas de memoria.|  
|**last_compile_memory_kb**|**bigint**|Recopilar estadísticas de memoria.|  
|**max_compile_memory_kb**|**bigint**|Recopilar estadísticas de memoria.|  
|**is_clouddb_internal_query**|**bit**|Siempre es 0 en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] local.|  
  
## <a name="permissions"></a>Permissions  
 Requiere la **VIEW DATABASE STATE** permiso.  
  
## <a name="see-also"></a>Vea también  
 [Sys.database_query_store_options &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [Sys.query_context_settings &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [Sys.query_store_plan &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)   
 [Sys.query_store_query_text &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)  
 [Sys.query_store_runtime_stats &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md)   
 [Sys.query_store_runtime_stats_interval &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [Supervisar el rendimiento mediante el almacén de consultas](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Vistas de catálogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Query Store Stored Procedures &#40;Transact-SQL&#41; (Procedimientos almacenados del Almacén de consultas &#40;Transact-SQL&#41;)](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)   
 [sys.fn_stmt_sql_handle_from_sql_stmt &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-stmt-sql-handle-from-sql-stmt-transact-sql.md)  
  
  
