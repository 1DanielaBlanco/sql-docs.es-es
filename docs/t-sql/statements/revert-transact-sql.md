---
title: REVERTIR (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- REVERT_TSQL
- REVERT
dev_langs:
- TSQL
helpviewer_keywords:
- REVERT statement
- context switching [SQL Server], reverting
- reverting execution context
- REVERT WITH COOKIE statement
- execution context [SQL Server]
- COOKIE clause
ms.assetid: 4688b17a-dfd1-4f03-8db4-273a401f879f
caps.latest.revision: 28
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: 033442da3e10fd834963df30ea071a220464de6f
ms.contentlocale: es-es
ms.lasthandoff: 10/24/2017

---
# <a name="revert-transact-sql"></a>REVERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Vuelve a cambiar el contexto de ejecución al autor de llamada de la última instrucción EXECUTE AS.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
REVERT  
    [ WITH COOKIE = @varbinary_variable ]  
```  
  
## <a name="arguments"></a>Argumentos  
 WITH COOKIE = @*varbinary_variable*  
 Especifica la cookie que se creó en su correspondiente [EXECUTE AS](../../t-sql/statements/execute-as-transact-sql.md) instrucción independiente. *@varbinary_variable*es **varbinary(100)**.  
  
## <a name="remarks"></a>Comentarios  
 REVERT se puede especificar en un módulo, por ejemplo, en un procedimiento almacenado o una función definida por el usuario, o como una instrucción independiente. Cuando se especifica en un módulo, REVERT solo se aplica a las instrucciones EXECUTE AS definidas en el módulo. Por ejemplo, el siguiente procedimiento almacenado emite una instrucción `EXECUTE AS` seguida de una instrucción `REVERT`.  
  
```  
CREATE PROCEDURE dbo.usp_myproc   
  WITH EXECUTE AS CALLER  
AS   
    SELECT SUSER_NAME(), USER_NAME();  
    EXECUTE AS USER = 'guest';  
    SELECT SUSER_NAME(), USER_NAME();  
    REVERT;  
    SELECT SUSER_NAME(), USER_NAME();  
GO  
```  
  
 Suponga que, como se muestra en el siguiente ejemplo, en la sesión en la que se ejecuta el procedimiento almacenado, el contexto de ejecución de la sesión se cambia explícitamente a `login1`.  
  
```  
  -- Sets the execution context of the session to 'login1'.  
EXECUTE AS LOGIN = 'login1';  
GO  
EXECUTE dbo.usp_myproc;   
```  
  
 El `REVERT` instrucción que se define dentro de `usp_myproc` cambia el contexto de ejecución establecido dentro del módulo, pero no afecta al contexto de ejecución establecido fuera del módulo. Es decir, el contexto de ejecución de la sesión permanece establecido en `login1`.  
  
 Cuando se especifica como una instrucción independiente, REVERT se aplica a las instrucciones EXECUTE AS definidas en un lote o sesión. REVERT no tiene efecto si la instrucción EXECUTE AS correspondiente contiene la cláusula WITH NO REVERT. En este caso, el contexto de ejecución permanece efectivo hasta que se quita la sesión.  
  
## <a name="using-revert-with-cookie"></a>Usar REVERT WITH COOKIE  
 La ejecución como instrucción que se usa para establecer el contexto de ejecución de una sesión puede incluir la cláusula opcional WITH NO REVERT COOKIE = @*varbinary_variabl*e. Cuando se ejecuta esta instrucción, la [!INCLUDE[ssDE](../../includes/ssde-md.md)] pasa la cookie a @*varbinary_variabl*e. El contexto de ejecución establecido esa instrucción solamente puede volver al contexto anterior si la llamada a REVERT WITH COOKIE = @*varbinary_variable* instrucción contiene el valor correcto  *@varbinary_variable*  valor.  
  
 Este mecanismo es útil en un entorno donde se utiliza la agrupación de conexiones. La agrupación de conexiones es el mantenimiento de un grupo de base de datos que reutilizan las aplicaciones entre varios usuarios finales. Puesto que el valor pasado a  *@varbinary_variable*  solo lo conoce el llamador de la ejecución como instrucción (en este caso, la aplicación), el llamador puede garantizar que no se puede cambiar el contexto de ejecución que establece que el usuario final que invoca la aplicación. Después de volver el contexto de ejecución, la aplicación puede cambiar el contexto a otra entidad de seguridad.  
  
## <a name="permissions"></a>Permissions  
 No se requieren permisos.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-using-execute-as-and-revert-to-switch-context"></a>A. Usar EXECUTE AS y REVERT para cambiar el contexto  
 En el ejemplo siguiente se crea una pila de contextos de ejecución mediante el uso de varias entidades de seguridad. La instrucción REVERT se utiliza a continuación para restablecer el contexto de ejecución al llamador anterior. La instrucción REVERT se ejecuta varias veces subiendo la pila hasta que el contexto de ejecución se establece en el llamador original.  
  
```  
USE AdventureWorks2012;  
GO  
-- Create two temporary principals.  
CREATE LOGIN login1 WITH PASSWORD = 'J345#$)thb';  
CREATE LOGIN login2 WITH PASSWORD = 'Uor80$23b';  
GO  
CREATE USER user1 FOR LOGIN login1;  
CREATE USER user2 FOR LOGIN login2;  
GO  
-- Give IMPERSONATE permissions on user2 to user1  
-- so that user1 can successfully set the execution context to user2.  
GRANT IMPERSONATE ON USER:: user2 TO user1;  
GO  
-- Display current execution context.  
SELECT SUSER_NAME(), USER_NAME();  
-- Set the execution context to login1.   
EXECUTE AS LOGIN = 'login1';  
-- Verify that the execution context is now login1.  
SELECT SUSER_NAME(), USER_NAME();  
-- Login1 sets the execution context to login2.  
EXECUTE AS USER = 'user2';  
-- Display current execution context.  
SELECT SUSER_NAME(), USER_NAME();  
-- The execution context stack now has three principals: the originating caller, login1, and login2.  
-- The following REVERT statements will reset the execution context to the previous context.  
REVERT;  
-- Display the current execution context.  
SELECT SUSER_NAME(), USER_NAME();  
REVERT;  
-- Display the current execution context.  
SELECT SUSER_NAME(), USER_NAME();  
  
-- Remove the temporary principals.  
DROP LOGIN login1;  
DROP LOGIN login2;  
DROP USER user1;  
DROP USER user2;  
GO  
```  
  
### <a name="b-using-the-with-cookie-clause"></a>B. Usar la cláusula WITH COOKIE  
 En el ejemplo siguiente se establece el contexto de ejecución de una sesión a un usuario especificado y especifica el WITH NO REVERT COOKIE = @*varbinary_variabl*cláusula e. La instrucción `REVERT` debe especificar el valor pasado a la variable `@cookie` en la instrucción `EXECUTE AS` para volver correctamente el contexto al llamador. Para ejecutar este ejemplo, deben existir el inicio de sesión `login1` y el usuario `user1` creados en el ejemplo A.  
  
```  
DECLARE @cookie varbinary(100);  
EXECUTE AS USER = 'user1' WITH COOKIE INTO @cookie;  
-- Store the cookie somewhere safe in your application.  
-- Verify the context switch.  
SELECT SUSER_NAME(), USER_NAME();  
--Display the cookie value.  
SELECT @cookie;  
GO  
-- Use the cookie in the REVERT statement.  
DECLARE @cookie varbinary(100);  
-- Set the cookie value to the one from the SELECT @cookie statement.  
SET @cookie = <value from the SELECT @cookie statement>;  
REVERT WITH COOKIE = @cookie;  
-- Verify the context switch reverted.  
SELECT SUSER_NAME(), USER_NAME();  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [EJECUTAR AS &#40; Transact-SQL &#41;](../../t-sql/statements/execute-as-transact-sql.md)   
 [EXECUTE AS &#40;cláusula de Transact-SQL&#41;](../../t-sql/statements/execute-as-clause-transact-sql.md)   
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [SUSER_NAME &#40; Transact-SQL &#41;](../../t-sql/functions/suser-name-transact-sql.md)   
 [User_name &#40; Transact-SQL &#41;](../../t-sql/functions/user-name-transact-sql.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [CREATE USER &#40;Transact-SQL&#41;](../../t-sql/statements/create-user-transact-sql.md)  
  
  

