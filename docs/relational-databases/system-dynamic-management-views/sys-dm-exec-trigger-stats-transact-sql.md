---
title: sys.dm_exec_trigger_stats (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 01/10/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_exec_trigger_stats
- dm_exec_trigger_stats_TSQL
- sys.dm_exec_trigger_stats_TSQL
- sys.dm_exec_trigger_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_trigger_stats dynamic management function
ms.assetid: 863498b4-849c-434d-b748-837411458738
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 63430240cfd518ce38567d10fbebbf258a37d872
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmexectriggerstats-transact-sql"></a>sys.dm_exec_trigger_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Devuelve estadísticas de rendimiento de agregado para los desencadenadores en memoria caché. La vista contiene una fila por cada desencadenador y la duración de la fila corresponde al tiempo que el desencadenador permanece en memoria caché. Cuando se quita un desencadenador de la memoria caché, la fila correspondiente se elimina de esta vista. En ese momento, se provoca un evento de seguimiento de SQL de estadísticas de rendimiento similar a **sys.dm_exec_query_stats**.  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|Identificador de base de datos en que reside el desencadenador.|  
|**object_id**|**int**|Número de identificación del objeto del desencadenador.|  
|**Tipo**|**char(2)**|Tipo del objeto:<br /><br /> TA = Desencadenador de ensamblado (CLR)<br /><br /> TR = Desencadenador SQL|  
|**Type_desc**|**nvarchar(60)**|Descripción del tipo de objeto:<br /><br /> CLR_TRIGGER<br /><br /> SQL_TRIGGER|  
|**sql_handle**|**varbinary(64)**|Esto puede usarse para poner en correlación con las consultas en **sys.dm_exec_query_stats** que se ejecutaron desde dentro de este desencadenador.|  
|**plan_handle**|**varbinary(64)**|Identificador del plan en memoria. Este identificador es transitorio y permanece constante solo mientras el plan permanece en la memoria caché. Este valor se puede usar con el **sys.dm_exec_cached_plans** vista de administración dinámica.|  
|**cached_time**|**datetime**|Momento en que el desencadenador se agregó a la caché.|  
|**last_execution_time**|**datetime**|Última vez que se ejecutó el desencadenador vez.|  
|**execution_count**|**bigint**|El número de veces que el desencadenador se ha ejecutado desde que se compiló por última vez.|  
|**total_worker_time**|**bigint**|La cantidad total de tiempo de CPU, en microsegundos, consumido por las ejecuciones de este desencadenador desde que se compiló.|  
|**last_worker_time**|**bigint**|Tiempo de CPU, en microsegundos, consumido la última vez que se ejecutó el desencadenador.|  
|**min_worker_time**|**bigint**|Tiempo de CPU máximo, en microsegundos, que ha utilizado este desencadenador durante una ejecución.|  
|**max_worker_time**|**bigint**|Tiempo de CPU máximo, en microsegundos, que ha utilizado este desencadenador durante una ejecución.|  
|**total_physical_reads**|**bigint**|El número total de lecturas físicas realizadas por las ejecuciones de este desencadenador desde que se compiló.|  
|**last_physical_reads**|**bigint**|El número de lecturas físicas realizadas la última vez que se ejecutó el desencadenador.|  
|**min_physical_reads**|**bigint**|El número mínimo de lecturas físicas que ha realizado este desencadenador durante una ejecución.|  
|**max_physical_reads**|**bigint**|El número máximo de lecturas físicas que ha realizado este desencadenador durante una ejecución.|  
|**total_logical_writes**|**bigint**|El número total de lecturas lógicas realizadas por las ejecuciones de este desencadenador desde que se compiló.|  
|**last_logical_writes**|**bigint**|El número de escrituras lógicas realizadas la última vez que se ejecutó el desencadenador.|  
|**min_logical_writes**|**bigint**|El número mínimo de escrituras lógicas que ha realizado este desencadenador durante una ejecución.|  
|**max_logical_writes**|**bigint**|El número máximo de escrituras lógicas que ha realizado este desencadenador durante una ejecución.|  
|**total_logical_reads**|**bigint**|El número total de lecturas lógicas realizadas por las ejecuciones de este desencadenador desde que se compiló.|  
|**last_logical_reads**|**bigint**|El número de lecturas lógicas realizadas la última vez que se ejecutó el desencadenador.|  
|**min_logical_reads**|**bigint**|El número mínimo de lecturas lógicas que ha realizado este desencadenador durante una ejecución.|  
|**max_logical_reads**|**bigint**|El número máximo de lecturas lógicas que ha realizado este desencadenador durante una ejecución.|  
|**total_elapsed_time**|**bigint**|El tiempo total transcurrido, en microsegundos para las ejecuciones completadas de este desencadenador.|  
|**last_elapsed_time**|**bigint**|Tiempo transcurrido, en microsegundos, hasta la finalización de la ejecución más reciente de este desencadenador.|  
|**min_elapsed_time**|**bigint**|El tiempo mínimo transcurrido, en microsegundos, para cualquier ejecución completada de este desencadenador.|  
|**max_elapsed_time**|**bigint**|El tiempo máximo transcurrido, en microsegundos, para cualquier ejecución completada de este desencadenador.| 
|**total_spills**|**bigint**|El número total de páginas derramado mediante la ejecución de este desencadenador desde que se compiló.<br /><br /> **Se aplica a**: a partir de [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**last_spills**|**bigint**|El número de páginas derramado la última vez que se ejecutó el desencadenador.<br /><br /> **Se aplica a**: a partir de [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**min_spills**|**bigint**|El número mínimo de páginas que alguna vez ha derramado este desencadenador durante una ejecución.<br /><br /> **Se aplica a**: a partir de [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**max_spills**|**bigint**|El número máximo de páginas que alguna vez ha derramado este desencadenador durante una ejecución.<br /><br /> **Se aplica a**: a partir de [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
  
## <a name="remarks"></a>Comentarios  
 En [!INCLUDE[ssSDS](../../includes/sssds-md.md)], las vistas de administración dinámica no pueden exponer información que impactaría a la contención de la base de datos ni acerca de otras bases de datos a las que el usuario tenga acceso. Para evitar exponer esta información, cada fila que contiene datos que no pertenecen al inquilino conectado se filtra.  

Cuando se completa una consulta, se actualizan las estadísticas en la vista.  
  
## <a name="permissions"></a>Permissions  
En [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], requiere `VIEW SERVER STATE` permiso.   
En [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] niveles de Premium, requieren la `VIEW DATABASE STATE` permiso en la base de datos. En [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] niveles estándar y básico, requiere la **administrador del servidor** o un **Administrador de Azure Active Directory** cuenta.
  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se devuelve información acerca de los cinco principales desencadenadores identificados por el promedio de tiempo transcurrido.  
  
```sql  
SELECT TOP 5 d.object_id, d.database_id, DB_NAME(database_id) AS 'database_name',   
    OBJECT_NAME(object_id, database_id) AS 'trigger_name', d.cached_time,  
    d.last_execution_time, d.total_elapsed_time,   
    d.total_elapsed_time/d.execution_count AS [avg_elapsed_time],   
    d.last_elapsed_time, d.execution_count  
FROM sys.dm_exec_trigger_stats AS d  
ORDER BY [total_worker_time] DESC;  
```  
  
## <a name="see-also"></a>Vea también  
[Funciones y vistas de administración dinámica &#40; relacionada con la ejecución Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
[sys.dm_exec_sql_text &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)   
[sys.dm_exec_query_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)   
[sys.dm_exec_procedure_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)   
[sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
  
  
