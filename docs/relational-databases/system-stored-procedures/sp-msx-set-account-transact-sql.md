---
title: sp_msx_set_account (Transact-SQL) | Microsoft Docs
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
- sp_msx_set_account
- sp_msx_set_account_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_msx_set_account
ms.assetid: 314ec720-3a37-48f7-bb6b-8d5b894bf843
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7d463863e71a0ba2899a987fdb425d08c8f5245a
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2018
---
# <a name="spmsxsetaccount-transact-sql"></a>sp_msx_set_account (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Establece el nombre y la contraseña de la cuenta del servidor maestro del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en el servidor de destino.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_msx_set_account [ @credential_name = ] 'credential_name'  | [ @credential_id = ] credential_id  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@credential_name=** ] **'***credential_name***'**  
 Nombre de la credencial que se utilizará para iniciar sesión en el servidor maestro. El nombre proporcionado debe ser el nombre de una credencial existente. Cualquier *credential_name* o *credential_id* debe especificarse.  
  
 [  **@credential_id=** ] *credential_id*  
 Identificador de la credencial que se utilizará para iniciar sesión en el servidor maestro. Debe ser el identificador de una credencial existente. Cualquier *credential_name* o *credential_id* debe especificarse.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
 Ninguno.  
  
## <a name="remarks"></a>Comentarios  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utiliza las credenciales para almacenar la información de nombre y la contraseña de usuario que utiliza un servidor de destino para iniciar sesión en un servidor maestro. Este procedimiento establece la credencial que utiliza el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de este servidor de destino para iniciar sesión en el servidor maestro.  
  
 La credencial especificada debe existir. Para obtener más información acerca de cómo crear una credencial, vea [CREATE CREDENTIAL &#40; Transact-SQL &#41; ](../../t-sql/statements/create-credential-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Permisos de ejecución para **sp_msx_set_account** predeterminada a los miembros de la **sysadmin** rol fijo de servidor.  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se establece este servidor de manera que utilice la credencial `MsxAccount` para iniciar sesión en el servidor maestro.  
  
```  
USE msdb ;  
GO  
  
EXECUTE dbo.sp_msx_set_account @credential_name = MsxAccount ;  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [Agente SQL Server almacena procedimientos &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sp_msx_get_account &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-msx-get-account-transact-sql.md)  
  
  
