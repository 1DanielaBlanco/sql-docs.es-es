---
title: IF...ELSE (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/11/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IF_TSQL
- IF
dev_langs:
- TSQL
helpviewer_keywords:
- IF...ELSE keyword
- ELSE (IF...ELSE) keyword
- ELSE keyword
- IF keyword
ms.assetid: 676c881f-dee1-417a-bc51-55da62398e81
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 34a14f617d5eed0b56d6ffb44134f03efa96d2c2
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="ifelse-transact-sql"></a>IF...ELSE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Impone condiciones en la ejecución de una instrucción de [!INCLUDE[tsql](../../includes/tsql-md.md)]. La instrucción [!INCLUDE[tsql](../../includes/tsql-md.md)] que sigue a una palabra clave IF y a su condición se ejecuta si la condición se cumple: la expresión booleana devuelve TRUE. La palabra clave opcional ELSE introduce otra instrucción [!INCLUDE[tsql](../../includes/tsql-md.md)] que se ejecuta cuando la condición IF no se cumple: la expresión booleana devuelve FALSE.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IF Boolean_expression   
     { sql_statement | statement_block }   
[ ELSE   
     { sql_statement | statement_block } ]   
```  
  
## <a name="arguments"></a>Argumentos  
 *Boolean_expression*  
 Es una expresión que devuelve TRUE o FALSE. Si la expresión booleana contiene una instrucción SELECT, la instrucción SELECT debe ir entre paréntesis.  
  
 { *sql_statement*| *statement_block* }  
 Es cualquier [!INCLUDE[tsql](../../includes/tsql-md.md)] instrucciones o agrupación tal como se define mediante el uso de un bloque de instrucciones. A menos que se utilice un bloque de instrucciones, la condición IF o ELSE puede afectar al rendimiento de una sola instrucción [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Para definir un bloque de instrucciones, utilice las palabras clave de control de flujo BEGIN y END.  
  
## <a name="remarks"></a>Comentarios  
 Una construcción IF...ELSE puede utilizarse en lotes, en procedimientos almacenados y en consultas ad hoc. Cuando esta construcción se utiliza en un procedimiento almacenado, se suele utilizar para probar la existencia de algún parámetro.  
  
 Las pruebas IF pueden estar anidadas después de otra área IF o a continuación de un área ELSE. El límite del número de niveles anidados depende de la memoria disponible.  
  
## <a name="example"></a>Ejemplo  
  
```  
IF DATENAME(weekday, GETDATE()) IN (N'Saturday', N'Sunday')
       SELECT 'Weekend';
ELSE 
       SELECT 'Weekday';
```  
  
 Para obtener más ejemplos, vea [ELSE &#40; IF... ELSE &#41; &#40; Transact-SQL &#41; ](../../t-sql/language-elements/else-if-else-transact-sql.md).  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Ejemplos: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] y[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 En el ejemplo siguiente se utiliza `IF…ELSE` determinar cuál de las dos respuestas para mostrar al usuario, en función del peso de un elemento en el `DimProduct` tabla.  
  
```  
-- Uses AdventureWorksDW  
  
DECLARE @maxWeight float, @productKey integer  
SET @maxWeight = 100.00  
SET @productKey = 424  
IF @maxWeight <= (SELECT Weight from DimProduct 
                  WHERE ProductKey = @productKey)   
    (SELECT @productKey AS ProductKey, EnglishDescription, Weight, 
    'This product is too heavy to ship and is only available for pickup.' 
        AS ShippingStatus
    FROM DimProduct WHERE ProductKey = @productKey);  
ELSE  
    (SELECT @productKey AS ProductKey, EnglishDescription, Weight, 
    'This product is available for shipping or pickup.' 
        AS ShippingStatus
    FROM DimProduct WHERE ProductKey = @productKey);  
```  
  
## <a name="see-also"></a>Vea también  
 [BEGIN...END &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-end-transact-sql.md)   
 [END &#40;BEGIN...END&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/end-begin-end-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [WHILE &#40;Transact-SQL&#41;](../../t-sql/language-elements/while-transact-sql.md)   
 [CASE &#40;Transact-SQL&#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [Lenguaje de control de flujo &#40; Transact-SQL &#41; ](~/t-sql/language-elements/control-of-flow.md) [ELSE &#40; IF... ELSE &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/else-if-else-transact-sql.md) 
  
  



