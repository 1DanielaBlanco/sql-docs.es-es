---
title: sp_update_category (Transact-SQL) | Microsoft Docs
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
- sp_update_category
- sp_update_category_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_category
ms.assetid: 098b926a-b078-4122-a5e1-3ef54b979dd4
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fab5ea9aea708af028114ef59e9274931c8257f9
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2018
---
# <a name="spupdatecategory-transact-sql"></a>sp_update_category (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cambia el nombre de una categoría.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_update_category  
     [@class =] 'class' ,   
     [@name =] 'old_name' ,  
     [@new_name =] 'new_name'  
```  
  
## <a name="arguments"></a>Argumentos  
 [ **@class =**] **'***class***'**  
 Clase de la categoría que se va a actualizar. *clase*es **varchar (8)**, no tiene ningún valor predeterminado y puede ser uno de estos valores.  
  
|Value|Description|  
|-----------|-----------------|  
|**ALERT**|Actualiza una categoría de alerta.|  
|**JOB**|Actualiza una categoría de trabajo.|  
|**OPERADOR**|Actualiza una categoría de operador.|  
  
 [ **@name =**] **'***old_name***'**  
 Nombre actual de la categoría. *Nombre_antiguo*es **sysname**, no tiene ningún valor predeterminado.  
  
 [ **@new_name =**] **'***new_name***'**  
 El nuevo nombre de la categoría. *new_name*es **sysname**, no tiene ningún valor predeterminado.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Comentarios  
 **sp_update_category** se debe ejecutar desde la **msdb** base de datos.  
  
## <a name="permissions"></a>Permissions  
 Para ejecutar este procedimiento almacenado, deben concederse a los usuarios la **sysadmin** rol fijo de servidor.  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se cambia el nombre de una categoría de trabajo de `AdminJobs` a `Administrative Jobs`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_category  
  @class = N'JOB',  
  @name = N'AdminJobs',  
  @new_name = N'Administrative Jobs' ;  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [sp_add_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-category-transact-sql.md)   
 [sp_delete_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-category-transact-sql.md)   
 [sp_help_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-category-transact-sql.md)   
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
