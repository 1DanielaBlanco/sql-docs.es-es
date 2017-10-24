---
title: Crear rol (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 04/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE ROLE
- DATABASE ROLE
- ROLE_TSQL
- DATABASE_ROLE_TSQL
- CREATE_ROLE_TSQL
- CREATE DATABASE ROLE
- ROLE
- CREATE_DATABASE_ROLE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database roles [SQL Server], creating
- CREATE DATABASE ROLE statement
- roles [SQL Server], creating
- CREATE ROLE statement
ms.assetid: b0cd54ad-e81d-4d71-acec-8a6d7261ca08
caps.latest.revision: 54
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 21e3cca3d07d7f53d646b5dd052fd40d0fa2cc1a
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="create-role-transact-sql"></a>CREATE ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Crea un rol de base de datos nuevo en la base de datos actual.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
CREATE ROLE role_name [ AUTHORIZATION owner_name ]  
```  
  
## <a name="arguments"></a>Argumentos  
 *role_name*  
 Es el nombre del rol que se va a crear.  
  
 AUTORIZACIÓN *owner_name*  
 Es el usuario o el rol de base de datos que será propietario del nuevo rol. Si no se especifica un usuario, el rol será propiedad del usuario que ejecute CREATE ROLE.  
  
## <a name="remarks"></a>Comentarios  
 Los roles son elementos protegibles de nivel de base de datos. Después de crear un rol, configure los permisos de nivel de base de datos del rol con GRANT, DENY y REVOKE. Para agregar miembros a un rol de base de datos, use [ALTER ROLE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-role-transact-sql.md). Para obtener más información, consulte [Roles de nivel de base de datos](../../relational-databases/security/authentication-access/database-level-roles.md).  
  
 Los roles de base de datos se pueden ver en las vistas de catálogos sys.database_role_members y sys.database_principals.  
  
 Para más información acerca de cómo diseñar un sistema de permisos, consulte [Getting Started with Database Engine Permissions](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).  
  
> [!CAUTION]  
>  [!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
## <a name="permissions"></a>Permissions  
 Requiere **CREATE ROLE** permiso en la base de datos o la pertenencia a la **db_securityadmin** rol fijo de base de datos. Cuando se usa el **autorización** opción, también se requieren los permisos siguientes:  
  
-   Asignar la propiedad de un rol a otro usuario requiere el permiso IMPERSONATE para ese usuario.  
  
-   Asignar la propiedad de un rol a otro rol requiere la pertenencia al rol receptor o el permiso ALTER para ese rol.  
  
-   Asignar la propiedad de un rol a un rol de aplicación requiere el permiso ALTER para el rol de aplicación.  
  
## <a name="examples"></a>Ejemplos  
Todos los ejemplos siguientes utiliza la base de datos de AdventureWorks.   

### <a name="a-creating-a-database-role-that-is-owned-by-a-database-user"></a>A. Crear un rol de base de datos propiedad de un usuario de la base de datos  
 En el siguiente ejemplo se crea el rol de base de datos `buyers` que es propiedad del usuario `BenMiller`.  
  
```  
CREATE ROLE buyers AUTHORIZATION BenMiller;  
GO  
```  
  
### <a name="b-creating-a-database-role-that-is-owned-by-a-fixed-database-role"></a>B. Crear un rol de base de datos que es propiedad de un rol fijo de base de datos  
 En el siguiente ejemplo se crea el rol de base de datos `auditors` que es propiedad del rol fijo de base de datos `db_securityadmin`.  
  
```  
CREATE ROLE auditors AUTHORIZATION db_securityadmin;  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [Entidades de seguridad &#40;motor de base de datos&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [ALTER ROLE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-role-transact-sql.md)   
 [ELIMINAR rol &#40; Transact-SQL &#41;](../../t-sql/statements/drop-role-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sys.database_role_members &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [Introducción a los permisos de los motores de bases de datos](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)  
  
  



