---
title: ERROR_NUMBER (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ERROR_NUMBER_TSQL
- ERROR_NUMBER
dev_langs:
- TSQL
helpviewer_keywords:
- errors [SQL Server], line number
- messages [SQL Server], numbers
- TRY...CATCH [SQL Server]
- ERROR_NUMBER function
- CATCH block
ms.assetid: 1de85fff-1ca2-4b31-841b-926e571cb150
caps.latest.revision: 50
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: c02f7639d021cad12fd8a6c144213e7cc71861c5
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39455219"
---
# <a name="errornumber-transact-sql"></a>ERROR_NUMBER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Esta función devuelve el número del error que ha provocado la ejecución del bloque CATCH de una construcción TRY…CATCH.  

 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
ERROR_NUMBER ( )  
```  
  
## <a name="return-types"></a>Tipos devueltos  
 **int**  
  
## <a name="return-value"></a>Valor devuelto  
Si se llama en un bloque CATCH, `ERROR_NUMBER` devuelve el número del error que ha provocado la ejecución del bloque CATCH.  

`ERROR_NUMBER` devuelve NULL si se llama desde fuera del ámbito de un bloque CATCH.  
  
## <a name="remarks"></a>Notas  
`ERROR_NUMBER` admite llamadas en cualquier lugar del ámbito de un bloque CATCH.  
  
`ERROR_NUMBER` devuelve un número de error relevante, con independencia de cuántas veces se ejecute o de dónde se ejecute dentro del ámbito del bloque `CATCH`. Esto contrasta con funciones como @@ERROR, que solo devuelve un número de error en la instrucción inmediatamente posterior a la que produjo el error.  

En un bloque `CATCH` anidado, `ERROR_NUMBER` devuelve el número de error específico del ámbito del bloque `CATCH` al que hace referencia ese bloque `CATCH`. Por ejemplo, el bloque `CATCH` de una construcción TRY...CATCH externa podría tener una construcción `TRY...CATCH` interna. Dentro de ese bloque interno `CATCH`, `ERROR_NUMBER` devuelve el número del error que invocó el bloque `CATCH` interno. Si `ERROR_NUMBER` se ejecuta en el bloque `CATCH` externo, devuelve el número del error que invocó ese bloque `CATCH` externo.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-using-errornumber-in-a-catch-block"></a>A. Usar ERROR_NUMBER en un bloque CATCH  
En este ejemplo se muestra una instrucción `SELECT` que genera un error de división por cero. El bloque `CATCH` devuelve el número de error.  
  
```  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_NUMBER() AS ErrorNumber;  
END CATCH;  
GO  

-----------

(0 row(s) affected)

ErrorNumber
-----------
8134

(1 row(s) affected)

```  
  
### <a name="b-using-errornumber-in-a-catch-block-with-other-error-handling-tools"></a>B. Usar ERROR_NUMBER en un bloque CATCH con otras herramientas de control de errores  
En este ejemplo se muestra una instrucción `SELECT` que genera un error de división por cero. Junto con el número de error, el bloque `CATCH` devuelve información sobre ese error.  

```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber,  
        ERROR_SEVERITY() AS ErrorSeverity,  
        ERROR_STATE() AS ErrorState,  
        ERROR_PROCEDURE() AS ErrorProcedure,  
        ERROR_LINE() AS ErrorLine,  
        ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  

-----------

(0 row(s) affected)

ErrorNumber ErrorSeverity ErrorState  ErrorProcedure   ErrorLine  ErrorMessage
----------- ------------- ----------- ---------------  ---------- ----------------------------------
8134        16            1           NULL             4          Divide by zero error encountered.

(1 row(s) affected)

```  
  
## <a name="see-also"></a>Ver también  
 [sys.messages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)   
 [TRY...CATCH &#40;Transact-SQL&#41;](../../t-sql/language-elements/try-catch-transact-sql.md)   
 [ERROR_LINE &#40;Transact-SQL&#41;](../../t-sql/functions/error-line-transact-sql.md)   
 [ERROR_MESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/error-message-transact-sql.md)   
 [ERROR_PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/functions/error-procedure-transact-sql.md)   
 [ERROR_SEVERITY &#40;Transact-SQL&#41;](../../t-sql/functions/error-severity-transact-sql.md)   
 [ERROR_STATE &#40;Transact-SQL&#41;](../../t-sql/functions/error-state-transact-sql.md)   
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [@@ERROR &#40;Transact-SQL&#41;](../../t-sql/functions/error-transact-sql.md)  
  
  

