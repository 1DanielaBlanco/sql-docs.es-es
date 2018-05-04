---
title: Sys.dm_exec_cached_plan_dependent_objects (Transact-SQL) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_cached_plan_dependent_objects
- dm_exec_cached_plan_dependent_objects_TSQL
- sys.dm_exec_cached_plan_dependent_objects_TSQL
- dm_exec_cached_plan_dependent_objects
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_cached_plan_dependent_objects dynamic management function
ms.assetid: 9b6cf5f7-b267-44fb-aac8-f49c9aa10cc1
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: e9303dd028cdc979e978e05ea87afe7718a566ba
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmexeccachedplandependentobjects-transact-sql"></a>sys.dm_exec_cached_plan_dependent_objects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Devuelve una fila para cada plan de ejecución de [!INCLUDE[tsql](../../includes/tsql-md.md)], plan de ejecución de Common Language Runtime (CLR) y cursor asociado a un plan.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dm_exec_cached_plan_dependent_objects(plan_handle)  
```  
  
## <a name="arguments"></a>Argumentos  
 *plan_handle*  
 Identifica de forma exclusiva un plan de ejecución de consultas de un proceso por lotes que se ha ejecutado y cuyo plan reside en la caché del plan. *plan_handle* es **varbinary(64)**. El *plan_handle* puede obtenerse de los siguientes objetos de administración dinámica:  
  
-   [sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
  
-   [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
-   [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
## <a name="table-returned"></a>Tabla devuelta  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**usecounts**|**int**|Número de veces que se ha usado un contexto de ejecución o un cursor.<br /><br /> La columna no acepta valores NULL.|  
|**memory_object_address**|**varbinary (8)**|Dirección de memoria del contexto de ejecución o el cursor.<br /><br /> La columna no acepta valores NULL.|  
|**cacheobjtype**|**nvarchar(50)**|El tipo de objeto de caché de Plan. La columna no acepta valores NULL. Los valores posibles son<br /><br /> Plan ejecutable<br /><br /> Función CLR compilada<br /><br /> Procedimiento CLR compilado<br /><br /> Cursor|  
  
## <a name="permissions"></a>Permissions  
 es necesario contar con el permiso VIEW SERVER STATE en el servidor.  
  
## <a name="physical-joins"></a>Combinaciones físicas  
 ![Diagrama de relaciones](../../relational-databases/system-dynamic-management-views/media/dm-dependent-objects.gif "diagrama de relaciones")  
  
## <a name="relationship-cardinalities"></a>Cardinalidades de relación  
  
|De|A|El|Relación|  
|----------|--------|--------|------------------|  
|**dm_exec_cached_plan_dependent_objects**|**dm_os_memory_objects**|**memory_object_address**|Uno a uno|  
  
## <a name="see-also"></a>Vea también  
 [Vistas de administración dinámica y funciones relacionadas con ejecuciones &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [Funciones y vistas de administración dinámica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Sys.syscacheobjects &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-syscacheobjects-transact-sql.md)  
  
  
