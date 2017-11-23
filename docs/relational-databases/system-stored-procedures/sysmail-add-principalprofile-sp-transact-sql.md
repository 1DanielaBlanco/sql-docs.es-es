---
title: sysmail_add_principalprofile_sp (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysmail_add_principalprofile_sp_TSQL
- sysmail_add_principalprofile_sp
dev_langs: TSQL
helpviewer_keywords: sysmail_add_principalprofile_sp
ms.assetid: b2a0b313-abb9-4c23-8511-db77ca8172b3
caps.latest.revision: "36"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 66f200bea02dc9be6fea1c9d8c55b746a4ace61e
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="sysmailaddprincipalprofilesp-transact-sql"></a>sysmail_add_principalprofile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Concede permiso a un usuario o un rol de base de datos para usar un perfil de Correo electrónico de base de datos.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sysmail_add_principalprofile_sp  { [ @principal_id = ] principal_id | [ @principal_name = ] 'principal_name' } ,  
    { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' }  
    [ , [ @is_default ] = 'is_default' ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@principal_id**  =] *principal_id*  
 El identificador del usuario de base de datos o del rol en el **msdb** base de datos para la asociación. *principal_id* es **int**, su valor predeterminado es null. Cualquier *principal_id* o *principal_name* debe especificarse. A *principal_id* de **0** convierte este perfil una pública, conceder acceso a todas las entidades en la base de datos.  
  
 [  **@principal_name**  =] **'***principal_name***'**  
 El nombre del usuario de base de datos o del rol en el **msdb** base de datos para la asociación. *principal_name* es **sysname**, su valor predeterminado es null. Cualquier *principal_id* o *principal_name* debe especificarse. A *principal_name* de **'public'** convierte este perfil una pública, conceder acceso a todas las entidades en la base de datos.  
  
 [  **@profile_id**  =] *profile_id*  
 Id. del perfil para la asociación. *profile_id* es **int**, su valor predeterminado es null. Cualquier *profile_id* o *profile_name* debe especificarse.  
  
 [  **@profile_name**  =] **'***profile_name***'**  
 Nombre del perfil para la asociación. *profile_name* es **sysname**, no tiene ningún valor predeterminado. Cualquier *profile_id* o *profile_name* debe especificarse.  
  
 [  **@is_default**  =] *is_default*  
 Especifica si este perfil es el predeterminado para la entidad de seguridad. Una entidad de seguridad debe tener solo un perfil predeterminado. *is_default* es **bits**, no tiene ningún valor predeterminado.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Comentarios  
 Para convertir un perfil público, especifique un  **@principal_id**  de **0** o un  **@principal_name**  de **público**. Un perfil público está disponible para todos los usuarios de la **msdb** la base de datos, aunque los usuarios también deben ser un miembro de **DatabaseMailUserRole** para ejecutar **sp_send_dbmail**.  
  
 El usuario de la base de datos solo puede tener un perfil predeterminado. Cuando  **@is_default**  es '**1**' y el usuario ya está asociado a uno o varios perfiles, el perfil especificado se convierte en el perfil predeterminado para el usuario. El perfil predeterminado anterior sigue estando asociado con el usuario, pero ya no es el perfil predeterminado.  
  
 Cuando  **@is_default**  es '**0**' y no existe otra asociación, el procedimiento almacenado devuelve un error.  
  
 El procedimiento almacenado **sysmail_add_principalprofile_sp** está en el **msdb** la base de datos y es propiedad de la **dbo** esquema. El procedimiento se debe ejecutar con un nombre de tres partes si la base de datos actual no es **msdb**.  
  
## <a name="permissions"></a>Permissions  
 Permisos de ejecución para este procedimiento de forma predeterminada a los miembros de la **sysadmin** rol fijo de servidor.  
  
## <a name="examples"></a>Ejemplos  
 **A. Crear una asociación y configurar el perfil predeterminado**  
  
 En el ejemplo siguiente se crea una asociación entre el perfil denominado `AdventureWorks Administrator Profile` y **msdb** usuario de base de datos `ApplicationUser`. El perfil es el predeterminado del usuario.  
  
```  
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp  
    @principal_name = 'ApplicationUser',  
    @profile_name = 'AdventureWorks Administrator Profile',  
    @is_default = 1 ;  
```  
  
 **B. Convertir un perfil en el perfil público predeterminado**  
  
 En el siguiente ejemplo se configura el perfil `AdventureWorks Public Profile` el perfil público predeterminado para los usuarios de la **msdb** base de datos.  
  
```  
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp  
    @principal_name = 'public',  
    @profile_name = 'AdventureWorks Public Profile',  
    @is_default = 1 ;  
```  
  
## <a name="see-also"></a>Vea también  
 [Correo electrónico de base de datos](../../relational-databases/database-mail/database-mail.md)   
 [Objetos de configuración de correo electrónico de base de datos](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Correo electrónico de base de datos almacenados procedimientos &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
