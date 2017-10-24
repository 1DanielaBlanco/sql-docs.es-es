---
title: ALTER USER (Transact-SQL) | Documentos de Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 05/05/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_USER_TSQL
- ALTER USER
dev_langs:
- TSQL
helpviewer_keywords:
- modifying database users
- ALTER USER statement
- renaming databases
- schemas [SQL Server], default
- database user names [SQL Server]
- names [SQL Server], database users
- default schemas
- modifying default schemas
ms.assetid: 344fc6ce-a008-47c8-a02e-47fae66cc590
caps.latest.revision: 75
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 62651475119ba147e6823ba9e25b2cde67678dcc
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="alter-user-transact-sql"></a>ALTER USER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Cambia el nombre de un usuario de base de datos o cambia su esquema predeterminado.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
-- Syntax for SQL Server  
  
ALTER USER userName    
     WITH <set_item> [ ,...n ]  
[;]  
  
<set_item> ::=   
      NAME = newUserName   
    | DEFAULT_SCHEMA = { schemaName | NULL }  
    | LOGIN = loginName  
    | PASSWORD = 'password' [ OLD_PASSWORD = 'oldpassword' ]  
    | DEFAULT_LANGUAGE = { NONE | <lcid> | <language name> | <language alias> }  
    | ALLOW_ENCRYPTED_VALUE_MODIFICATIONS = [ ON | OFF ]  
```  
  
```  
-- Syntax for Azure SQL Database  
  
ALTER USER userName    
     WITH <set_item> [ ,...n ]  
  
<set_item> ::=   
      NAME = newUserName   
    | DEFAULT_SCHEMA = schemaName  
    | LOGIN = loginName  
    | ALLOW_ENCRYPTED_VALUE_MODIFICATIONS = [ ON | OFF ]   
[;]  
  
-- Azure SQL Database Update Syntax  
ALTER USER userName    
     WITH <set_item> [ ,...n ]  
[;]  
  
<set_item> ::=   
      NAME = newUserName   
    | DEFAULT_SCHEMA = { schemaName | NULL }  
    | LOGIN = loginName  
    | PASSWORD = 'password' [ OLD_PASSWORD = 'oldpassword' ]  
    | ALLOW_ENCRYPTED_VALUE_MODIFICATIONS = [ ON | OFF ]   
  
-- SQL Database syntax when connected to a federation member  
ALTER USER userName  
     WITH <set_item> [ ,… n ]   
[;]  
  
<set_item> ::=   
     NAME = newUserName  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
ALTER USER userName    
     WITH <set_item> [ ,...n ]  
  
<set_item> ::=   
     NAME =newUserName   
     | LOGIN =loginName  
     | DEFAULT_SCHEMA = schema_name  
[;]  
```  
  
## <a name="arguments"></a>Argumentos  
 *nombre de usuario*  
 Especifica el nombre por el que se identifica al usuario en esta base de datos.  
  
 Inicio de sesión  **=**  *loginName*  
 Reasigna un usuario a otro inicio de sesión cambiando el identificador de seguridad (SID) del usuario para que coincida con el SID de inicio de sesión.  
  
 Si la instrucción ALTER USER es la única instrucción en un lote SQL, SQL Database de Microsoft Azure admite la cláusula WITH LOGIN. Si la instrucción ALTER USER no es la única instrucción en un lote SQL ni se ejecuta en SQL dinámico, la cláusula WITH LOGIN no se admite.  
  
 NOMBRE  **=**  *newUserName*  
 Especifica el nuevo nombre de este usuario. *newUserName* no debe existir en la base de datos actual.  
  
 DEFAULT_SCHEMA  **=**  { *schemaName* | NULL}  
 Especifica el primer esquema donde buscará el servidor cuando resuelva los nombres de objetos de este usuario. El establecimiento del esquema predeterminado en NULL quita un esquema predeterminado de un grupo de Windows.   La opción NULL no se puede utilizar con un usuario de Windows.  
  
 CONTRASEÑA  **=**  '*contraseña*'  
 **Se aplica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  
  
 Especifica la contraseña del usuario que se está cambiando. En las contraseñas se distingue entre mayúsculas y minúsculas.  
  
> [!NOTE]  
>  Esta opción solo está disponible para los usuarios contenidos. Vea [las bases de datos](../../relational-databases/databases/contained-databases.md) y [sp_migrate_user_to_contained &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-migrate-user-to-contained-transact-sql.md) para obtener más información.  
  
 Contraseña_anterior  **=**  *'oldpassword'*  
 **Se aplica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  
  
 La contraseña de usuario actual que se reemplazará por '*contraseña*'. En las contraseñas se distingue entre mayúsculas y minúsculas. *Contraseña_anterior* es necesario para cambiar una contraseña, a menos que tenga **ALTER ANY USER** permiso. Requerir *contraseña_anterior* impide que los usuarios con **SUPLANTACIÓN** permiso de cambiar la contraseña.  
  
> [!NOTE]  
>  Esta opción solo está disponible para los usuarios contenidos.  
  
 DEFAULT_LANGUAGE  **=**  *{NONE | \<lcid > | \<nombreidioma > | \<aliasidioma >}*  
 **Se aplica a**: desde [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] hasta [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Especifica el idioma predeterminado que debe asignarse al usuario. Si esta opción se establece en NONE, el idioma predeterminado se establece en el de la base de datos. Si el idioma predeterminado de la base de datos se cambia más tarde, el idioma predeterminado del usuario no se modificará. *DEFAULT_LANGUAGE* puede ser el identificador local (lcid), el nombre del idioma o alias de idioma.  
  
> [!NOTE]  
>  Esta opción solo se puede especificar en una base de datos independiente y solo para los usuarios independientes.  
  
 ALLOW_ENCRYPTED_VALUE_MODIFICATIONS = [ON | **OFF** ]]  
 **Se aplica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Suprime las comprobaciones de metadatos criptográficos en el servidor en operaciones de copia masiva. Esto permite al usuario copiar los datos de forma masiva entre tablas o bases de datos, sin descifrar los datos. El valor predeterminado es OFF.  
  
> [!WARNING]  
>  Si esta opción no se utiliza adecuadamente, pueden dañarse los datos. Para obtener más información, consulte [migrar información confidencial protegida mediante Always Encrypted](../../relational-databases/security/encryption/migrate-sensitive-data-protected-by-always-encrypted.md).  
  
## <a name="remarks"></a>Comentarios  
 El esquema predeterminado será el primer esquema donde buscará el servidor cuando resuelva los nombres de objetos de este usuario de base de datos. A menos que se especifique lo contrario, el esquema predeterminado será el propietario de los objetos creados por este usuario de base de datos.  
  
 Si el usuario tiene un esquema predeterminado, se utilizará dicho esquema. Si el usuario no tiene un esquema predeterminado pero es miembro de un grupo con un esquema predeterminado, se utilizará el esquema predeterminado del grupo. Si el usuario no tiene un esquema predeterminado y es miembro de varios grupos, el esquema predeterminado para el usuario será el del grupo de Windows con el principal_id mínimo y un esquema predeterminado establecido explícitamente. Si no se puede determinar ningún esquema predeterminado para un usuario, el **dbo** se utilizará el esquema.  
  
 DEFAULT_SCHEMA puede establecerse en un esquema que no existe actualmente en la base de datos. Por tanto, puede asignar un DEFAULT_SCHEMA a un usuario antes de crear el esquema.  
  
 No se puede especificar DEFAULT_SCHEMA para un usuario asignado a un certificado o una clave asimétrica.  
  
> [!IMPORTANT]  
>  El valor de DEFAULT_SCHEMA se omite si el usuario es un miembro de la **sysadmin** rol fijo de servidor. Todos los miembros de la **sysadmin** rol fijo de servidor tiene un esquema predeterminado de `dbo`.  
  
 Solo puede cambiar el nombre de un usuario que está asignado a un grupo o inicio de sesión de Windows cuando el SID del nuevo nombre de usuario coincide con el SID registrado en la base de datos. Esta comprobación ayuda a evitar la suplantación de inicios de sesión de Windows en la base de datos.  
  
 La cláusula WITH LOGIN habilita la reasignación de un usuario a un inicio de sesión diferente. Los usuarios sin inicio de sesión, los usuarios asignados a un certificado y los usuarios asignados a una clave asimétrica no se pueden reasignar con esta cláusula. Solo se pueden reasignar usuarios de SQL y usuarios (o grupos) de Windows. La cláusula WITH LOGIN no se puede utilizar para cambiar el tipo de usuario, como cambiar una cuenta de Windows a un inicio de sesión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 El nombre del usuario se cambiará automáticamente por el nombre de inicio de sesión si se cumplen las condiciones siguientes.  
  
-   El usuario es un usuario de Windows.  
  
-   El nombre es un nombre de Windows (contiene una barra diagonal inversa).  
  
-   No se ha especificado ningún nombre nuevo.  
  
-   El nombre actual difiere del nombre de inicio de sesión.  
  
 En caso contrario, no se cambiará el nombre del usuario a menos que el autor de las llamadas invoque también la cláusula NAME.  
  
El nombre de un usuario asignado a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inicio de sesión, un certificado o una clave asimétrica no puede contener el carácter de barra diagonal inversa (\\).  
  
> [!CAUTION]  
>  [!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
## <a name="security"></a>Seguridad  
  
> [!NOTE]  
>  Un usuario que tenga **ALTER ANY USER** permiso puede cambiar el esquema predeterminado de cualquier usuario. Un usuario que tenga un esquema modificado podría seleccionar datos de la tabla incorrecta o ejecutar código del esquema incorrecto sin saberlo.  
  
### <a name="permissions"></a>Permissions  
 Para cambiar el nombre de un usuario requiere la **ALTER ANY USER** permiso.  
  
 Para cambiar el inicio de sesión de destino de un usuario requiere la **CONTROL** permiso en la base de datos.  
  
 Para cambiar el nombre de usuario de un usuario que tenga **CONTROL** permiso en la base de datos requiere el **CONTROL** permiso en la base de datos.  
  
 Para cambiar el esquema predeterminado o el idioma requiere **ALTER** permiso para el usuario. Los usuarios pueden cambiar el idioma y el esquema predeterminados.  
  
## <a name="examples"></a>Ejemplos  

Todos los ejemplos se ejecutan en una base de datos de usuario.  

### <a name="a-changing-the-name-of-a-database-user"></a>A. Cambiar el nombre de usuario de una base de datos  
 En el ejemplo siguiente se cambia el nombre del usuario de la base de datos `Mary5` a `Mary51`.  
  
```  
ALTER USER Mary5 WITH NAME = Mary51;  
GO  
```  
  
### <a name="b-changing-the-default-schema-of-a-user"></a>B. Cambiar el esquema predeterminado de un usuario  
 En el ejemplo siguiente se cambia el esquema predeterminado del usuario de `Mary51` a `Purchasing`.  
  
```  
ALTER USER Mary51 WITH DEFAULT_SCHEMA = Purchasing;  
GO  
```  
  
### <a name="c-changing-several-options-at-once"></a>C. Cambiar varias opciones a la vez  
 En el siguiente ejemplo se cambian varias opciones para un usuario de base de datos independiente en una instrucción.  
  
**Se aplica a**: desde [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] hasta [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
ALTER USER Philip   
WITH  NAME = Philipe   
    , DEFAULT_SCHEMA = Development   
    , PASSWORD = 'W1r77TT98%ab@#’ OLD_PASSWORD = 'New Devel0per'   
    , DEFAULT_LANGUAGE  = French ;  
GO  
```  
  
  
## <a name="see-also"></a>Vea también  
 [CREATE USER &#40;Transact-SQL&#41;](../../t-sql/statements/create-user-transact-sql.md)   
 [Eliminar usuario &#40; Transact-SQL &#41;](../../t-sql/statements/drop-user-transact-sql.md)   
 [Bases de datos independientes](../../relational-databases/databases/contained-databases.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_migrate_user_to_contained &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-migrate-user-to-contained-transact-sql.md)  
  
  



