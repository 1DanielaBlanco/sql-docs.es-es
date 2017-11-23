---
title: Sys.dm_exec_procedure_stats (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_procedure_stats_TSQL
- dm_exec_procedure_stats_TSQL
- dm_exec_procedure_stats
- sys.dm_exec_procedure_stats
dev_langs: TSQL
helpviewer_keywords: sys.dm_exec_procedure_stats dynamic management view
ms.assetid: ab8ddde8-1cea-4b41-a7e4-697e6ddd785a
caps.latest.revision: "24"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: f935b0e9a4c150830a03ecb2ea1f67a4cd270d3f
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmexecprocedurestats-transact-sql"></a>sys.dm_exec_procedure_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Devuelve estadísticas de rendimiento de agregado para los procedimientos almacenados en memoria caché. La vista devuelve una fila por cada procedimiento almacenado en memoria caché y la vigencia de la fila corresponde al tiempo que el procedimiento almacenado permanece en memoria caché. Cuando se quita un procedimiento almacenado de la memoria caché, la fila correspondiente se elimina de esta vista. En ese momento, se provoca un evento de seguimiento de SQL de estadísticas de rendimiento similar a **sys.dm_exec_query_stats**.  
  
 En [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], las vistas de administración dinámica no pueden exponer información que impactaría a la contención de la base de datos ni acerca de otras bases de datos a las que el usuario tenga acceso. Para evitar exponer esta información, cada fila que contiene datos que no pertenecen al inquilino conectado se filtra.  
  
> **Nota:** una consulta inicial de **sys.dm_exec_procedure_stats** podría producir resultados imprecisos si hay una carga de trabajo ejecutándose actualmente en el servidor. Pueden determinarse resultados más precisos volviendo a ejecutar la consulta.  
  
> **Tenga en cuenta para el almacenamiento de datos SQL Azure.** Para llamar a esta desde [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], use el nombre **sys.dm_pdw_nodes_exec_procedure_stats**.  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|Identificador de base de datos en el que el procedimiento almacenado reside.|  
|**object_id**|**int**|Número de identificación de objeto del procedimiento almacenado.|  
|**tipo**|**Char(2)**|Tipo del objeto:<br /><br /> P = procedimiento almacenado de SQL<br /><br /> PC = Procedimiento almacenado de ensamblado (CLR)<br /><br /> X = Procedimiento almacenado extendido|  
|**type_desc**|**nvarchar (60)**|Descripción del tipo de objeto:<br /><br /> SQL_STORED_PROCEDURE<br /><br /> CLR_STORED_PROCEDURE<br /><br /> EXTENDED_STORED_PROCEDURE|  
|**sql_handle**|**varbinary(64)**|Esto puede usarse para poner en correlación con las consultas en **sys.dm_exec_query_stats** que se ejecutaron desde dentro de este procedimiento almacenado.|  
|**plan_handle**|**varbinary(64)**|Identificador del plan en memoria. Este identificador es transitorio y permanece constante solo mientras el plan permanece en la memoria caché. Este valor se puede usar con el **sys.dm_exec_cached_plans** vista de administración dinámica.<br /><br /> Será siempre 0x000 cuando un procedimiento almacenado nativo consulte una tabla optimizada para memoria.|  
|**cached_time**|**datetime**|Momento en el que el procedimiento almacenado se agregó a la caché.|  
|**last_execution_time**|**datetime**|Hora en que se ejecutó el procedimiento almacenado por última vez.|  
|**entre execution_count**|**bigint**|Número de veces que se ha ejecutado el procedimiento almacenado desde que se compiló por última vez.|  
|**total_worker_time**|**bigint**|Tiempo total de CPU, en microsegundos, consumido por las ejecuciones de este procedimiento almacenado desde que se compiló.<br /><br /> Para los procedimientos almacenados compilados de forma nativa, **total_worker_time** puede no ser exacto si varias ejecuciones tardan menos de 1 milisegundo.|  
|**last_worker_time**|**bigint**|Tiempo de CPU, en microsegundos, consumido la última vez que se ejecutó el procedimiento almacenado. <sup>1</sup>|  
|**min_worker_time**|**bigint**|Tiempo mínimo de CPU, en microsegundos, que ha utilizado este procedimiento almacenado durante una ejecución. <sup>1</sup>|  
|**max_worker_time**|**bigint**|Tiempo máximo de CPU, en microsegundos, que ha utilizado este procedimiento almacenado durante una ejecución. <sup>1</sup>|  
|**número**|**bigint**|Número total de lecturas físicas realizadas por las ejecuciones de este procedimiento almacenado desde que se compiló.<br /><br /> Será siempre 0 al consultar una tabla optimizada para memoria.|  
|**last_physical_reads**|**bigint**|Número de lecturas físicas realizadas la última vez que se ejecutó el procedimiento almacenado.<br /><br /> Será siempre 0 al consultar una tabla optimizada para memoria.|  
|**min_physical_reads**|**bigint**|Número mínimo de lecturas físicas que ha realizado este procedimiento almacenado durante una ejecución.<br /><br /> Será siempre 0 al consultar una tabla optimizada para memoria.|  
|**max_physical_reads**|**bigint**|Número máximo de lecturas físicas que ha realizado este procedimiento almacenado durante una ejecución.<br /><br /> Será siempre 0 al consultar una tabla optimizada para memoria.|  
|**total_logical_writes**|**bigint**|Número total de lecturas lógicas realizadas por las ejecuciones de este procedimiento almacenado desde que se compiló.<br /><br /> Será siempre 0 al consultar una tabla optimizada para memoria.|  
|**last_logical_writes**|**bigint**|Número de páginas del grupo de búferes desfasadas la última vez que se ejecutó el plan. Si una página ya está desfasada (modificada) no se cuenta ninguna escritura.<br /><br /> Será siempre 0 al consultar una tabla optimizada para memoria.|  
|**min_logical_writes**|**bigint**|Número mínimo de escrituras lógicas que este procedimiento almacenado se ha realizado durante una ejecución.<br /><br /> Será siempre 0 al consultar una tabla optimizada para memoria.|  
|**max_logical_writes**|**bigint**|Número máximo de escrituras lógicas que este procedimiento almacenado se ha realizado durante una ejecución.<br /><br /> Será siempre 0 al consultar una tabla optimizada para memoria.|  
|**total_logical_reads**|**bigint**|Número total de lecturas lógicas realizadas por las ejecuciones de este procedimiento almacenado desde que se compiló.<br /><br /> Será siempre 0 al consultar una tabla optimizada para memoria.|  
|**last_logical_reads**|**bigint**|Número de lecturas lógicas realizadas la última vez que se ejecutó el procedimiento almacenado.<br /><br /> Será siempre 0 al consultar una tabla optimizada para memoria.|  
|**min_logical_reads**|**bigint**|Número mínimo de lecturas lógicas que ha realizado este procedimiento almacenado durante una ejecución.<br /><br /> Será siempre 0 al consultar una tabla optimizada para memoria.|  
|**max_logical_reads**|**bigint**|Número máximo de lecturas lógicas que ha realizado este procedimiento almacenado durante una ejecución.<br /><br /> Será siempre 0 al consultar una tabla optimizada para memoria.|  
|**total_elapsed_time**|**bigint**|Tiempo total transcurrido, en microsegundos, hasta la finalización de las ejecuciones de este procedimiento almacenado.|  
|**last_elapsed_time**|**bigint**|Tiempo transcurrido, en microsegundos, hasta la finalización de la ejecución más reciente de este procedimiento almacenado.|  
|**min_elapsed_time**|**bigint**|Tiempo mínimo transcurrido, en microsegundos, hasta que se completa cualquier ejecución de este procedimiento almacenado.|  
|**max_elapsed_time**|**bigint**|Tiempo máximo transcurrido, en microsegundos, hasta que se completa cualquier ejecución de este procedimiento almacenado.|  
|**pdw_node_id**|**int**|**Se aplica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> El identificador para el nodo que se encuentra en esta distribución.|  
  
 <sup>1</sup> para los procedimientos almacenados compilados de forma nativa cuando se habilita la recopilación de estadísticas, el tiempo de trabajo se recopila en milisegundos. Si la consulta se ejecuta en menos de un milisegundo, el valor será 0.  
  
## <a name="permissions"></a>Permissions  
En [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], requiere `VIEW SERVER STATE` permiso.   
En [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] niveles de Premium, requieren la `VIEW DATABASE STATE` permiso en la base de datos. En [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] niveles estándar y básico, requiere la **administrador del servidor** o un **Administrador de Azure Active Directory** cuenta. 
  
## <a name="remarks"></a>Comentarios  
 Las estadísticas en la vista se actualizan cuando una ejecución del procedimiento almacenado se completa.  
  
## <a name="examples"></a>Ejemplos  
 En el siguiente ejemplo se devuelve información acerca de los diez procedimientos almacenados identificados con el mayor promedio de tiempo transcurrido.  
  
```  
SELECT TOP 10 d.object_id, d.database_id, OBJECT_NAME(object_id, database_id) 'proc name',   
    d.cached_time, d.last_execution_time, d.total_elapsed_time,  
    d.total_elapsed_time/d.execution_count AS [avg_elapsed_time],  
    d.last_elapsed_time, d.execution_count  
FROM sys.dm_exec_procedure_stats AS d  
ORDER BY [total_worker_time] DESC;  
```  
  
## <a name="see-also"></a>Vea también  
 [Funciones y vistas de administración dinámica &#40; relacionada con la ejecución Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [Sys.dm_exec_sql_text &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)   
 [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)   
 
 [Sys.dm_exec_trigger_stats &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)  
  
  


