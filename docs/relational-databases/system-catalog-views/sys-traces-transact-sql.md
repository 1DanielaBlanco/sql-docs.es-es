---
title: Sys.Traces (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- traces
- sys.traces_TSQL
- sys.traces
- traces_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.traces catalog view
ms.assetid: 4a03be22-b7da-4e2a-97ff-94bed890a620
caps.latest.revision: "23"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6e195b27208480e28b6ac18b0b40d36e7c543312
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="systraces-transact-sql"></a>sys.traces (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  El **sys.traces** vista de catálogo contiene las trazas de ejecución actuales en el sistema. Esta vista se ha diseñado como un reemplazo para el **fn_trace_getinfo** función.  
  
 Para obtener una lista completa de los eventos de seguimiento compatibles, consulte [SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md).  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Use vistas de catálogo de eventos extendidos en su lugar.  
  
||  
|-|  
|**Se aplica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a través de la [versión actual](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Id. de seguimiento.|  
|**status**|**int**|Estado de la seguimiento:<br /><br /> 0 = detenida<br /><br /> 1 = en ejecución|  
|**ruta de acceso**|**nvarchar (260)**|Ruta de acceso al archivo de seguimiento. Este valor es NULL se trata de una seguimiento de conjunto de filas.|  
|**max_size**|**bigint**|Tamaño máximo permitido del archivo de seguimiento, en megabytes (MB). Este valor es NULL se trata de una seguimiento de conjunto de filas.|  
|**stop_time**|**datetime**|Hora a la que se detiene la seguimiento en ejecución.|  
|**max_files**|**int**|Número máximo de archivos de sustitución incremental. Este valor es NULL si no se establece el número máximo.|  
|**is_rowset**|**bit**|1 = Seguimiento de conjunto de filas.|  
|**is_rollover**|**bit**|1 = La opción de sustitución incremental está habilitada.|  
|**is_shutdown**|**bit**|1 = La opción de cierre está habilitada.|  
|**is_default**|**bit**|1 = Seguimiento predeterminado.|  
|**buffer_count**|**int**|Número de búferes en memoria utilizados por la seguimiento.|  
|**buffer_size**|**int**|Tamaño de cada búfer (KB).|  
|**file_position**|**bigint**|Última posición del archivo de seguimiento. Este valor es NULL se trata de una seguimiento de conjunto de filas.|  
|**reader_spid**|**int**|Identificador de sesión del lector de seguimiento del conjunto de filas. Este valor es NULL cuando se trata de un seguimiento de archivo.|  
|**start_time**|**datetime**|Hora de inicio de la seguimiento.|  
|**last_event_time**|**datetime**|Hora en que se desencadenó el último evento.|  
|**event_count**|**bigint**|Número total de eventos que se han producido.|  
|**dropped_event_count**|**int**|Número total de eventos que se han quitado.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Para obtener más información, consulte [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vea también  
 [Vistas de catálogo de objetos &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Sys.trace_categories &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-trace-categories-transact-sql.md)   
 [Sys.trace_columns &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-trace-columns-transact-sql.md)   
 [Sys.trace_events &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-trace-events-transact-sql.md)   
 [Sys.trace_event_bindings &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-trace-event-bindings-transact-sql.md)   
 [Sys.trace_subclass_values &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-trace-subclass-values-transact-sql.md)  
  
  
