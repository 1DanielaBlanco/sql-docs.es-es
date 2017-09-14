---
title: '@@NESTLEVEL (Transact-SQL) | Documentos de Microsoft'
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@NESTLEVEL'
- '@@NESTLEVEL_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@NESTLEVEL function'
- nesting stored procedures
- stored procedure nesting levels [SQL Server]
ms.assetid: 8c0b2134-8616-44f6-addc-6583c432fb62
caps.latest.revision: 40
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ce6980ba008189a1588dc87e955a26125dc6a30d
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="nestlevel-transact-sql"></a>@@NESTLEVEL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Devuelve el nivel de anidamiento de la ejecución del procedimiento almacenado actual (inicialmente 0) en el servidor local.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
@@NESTLEVEL  
```  
  
## <a name="return-types"></a>Tipos devueltos  
 **int**  
  
## <a name="remarks"></a>Comentarios  
 Cada vez que un procedimiento almacenado llama a otro procedimiento almacenado o ejecuta un código administrado haciendo referencia a una rutina Common Language Runtime (CLR), un tipo o un agregado, se incrementa el nivel de anidamiento. Cuando se sobrepasa el máximo de 32, se termina la transacción.  
  
 Cuando @@NESTLEVEL se ejecuta en un [!INCLUDE[tsql](../../includes/tsql-md.md)] cadena, el valor devuelto es 1 + actual nivel de anidamiento. Cuando @@NESTLEVEL se ejecuta dinámicamente mediante el uso de sp_executesql el valor devuelto es 2 + el nivel de anidamiento actual.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-using-nestlevel-in-a-procedure"></a>A. Usar@NESTLEVEL en un procedimiento  
 En el ejemplo siguiente se crean dos procedimientos: uno que llama al otro y uno que muestra el valor `@@NESTLEVEL` de cada uno.  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID (N'usp_OuterProc', N'P')IS NOT NULL  
    DROP PROCEDURE usp_OuterProc;  
GO  
IF OBJECT_ID (N'usp_InnerProc', N'P')IS NOT NULL  
    DROP PROCEDURE usp_InnerProc;  
GO  
CREATE PROCEDURE usp_InnerProc AS   
    SELECT @@NESTLEVEL AS 'Inner Level';  
GO  
CREATE PROCEDURE usp_OuterProc AS   
    SELECT @@NESTLEVEL AS 'Outer Level';  
    EXEC usp_InnerProc;  
GO  
EXECUTE usp_OuterProc;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Outer Level`  
  
 `-----------`  
  
 `1`  
  
 `Inner Level`  
  
 `-----------`  
  
 `2`  
  
### <a name="b-calling-nestlevel"></a>B. Llamar a @@NESTLEVEL  
 El ejemplo siguiente muestra la diferencia en los valores devueltos por `SELECT`, `EXEC` y `sp`_`executesql` cuando cada uno de ellos llama a `@@NESTLEVEL`.  
  
```  
CREATE PROC usp_NestLevelValues AS  
    SELECT @@NESTLEVEL AS 'Current Nest Level';  
EXEC ('SELECT @@NESTLEVEL AS OneGreater');   
EXEC sp_executesql N'SELECT @@NESTLEVEL as TwoGreater' ;  
GO  
EXEC usp_NestLevelValues;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Current Nest Level`  
  
 `------------------`  
  
 `1`  
  
 `(1 row(s) affected)`  
  
 `OneGreater`  
  
 `-----------`  
  
 `2`  
  
 `(1 row(s) affected)`  
  
 `TwoGreater`  
  
 `-----------`  
  
 `3`  
  
 `(1 row(s) affected)`  
  
## <a name="see-also"></a>Vea también  
 [Funciones de configuración &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [Crear un procedimiento almacenado](../../relational-databases/stored-procedures/create-a-stored-procedure.md)   
 [@@TRANCOUNT &#40;Transact-SQL&#41;](../../t-sql/functions/trancount-transact-sql.md)  
  
  