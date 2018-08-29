---
title: sp_helplogins (Transact-SQL) | Microsoft Docs
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
- sp_helplogins_TSQL
- sp_helplogins
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helplogins
ms.assetid: f9ad3767-5b9f-420d-8922-b637811404f7
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d497fdd54fd0a8fce44282a2caa819fef60a76fb
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "43028794"
---
# <a name="sphelplogins-transact-sql"></a>sp_helplogins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Proporciona información acerca de inicios de sesión y sus usuarios asociados en cada base de datos.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_helplogins [ [ @LoginNamePattern = ] 'login' ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [ **@LoginNamePattern =** ] **'***login***'**  
 Es un nombre de inicio de sesión. *login* es de tipo **sysname** y su valor predeterminado es NULL. *inicio de sesión* debe existir si se especifica. Si *inicio de sesión* no es se especifica, se devuelve información sobre todos los inicios de sesión.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 0 (correcto) o 1 (error)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
 El primer informe contiene información acerca de cada inicio de sesión especificado, tal como se muestra en la tabla siguiente.  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**LoginName**|**sysname**|Nombre de inicio de sesión.|  
|**SID**|**varbinary(85)**|Identificador de seguridad (SID) del inicio de sesión.|  
|**DefDBName**|**sysname**|Base de datos predeterminada que **LoginName** utiliza al conectarse a una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**DefLangName**|**sysname**|Idioma predeterminado utilizado por **LoginName**.|  
|**Auser**|**Char (5)**|Sí = **LoginName** tiene un nombre de usuario asociada en una base de datos.<br /><br /> No = **LoginName** no tiene un nombre de usuario asociado.|  
|**Remota**|**caracter (7)**|Sí = **LoginName** tiene asociado un inicio de sesión remoto.<br /><br /> No = **LoginName** no tiene asociado un inicio de sesión.|  
  
 El segundo informe contiene información sobre los usuarios asignados a cada inicio de sesión y las pertenencias a roles del inicio de sesión como se muestra en la tabla siguiente.  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**LoginName**|**sysname**|Nombre de inicio de sesión.|  
|**DBName**|**sysname**|Base de datos predeterminada que **LoginName** utiliza al conectarse a una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**UserName**|**sysname**|Cuenta de usuario que **LoginName** está asociado en **DBName**y los roles que **LoginName** es un miembro en **DBName**.|  
|**UserOrAlias**|**Char (8)**|MemberOf = **UserName** es un rol.<br /><br /> Usuario = **UserName** es una cuenta de usuario.|  
  
## <a name="remarks"></a>Notas  
 Antes de quitar un inicio de sesión, utilice **sp_helplogins** para identificar las cuentas de usuario que se asignan al inicio de sesión.  
  
## <a name="permissions"></a>Permisos  
 Debe pertenecer a la **securityadmin** rol fijo de servidor.  
  
 Para identificar todas las cuentas de usuario asignadas a un inicio de sesión determinado, **sp_helplogins** debe comprobar todas las bases de datos en el servidor. Por lo tanto, en todas las bases de datos del servidor se tiene que dar, como mínimo, una de las condiciones siguientes:  
  
-   El usuario que se está ejecutando **sp_helplogins** tiene permiso para acceder a la base de datos.  
  
-   El **invitado** cuenta de usuario está habilitada en la base de datos.  
  
 Si **sp_helplogins** no puede tener acceso a una base de datos, **sp_helplogins** devolverá tanta información como posible y mostrará el mensaje de error 15622.  
  
## <a name="examples"></a>Ejemplos  
 En el siguiente ejemplo se proporciona información sobre el inicio de sesión `John`.  
  
```  
EXEC sp_helplogins 'John';  
GO  
  
LoginName SID                        DefDBName DefLangName AUser ARemote   
--------- -------------------------- --------- ----------- ----- -------   
John      0x23B348613497D11190C100C  master    us_english  yes   no  
  
(1 row(s) affected)  
  
LoginName   DBName   UserName   UserOrAlias   
---------   ------   --------   -----------   
John        pubs     John       User          
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vea también  
 [Procedimientos almacenados de seguridad &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_helpdb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdb-transact-sql.md)   
 [sp_helpuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)   
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
