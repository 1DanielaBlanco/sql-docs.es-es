---
title: Sys.fn_trace_getinfo (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- fn_trace_getinfo
- fn_trace_getinfo_TSQL
dev_langs: TSQL
helpviewer_keywords:
- traces [SQL Server], status information
- status information [SQL Server], traces
- sys.fn_trace_getinfo function
- fn_trace_getinfo function
ms.assetid: 04b140fe-110a-47b8-98b5-e4c161beb6c9
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 0f7816b4115982fb01f9b456864bb11fc5194ba1
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="sysfntracegetinfo-transact-sql"></a>sys.fn_trace_getinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve información acerca de un seguimiento especificado o de todas los seguimientos existentes.  
  
> **IMPORTANTE:** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Use eventos extendidos en su lugar.    
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sys.fn_trace_getinfo ( { trace_id | NULL | 0 | DEFAULT } )  
```  
  
## <a name="arguments"></a>Argumentos  
 *trace_id*  
 Es el identificador de seguimiento. *trace_id* es **int**.  Las entradas válidas son el número de identificador de un seguimiento, NULL, 0 o DEFAULT. NULL, 0 y DEFAULT son valores equivalentes en este contexto. Especifique NULL, 0 o DEFAULT para devolver información de todos los seguimientos en la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="tables-returned"></a>Tablas devueltas  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|traceid|**int**|Identificador del seguimiento.|  
|propiedad|**int**|Propiedad del seguimiento:<br /><br /> 1= Opciones de seguimiento. Para obtener más información, consulte @options en [sp_trace_create &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md).<br /><br /> 2 = Nombre de archivo<br /><br /> 3 = Tamaño máximo<br /><br /> 4 = Hora de detención<br /><br /> 5 = Estado actual del seguimiento. 0 = detenido. 1 = en ejecución.|  
|value|**sql_variant**|Información acerca de la propiedad de seguimiento especificado.|  
  
## <a name="remarks"></a>Comentarios  
 Cuando se ha pasado el identificador de un seguimiento específico, fn_trace_getinfo devuelve información acerca del seguimiento. Si se pasa un Id. no válido, esta función devuelve un conjunto de filas vacío.  
  
 fn_trace_getinfo anexa una extensión .trc al nombre de un archivo de seguimiento incluido en su conjunto de resultados. Para obtener información acerca de cómo definir un seguimiento, vea [sp_trace_create &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md). Para obtener información similar acerca de los filtros de seguimiento, vea [sys.fn_trace_getfilterinfo &#40; Transact-SQL &#41; ](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md).  
  
 Para obtener un ejemplo completo del uso de procedimientos almacenados de seguimiento, vea [crear un seguimiento &#40; Transact-SQL &#41; ](../../relational-databases/sql-trace/create-a-trace-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Requiere el permiso ALTER TRACE en el servidor.  
  
## <a name="examples"></a>Ejemplos  
 En el siguiente ejemplo se devuelve información acerca de todos los seguimientos activos.  
  
```  
SELECT * FROM sys.fn_trace_getinfo(0) ;  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [Crear un seguimiento &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/create-a-trace-transact-sql.md)   
 [sp_trace_create &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)   
 [sp_trace_generateevent &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)   
 [sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md)   
 [Sys.fn_trace_geteventinfo &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql.md)   
 [Sys.fn_trace_gettable &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-trace-gettable-transact-sql.md)  
  
  
