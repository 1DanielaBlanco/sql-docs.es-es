---
title: sp_password (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_password
- sp_password_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_password
ms.assetid: 0ecbec81-e637-44a9-a61e-11bf060ef084
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 8529ad14ec49881e8628fb46e9122709e082bf18
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "43038617"
---
# <a name="sppassword-transact-sql"></a>sp_password (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Agrega o cambia una contraseña para un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inicio de sesión.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Use [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md) en su lugar.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_password [ [ @old = ] 'old_password' , ]  
     { [ @new =] 'new_password' }  
     [ , [ @loginame = ] 'login' ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@old=** ] **'***old_password***'**  
 Es la contraseña antigua. *old_password* es **sysname**, su valor predeterminado es null.  
  
 [  **@new=** ] **'***nuevacontraseña***'**  
 Es la nueva contraseña. *nuevacontraseña* es **sysname**, no tiene ningún valor predeterminado. *old_password* debe especificarse si no se utilizan parámetros con nombre.  
  
> [!IMPORTANT]  
>  No utilice una contraseña NULL. Utilice una contraseña segura. Para obtener más información, consulte [Strong Passwords](../../relational-databases/security/strong-passwords.md).  
  
 [  **@loginame=** ] **'***inicio de sesión***'**  
 Es el nombre del inicio de sesión afectado por el cambio de contraseña. *login* es de tipo **sysname** y su valor predeterminado es NULL. *inicio de sesión* ya debe existir y solo pueden especificarlo los miembros de la **sysadmin** o **securityadmin** roles fijos de servidor.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 0 (correcto) o 1 (error)  
  
## <a name="remarks"></a>Notas  
 **sp_password** llama a ALTER LOGIN. Esta instrucción admite opciones adicionales. Para obtener información acerca de cómo cambiar las contraseñas, consulte [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md).  
  
 **sp_password** no se puede ejecutar dentro de una transacción definida por el usuario.  
  
## <a name="permissions"></a>Permisos  
 Requiere el permiso ALTER ANY LOGIN. También requiere el permiso CONTROL SERVER para restablecer una contraseña sin suministrar la antigua, o si el inicio de sesión que se va a cambiar tiene el permiso CONTROL SERVER.  
  
 Una entidad de seguridad puede cambiar su propia contraseña.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-changing-the-password-of-a-login-without-knowing-the-old-password"></a>A. Cambiar la contraseña de un inicio de sesión sin conocer la contraseña antigua  
 En el siguiente ejemplo se muestra cómo utilizar `ALTER LOGIN` para cambiar la contraseña del inicio de sesión `Victoria` a `B3r1000d#2-36`. Éste es el método preferido. El usuario que ejecute este comando debe tener el permiso CONTROL SERVER.  
  
```  
ALTER LOGIN Victoria WITH PASSWORD = 'B3r1000d#2-36';  
GO  
```  
  
### <a name="b-changing-a-password"></a>B. Cambiar una contraseña  
 En el siguiente ejemplo se muestra cómo utilizar `ALTER LOGIN` para cambiar la contraseña del inicio de sesión de `Victoria` de `B3r1000d#2-36` a `V1cteAmanti55imE`. Éste es el método preferido. El usuario `Victoria` puede ejecutar este comando sin permisos adicionales. Otros usuarios necesitan el permiso ALTER ANY LOGIN.  
  
```  
ALTER LOGIN Victoria WITH   
     PASSWORD = 'V1cteAmanti55imE'   
     OLD_PASSWORD = 'B3r1000d#2-36';  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [Procedimientos almacenados de seguridad &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [sp_addlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_adduser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adduser-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [sp_revokelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
