---
title: dbo.cdc_jobs (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- cdc_jobs
- cdc_jobs_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dbo.cdc_jobs
ms.assetid: 85e2d580-1c54-4b81-b7e6-2e12997199fd
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1c455f083d0cb635d62e67a9b8e03e7bdda0b106
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="dbocdcjobs-transact-sql"></a>dbo.cdc_jobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Almacena los parámetros de configuración de captura de datos del cambio para trabajos de captura y limpieza. Esta tabla se almacena en **msdb**.  
  
 
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|Id. de la base de datos en la que se ejecuta el trabajo.|  
|**job_type**|**nvarchar (20)**|Tipo de trabajo, que puede ser 'capture' o 'cleanup'.|  
|**job_id**|**uniqueidentifier**|Id. único asociado al trabajo.|  
|**maxtrans**|**int**|El número máximo de transacciones que se va a procesar en cada ciclo de examen.<br /><br /> **maxtrans** es válida únicamente para los trabajos de captura.|  
|**maxscans**|**int**|El número máximo de ciclos de recorrido para ejecutar en orden y extraer todas las filas del registro.<br /><br /> **maxscans** es válida únicamente para los trabajos de captura.|  
|**continuo**|**bit**|Una marca que indica si el trabajo de captura debe ejecutarse continuamente (1) o solo una vez (0). Para obtener más información, consulte [sys.sp_cdc_add_job &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md).<br /><br /> **continuo** es válida únicamente para los trabajos de captura.|  
|**pollingInterval**|**bigint**|El número de segundos entre los ciclos del recorrido del registro.<br /><br /> **pollingInterval** es válida únicamente para los trabajos de captura.|  
|**retención**|**bigint**|El número de minutos que se conservan las filas de cambios en las tablas de cambios.<br /><br /> **retención** es válida únicamente para los trabajos de limpieza.|  
|**umbral**|**bigint**|El número máximo de entradas correspondientes a operaciones de eliminación que se pueden eliminar mediante una única instrucción durante el proceso de limpieza.|  
  
## <a name="see-also"></a>Vea también  
 [Sys.sp_cdc_add_job &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md)   
 [Sys.sp_cdc_change_job &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-change-job-transact-sql.md)   
 [Sys.sp_cdc_help_jobs &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql.md)   
 [Sys.sp_cdc_drop_job &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-drop-job-transact-sql.md)  
  
  
