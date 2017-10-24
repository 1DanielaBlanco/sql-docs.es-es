---
title: ERROR_SEVERITY (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ERROR_SEVERITY_TSQL
- ERROR_SEVERITY
dev_langs:
- TSQL
helpviewer_keywords:
- errors [SQL Server], severity
- messages [SQL Server], severity
- TRY...CATCH [SQL Server]
- CATCH block
- ERROR_SEVERITY function
ms.assetid: 50228f2f-6949-4d2e-8e43-fad11bf973ab
caps.latest.revision: 41
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: 5c3cd713bcbb239c037ff0a43083058de117cb9b
ms.contentlocale: es-es
ms.lasthandoff: 10/17/2017

---
# <a name="errorseverity-transact-sql"></a>ERROR_SEVERITY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Devuelve la gravedad del error que provocó la ejecución del bloque CATCH de una construcción TRY…CATCH.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
ERROR_SEVERITY ( )  
```  
  
## <a name="return-types"></a>Tipos devueltos  
 **int**  
  
## <a name="return-value"></a>Valor devuelto  
 Cuando se llama en un bloque CATCH, devuelve la gravedad del mensaje de error que provocó la ejecución del bloque CATCH.  
  
 Devuelve NULL si se le llama desde fuera del ámbito del bloque CATCH.  
  
## <a name="remarks"></a>Comentarios  
 ERROR_SEVERITY se puede llamar desde cualquier lugar dentro del ámbito de un bloque CATCH.  
  
 ERROR_SEVERITY devuelve la gravedad del error independientemente de cuántas veces se ejecute o de si se ejecuta dentro del ámbito del bloque CATCH. Esto difiere de las funciones como @@ERROR, que sólo devuelve el número de error en la instrucción inmediatamente posterior a la que se produzca un error, o en la primera instrucción de un bloque CATCH.  
  
 En los bloques CATCH anidados, ERROR_SEVERITY devuelve la gravedad del error específica del ámbito del bloque CATCH en el que se hace referencia al mismo. Por ejemplo, el bloque CATCH de una construcción TRY...CATCH externa podría tener una construcción TRY...CATCH anidada. Dentro del bloque CATCH anidado, ERROR_SEVERITY devuelve la gravedad del error que invocó el bloque CATCH anidado. Si ERROR_SEVERITY se ejecuta en el bloque CATCH externo, devuelve la gravedad del error que invocó ese bloque CATCH.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-using-errorseverity-in-a-catch-block"></a>A. Utilizar ERROR_SEVERITY en un bloque CATCH  
 El ejemplo siguiente muestra un `SELECT` instrucción que genera un error de división por cero. Se devuelve la gravedad del error.  
  
```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_SEVERITY() AS ErrorSeverity;  
END CATCH;  
GO  
```  
  
### <a name="b-using-errorseverity-in-a-catch-block-with-other-error-handling-tools"></a>B. Utilizar ERROR_SEVERITY en un bloque CATCH con otras herramientas de control de errores  
 El siguiente ejemplo muestra una instrucción `SELECT` que genera un error de división por cero. Además de la gravedad, se devuelve otra información relacionada con el error.  
  
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
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Ejemplos: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] y[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-errorseverity-in-a-catch-block-with-other-error-handling-tools"></a>C. Utilizar ERROR_SEVERITY en un bloque CATCH con otras herramientas de control de errores  
 El siguiente ejemplo muestra una instrucción `SELECT` que genera un error de división por cero. Además de la gravedad, se devuelve otra información relacionada con el error.  
  
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
        ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [sys.messages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)   
 [TRY...CATCH &#40;Transact-SQL&#41;](../../t-sql/language-elements/try-catch-transact-sql.md)   
 [ERROR_LINE &#40;Transact-SQL&#41;](../../t-sql/functions/error-line-transact-sql.md)   
 [ERROR_MESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/error-message-transact-sql.md)   
 [ERROR_NUMBER &#40;Transact-SQL&#41;](../../t-sql/functions/error-number-transact-sql.md)   
 [ERROR_PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/functions/error-procedure-transact-sql.md)   
 [ERROR_STATE &#40; Transact-SQL &#41;](../../t-sql/functions/error-state-transact-sql.md)   
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [@@ERROR &#40;Transact-SQL&#41;](../../t-sql/functions/error-transact-sql.md)  
  
  


