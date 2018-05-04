---
title: Sys.dm_cdc_errors (Transact-SQL) | Documentos de Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_cdc_errors_TSQL
- dm_cdc_errors
- sys.dm_cdc_errors
- sys.dm_cdc_errors_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_cdc_errors dynamic management view
- change data capture [SQL Server], error reporting
ms.assetid: 898f2d76-9e63-45ef-94da-8034e86004ab
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1dff0b78d270982c6dfeb84d55121dbb8c190c59
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="change-data-capture---sysdmcdcerrors"></a>Captura de datos modificados - sys.dm_cdc_errors
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve una fila para cada error encontrado durante la sesión de recorrido de registro de captura de datos del cambio.  
 
 
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|Id. de la sesión.<br /><br /> 0 = el error no se produjo durante una sesión de recorrido del registro.|  
|**phase_number**|**int**|Número que indica la fase de la sesión que estaba en el momento del error se ha producido. Para obtener una descripción de cada fase, vea [sys.dm_cdc_log_scan_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/change-data-capture-sys-dm-cdc-log-scan-sessions.md).|  
|**entry_time**|**datetime**|Fecha y hora de registro del error. Este valor corresponde a la marca de tiempo en el registro de errores de SQL.|  
|**error_number**|**int**|Id. del mensaje de error.|  
|**error_severity**|**int**|Nivel de gravedad del mensaje, entre 1 y 25.|  
|**error_state**|**int**|Número de estado del error.|  
|**error_message**|**nvarchar(1024)**|Texto del mensaje del error.|  
|**start_lsn**|**nvarchar(23)**|Valor LSN inicial de las filas que se estaban procesando en el momento de producirse el error.<br /><br /> 0 = el error no se produjo durante una sesión de recorrido del registro.|  
|**begin_lsn**|**nvarchar(23)**|Valor LSN inicial de la transacción que se estaba procesando en el momento de producirse el error.<br /><br /> 0 = el error no se produjo durante una sesión de recorrido del registro.|  
|**sequence_value**|**nvarchar(23)**|Valor LSN de las filas que se estaban procesando en el momento de producirse el error.<br /><br /> 0 = el error no se produjo durante una sesión de recorrido del registro.|  
  
## <a name="remarks"></a>Comentarios  
 **Sys.dm_cdc_errors** contiene información de error para las 32 sesiones anteriores.  
  
## <a name="permissions"></a>Permissions  
 Requiere el permiso VIEW DATABASE STATE para consultar el **sys.dm_cdc_errors** vista de administración dinámica. Para obtener más información acerca de los permisos en las vistas de administración dinámica, consulte [funciones y vistas de administración dinámica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md).  
  
## <a name="see-also"></a>Vea también  
 [sys.dm_cdc_log_scan_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/change-data-capture-sys-dm-cdc-log-scan-sessions.md)   
 [sys.dm_repl_traninfo &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-repl-traninfo-transact-sql.md)  
  
  

