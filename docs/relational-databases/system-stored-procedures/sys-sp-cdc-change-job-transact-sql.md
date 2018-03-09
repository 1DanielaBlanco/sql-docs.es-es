---
title: Sys.sp_cdc_change_job (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sp_cdc_change_job_TSQL
- sys.sp_cdc_change_job
- sp_cdc_change_job_TSQL
- sp_cdc_change_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_change_job
ms.assetid: ea918888-0fc5-4cc1-b301-26b2a9fbb20d
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8fb123d1d872ed43131db241bf9c94944000fe12
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/27/2017
---
# <a name="sysspcdcchangejob-transact-sql"></a>sys.sp_cdc_change_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifica la configuración de un trabajo de captura o de limpieza de captura de datos de cambio en la base de datos actual. Para ver la configuración actual de un trabajo, consulte la [dbo.cdc_jobs](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md) tabla o usar [sp_cdc_help_jobs](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql.md).  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sys.sp_cdc_change_job [ [ @job_type = ] 'job_type' ]  
    [ , [ @maxtrans = ] max_trans ]   
    [ , [ @maxscans = ] max_scans ]   
    [ , [ @continuous = ] continuous ]   
    [ , [ @pollinginterval = ] polling_interval ]   
    [ , [ @retention ] = retention ]   
    [ @threshold = ] 'delete threshold'  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@job_type=** ] **'***job_type***'**  
 Tipo de trabajo para modificar. *job_type* es **nvarchar (20)** su valor predeterminado es 'capture'. Las entradas válidas son 'capture' y 'cleanup'.  
  
 [  **@maxtrans**  ]  **=**  *max_trans*  
 Número máximo de transacciones para procesar en cada ciclo de recorrido. *max_trans* es **int** su valor predeterminado es null, que no indica que ningún cambio para este parámetro. Si se especifica, el valor debe ser un entero positivo.  
  
 *max_trans* es válida únicamente para los trabajos de captura.  
  
 [  **@maxscans**  ]  **=**  *max_scans*  
 Número máximo de ciclos de recorrido que se ejecutarán para extraer todas las filas del registro. *max_scans* es **int** su valor predeterminado es null, que no indica que ningún cambio para este parámetro.  
  
 *max_scan* es válida únicamente para los trabajos de captura.  
  
 [  **@continuous**  ]  **=**  *continua*  
 Indica si el trabajo de captura se ejecutará continuamente (1), o solo una vez (0). *continuo* es **bits** su valor predeterminado es null, que no indica que ningún cambio para este parámetro.  
  
 Cuando *continua* = 1, el [sp_cdc_scan](../../relational-databases/system-stored-procedures/sys-sp-cdc-scan-transact-sql.md) trabajo examina el registro y procesa hasta (*max_trans* \* *max_scans*) transacciones. A continuación, espera el número de segundos especificado en *polling_interval* antes de comenzar el recorrido del registro siguiente.  
  
 Cuando *continua* = 0, el **sp_cdc_scan** hasta se ejecuta el trabajo *max_scans* recorridos del registro, procesando hasta *max_trans* transacciones durante cada recorrido y, a continuación, se cierra.  
  
 Si  **@continuous**  se cambia de 1 a 0,  **@pollinginterval**  se establece automáticamente en 0. Un valor especificado para  **@pollinginterval**  distinto de 0 se omite.  
  
 Si  **@continuous**  se omite o se establece explícitamente en NULL y  **@pollinginterval**  se establece explícitamente en un valor mayor que 0,  **@continuous**  automáticamente Establezca en 1.  
  
 *continuo* es válida únicamente para los trabajos de captura.  
  
 [  **@pollinginterval**  ]  **=**  *polling_interval*  
 Número de segundos entre los ciclos de recorrido del registro. *polling_interval* es **bigint** su valor predeterminado es null, que no indica que ningún cambio para este parámetro.  
  
 *polling_interval* es válida sólo para la captura de los trabajos al *continua* está establecido en 1.  
  
 [  **@retention**  ]  **=**  *retención*  
 Número de minutos durante los que las filas de cambio deben retenerse en las tablas de cambio. *retención* es **bigint** su valor predeterminado es null, que no indica que ningún cambio para este parámetro. El valor máximo es 52494800 (100 años). Si se especifica, el valor debe ser un entero positivo.  
  
 *retención* es válida únicamente para los trabajos de limpieza.  
  
 [  **@threshold=** ] **'***eliminar umbral***'**  
 Número máximo de entradas de eliminación que se pueden eliminar mediante el uso de una única instrucción en el proceso de limpieza. *eliminar umbral* es **bigint** su valor predeterminado es null, que no indica que ningún cambio para este parámetro. *eliminar umbral* es válida únicamente para los trabajos de limpieza.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
 Ninguno  
  
## <a name="remarks"></a>Comentarios  
 Si se omite un parámetro, el valor asociado en el [dbo.cdc_jobs](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md) no se actualiza la tabla. Un parámetro establecido explícitamente en NULL se trata como si se omitiese el parámetro.  
  
 Si se especifica un parámetro que no es válido para el tipo de trabajo, la instrucción generará un error.  
  
 Cambios a un trabajo no surtirán efecto hasta que se detenga el trabajo mediante el uso de [sp_cdc_stop_job](../../relational-databases/system-stored-procedures/sys-sp-cdc-stop-job-transact-sql.md) y reiniciar mediante el uso de [sp_cdc_start_job](../../relational-databases/system-stored-procedures/sys-sp-cdc-start-job-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Debe pertenecer a la **db_owner** rol fijo de base de datos.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-changing-a-capture-job"></a>A. Cambiar un trabajo de captura  
 El siguiente ejemplo se actualiza el `@job_type`, `@maxscans`, y `@maxtrans` parámetros de un trabajo de captura en el `AdventureWorks2012` base de datos. El resto de parámetros válidos para un trabajo captura, `@continuous` y `@pollinginterval`, se omiten; sus valores no se modifican.  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_change_job   
    @job_type = N'capture',  
    @maxscans = 1000,  
    @maxtrans = 15;  
GO  
```  
  
### <a name="b-changing-a-cleanup-job"></a>B. Cambiar un trabajo de limpieza  
 En el siguiente ejemplo se actualiza un trabajo de limpieza en la base de datos `AdventureWorks2012`. Todos los parámetros válidos para este tipo de trabajo, excepto  **@threshold** , se especifican. El valor de  **@threshold**  no se modifica.  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_change_job   
    @job_type = N'cleanup',  
    @retention = 2880;  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [dbo.cdc_jobs &#40; Transact-SQL &#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)   
 [Sys.sp_cdc_enable_table &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)   
 [sys.sp_cdc_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md)  
  
  
