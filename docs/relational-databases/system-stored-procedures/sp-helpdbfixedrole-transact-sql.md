---
title: sp_helpdbfixedrole (Transact-SQL) | Documentos de Microsoft
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
- sp_helpdbfixedrole
- sp_helpdbfixedrole_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpdbfixedrole
ms.assetid: ad87e9a0-b901-4e37-9950-aa517d680fc3
caps.latest.revision: 24
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 2a1ca726e6770fd4a36e34651a83c55ab1e5475b
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33252776"
---
# <a name="sphelpdbfixedrole-transact-sql"></a>sp_helpdbfixedrole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve la lista de los roles fijos de base de datos.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_helpdbfixedrole [ [ @rolename = ] 'role' ]   
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@rolename =** ] **'***rol***'**  
 Nombre de un rol fijo de base de datos. *rol* es **sysname**, su valor predeterminado es null. Si *rol* está especificado, se devuelve solo la información de ese rol; en caso contrario, se devuelve una lista y una descripción de todos los roles de base de datos fija.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 0 (correcto) o 1 (error)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**DbFixedRole.**|**sysname**|Nombre del rol fijo de base de datos.|  
|**Description**|**nvarchar (70)**|Descripción de **DbFixedRole.**|  
  
## <a name="remarks"></a>Comentarios  
 Los roles fijos de base de datos, como se muestra en la siguiente tabla, se definen de nivel de base de datos y tienen permisos para realizar actividades administrativas específicas en la base de datos. No es posible agregar o quitar roles fijos de base de datos. No es posible cambiar los permisos concedidos a un rol fijo de base de datos.  
  
|Rol fijo de base de datos|Description|  
|-------------------------|-----------------|  
|**db_owner**|Propietarios de base de datos|  
|**db_accessadmin**|Administradores de acceso a la base de datos|  
|**db_securityadmin**|Administradores de seguridad de la base de datos|  
|**db_ddladmin**|Administradores de DDL de la base de datos|  
|**db_backupoperator**|Operadores de copia de seguridad de la base de datos|  
|**db_datareader**|Lectores de datos de la base de datos|  
|**db_datawriter**|Escritores de datos de la base de datos|  
|**db_denydatareader**|Lectores de datos denegados de la base de datos|  
|**db_denydatawriter**|Escritores de datos denegados de la base de datos|  
  
 En la siguiente tabla se muestran los procedimientos almacenados que se utilizan para modificar los roles de base de datos.  
  
|Procedimiento almacenado|Acción|  
|----------------------|------------|  
|**sp_addrolemember**|Agrega un usuario de base de datos a un rol fijo de base de datos.|  
|**sp_helprole**|Presenta la lista de los miembros de un rol fijo de base de datos.|  
|**sp_droprolemember**|Quita un miembro de un rol fijo de base de datos.|  
  
## <a name="permissions"></a>Permissions  
 Debe pertenecer al rol **public** .  
  
 La información mostrada está sometida a restricciones de acceso a los metadatos. No se mostrarán las entidades en las que la entidad de seguridad no tiene permiso. Para obtener más información, consulte [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Ejemplos  
 En el siguiente ejemplo se muestra la lista de todos los roles fijos de base de datos.  
  
```  
EXEC sp_helpdbfixedrole;  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [Procedimientos almacenados de seguridad &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sp_dbfixedrolepermission &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbfixedrolepermission-transact-sql.md)   
 [sp_droprolemember & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)   
 [sp_helprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helprole-transact-sql.md)   
 [sp_helprolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helprolemember-transact-sql.md)   
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
