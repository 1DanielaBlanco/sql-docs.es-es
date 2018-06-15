---
title: sp_addapprole (Transact-SQL) | Documentos de Microsoft
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
- sp_addapprole_TSQL
- sp_addapprole
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addapprole
ms.assetid: 24200295-9a54-4cab-9922-fb2e88632721
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 3de15b3d1f02f3acf8dd5809dce7ec01ad74e65f
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33239085"
---
# <a name="spaddapprole-transact-sql"></a>sp_addapprole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Agrega un rol de aplicación a la base de datos actual.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Use [CREATE APPLICATION ROLE](../../t-sql/statements/create-application-role-transact-sql.md) en su lugar.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_addapprole [ @rolename = ] 'role' , [ @password = ] 'password'  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@rolename =** ] **'***rol***'**  
 Es el nombre del nuevo rol de aplicación. *rol* es **sysname**, no tiene ningún valor predeterminado. *función* debe ser un identificador válido y no puede existir en la base de datos actual.  
  
 Los nombres de roles de aplicación pueden contener entre 1 y 128 caracteres, y pueden incluir letras, símbolos y números. Los nombres de función no pueden contener una barra diagonal inversa (\\) ni ser NULL ni una cadena vacía (").  
  
 [  **@password =** ] **'***contraseña***'**  
 Es la contraseña necesaria para activar el rol de aplicación. *contraseña* es **sysname**, no tiene ningún valor predeterminado. *contraseña* no puede ser NULL.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 0 (correcto) o 1 (error)  
  
## <a name="remarks"></a>Comentarios  
 En versiones anteriores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], los usuarios (y roles) no se distinguían completamente de los esquemas. A partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], los esquemas son totalmente distintos de los roles. Esta nueva arquitectura se refleja en el comportamiento de CREATE APPLICATION ROLE. Esta instrucción sustituye a **sp_addapprole**.  
  
 Para mantener la compatibilidad con versiones anteriores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], **sp_addapprole** hará lo siguiente:  
  
-   Si no existe un esquema con el mismo nombre que el rol de aplicación, se creará dicho esquema. El nuevo esquema será propiedad del rol de aplicación y será el esquema predeterminado del rol de aplicación.  
  
-   Si ya existe un esquema con el mismo nombre que el rol de aplicación, el procedimiento generará un error.  
  
-   No se comprueba la complejidad de la contraseña **sp_addapprole**. La complejidad de la contraseña la comprueba CREATE APPLICATION ROLE.  
  
 El parámetro *contraseña* se almacena como un hash unidireccional.  
  
 El **sp_addapprole** procedimiento almacenado no puede ejecutarse desde una transacción definida por el usuario.  
  
> [!IMPORTANT]  
>  Microsoft ODBC **cifrar** opción no es compatible con **SqlClient**. Cuando pueda, pida a los usuarios que escriban las credenciales del rol de aplicación en tiempo de ejecución. No guarde las credenciales en un archivo. Si debe conservar las credenciales, cífrelas con las funciones CryptoAPI.  
  
## <a name="permissions"></a>Permissions  
 Requiere el permiso ALTER ANY APPLICATION ROLE en la base de datos. Si aún no existe un esquema con el mismo nombre de esquema y propietario que el nuevo rol, también se requiere el permiso CREATE SCHEMA en la base de datos.  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se agrega el nuevo rol de aplicación `SalesApp` con la contraseña `x97898jLJfcooFUYLKm387gf3` a la base de datos actual.  
  
```  
EXEC sp_addapprole 'SalesApp', 'x97898jLJfcooFUYLKm387gf3' ;  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-application-role-transact-sql.md)  
  
  
