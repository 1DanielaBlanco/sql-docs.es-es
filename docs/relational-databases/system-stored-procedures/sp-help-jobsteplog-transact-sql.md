---
title: sp_help_jobsteplog (Transact-SQL) | Documentos de Microsoft
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_help_jobsteplog_TSQL
- sp_help_jobsteplog
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobsteplog
ms.assetid: 1a0be7b1-8f31-4b4c-aadb-586c0e00ed04
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0957fff641ef4306d66c3ee4a233062503008b9e
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="sphelpjobsteplog-transact-sql"></a>sp_help_jobsteplog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve los metadatos sobre un determinado [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] registro de paso de trabajo de agente. **sp_help_jobsteplog** no devuelve el registro real.  

  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_help_jobsteplog { [ @job_id = ] 'job_id' | [ @job_name = ] 'job_name' }  
     [ , [ @step_id = ] step_id ]  
     [ , [ @step_name = ] 'step_name' ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@job_id =**] **'***job_id***'**  
 Número de identificación del trabajo para el que se va a devolver información del registro de pasos de trabajo. *job_id* es **int**, su valor predeterminado es null.  
  
 [  **@job_name =**] **'***job_name***'**  
 Nombre del trabajo. *job_name* es **sysname**, su valor predeterminado es NULL.  
  
> [!NOTE]  
>  Cualquier *job_id* o *job_name* debe especificarse, pero no pueden especificarse ambos.  
  
 [ **@step_id =**] *step_id*  
 Número de identificación del paso en el trabajo. Si no se especifica, se incluirán todos los pasos del trabajo. *step_id* es **int**, su valor predeterminado es null.  
  
 [  **@step_name =**] **'***step_name***'**  
 Nombre del paso en el trabajo. *Step_name* es **sysname**, su valor predeterminado es null.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 0 (correcto) o 1 (error)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|Identificador único del trabajo.|  
|**job_name**|**sysname**|Nombre del trabajo.|  
|**step_id**|**int**|Identificador del paso en el trabajo. Por ejemplo, si el paso es el primer paso en el trabajo, su *step_id* es 1.|  
|**Step_name**|**sysname**|Nombre del paso del trabajo.|  
|**step_uid**|**uniqueidentifier**|Identificador único del paso en el trabajo (generado por el sistema).|  
|**date_created**|**datetime**|Fecha de creación del paso.|  
|**date_modified**|**datetime**|Fecha de la última modificación del paso.|  
|**log_size**|**float**|Tamaño del registro de pasos de trabajo, en megabytes (MB).|  
|**registro**|**nvarchar(max)**|Salida del registro de pasos de trabajo.|  
  
## <a name="remarks"></a>Comentarios  
 **sp_help_jobsteplog** está en el **msdb** base de datos.  
  
## <a name="permissions"></a>Permissions  
 De forma predeterminada, los miembros del rol fijo de servidor **sysadmin** pueden ejecutar este procedimiento almacenado. Al resto de usuarios se les debe conceder uno de los siguientes roles fijos de base de datos del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en la base de datos **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Para detalles sobre los permisos de estos roles, consulte [Roles fijos de base de datos del Agente SQL Server](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
 Los miembros de **SQLAgentUserRole** solo se pueden ver los metadatos del registro de paso de trabajo de pasos de trabajo que les pertenecen.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-returns-job-step-log-information-for-all-steps-in-a-specific-job"></a>A. Devolver información del registro de pasos de trabajo para todos los pasos de un trabajo específico  
 En el ejemplo siguiente se devuelve toda la información del registro de pasos de trabajo del trabajo denominado `Weekly Sales Data Backup`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobsteplog  
    @job_name = N'Weekly Sales Data Backup' ;  
GO  
```  
  
### <a name="b-return-job-step-log-information-about-a-specific-job-step"></a>B. Devolver información del registro de pasos de trabajo para un paso de trabajo específico  
 En el ejemplo siguiente se devuelve información del registro de pasos de trabajo para el primer paso de trabajo del trabajo denominado `Weekly Sales Data Backup`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobsteplog  
    @job_name = N'Weekly Sales Data Backup',  
    @step_id = 1 ;  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [sp_add_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)   
 [sp_delete_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [sp_help_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md)   
 [sp_delete_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [sp_delete_jobsteplog &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobsteplog-transact-sql.md)   
 [Procedimientos almacenados del Agente SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)  
  
  
