---
title: sp_changedbowner (Transact-SQL) | Documentos de Microsoft
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
- sp_changedbowner
- sp_changedbowner_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_changedbowner
ms.assetid: 516ef311-e83b-45c9-b9cd-0e0641774c04
caps.latest.revision: 35
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: cb7d6df77a581b82ca79e1962c80df827ffd1718
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33238268"
---
# <a name="spchangedbowner-transact-sql"></a>sp_changedbowner (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cambia el propietario de la base de datos actual.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Use [ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md) en su lugar.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_changedbowner [ @loginame = ] 'login'  
     [ , [ @map = ] remap_alias_flag ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [ @loginame=] '*inicio de sesión*'  
 Es el identificador de inicio de sesión del nuevo propietario de la base de datos actual. *inicio de sesión* es **sysname**, no tiene ningún valor predeterminado. *inicio de sesión* debe ser una ya existente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inicio de sesión o usuario de Windows. *inicio de sesión* no puede ser el propietario de la base de datos actual si ya tiene acceso a la base de datos a través de una cuenta de seguridad de usuario existente dentro de la base de datos. Para evitar esto, quite antes el usuario de la base de datos actual.  
  
 [ @map=] *remap_alias_flag*  
 El *remap_alias_flag* parámetro está obsoleto porque se han quitado los alias de inicio de sesión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Mediante el *remap_alias_flag* parámetro no produce un error pero no tiene ningún efecto.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 0 (correcto) o 1 (error)  
  
## <a name="remarks"></a>Comentarios  
 Después de ejecutar sp_changedbowner, el nuevo propietario se conoce como el usuario dbo de la base de datos. El dbo disfruta implícitamente de permisos para realizar todas las actividades de la base de datos.  
  
 No se puede cambiar el propietario de las bases de datos maestra, de modelos o tempdb del sistema.  
  
 Para mostrar una lista de la validez *inicio de sesión* valores, ejecute el procedimiento almacenado sp_helplogins.  
  
 Si se ejecuta sp_changedbowner solamente con el *inicio de sesión* cambios en los parámetros de base de datos para la propiedad *inicio de sesión*.  
  
 Puede cambiar el propietario de cualquier elemento protegible usando la instrucción ALTER AUTHORIZATION. Para obtener más información, vea [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Requiere permiso TAKE OWNERSHIP en la base de datos. Si el nuevo propietario tiene un usuario correspondiente en la base de datos, requiere el permiso IMPERSONATE en el inicio de sesión, en caso contrario, requiere el permiso CONTROL SERVER en el servidor.  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente, el nombre de inicio de sesión `Albert` se convierte en el propietario de la base de datos actual.  
  
```  
EXEC sp_changedbowner 'Albert';  
```  
  
## <a name="see-also"></a>Vea también  
 [Procedimientos almacenados de seguridad &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE DATABASE &#40;Transact-SQL de SQL Server&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [sp_dropalias &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropalias-transact-sql.md)   
 [sp_dropuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_helpdb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdb-transact-sql.md)   
 [sp_helplogins &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helplogins-transact-sql.md)   
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
