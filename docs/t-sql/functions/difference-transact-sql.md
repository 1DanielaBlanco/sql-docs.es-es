---
title: DIFERENCIA (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DIFFERENCE
- DIFFERENCE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DIFFERENCE function
- comparing SOUNDEX values
- SOUNDEX values
ms.assetid: c58ca25d-d6ea-48fa-93bb-c9374b0b2a2b
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: 1868f902cf41eba9637138d7333ac908c72cb76e
ms.contentlocale: es-es
ms.lasthandoff: 10/17/2017

---
# <a name="difference-transact-sql"></a>DIFFERENCE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Devuelve un valor entero que indica la diferencia entre los valores de SOUNDEX de dos expresiones de caracteres.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
DIFFERENCE ( character_expression , character_expression )  
```  
  
## <a name="arguments"></a>Argumentos  
 *character_expression*  
 Es un carácter alfanumérico [expresión](../../t-sql/language-elements/expressions-transact-sql.md) de datos de caracteres. *character_expression* puede ser una constante, variable o columna.  
  
## <a name="return-types"></a>Tipos devueltos  
 **int**  
  
## <a name="remarks"></a>Comentarios  
 El entero devuelto es el número de caracteres de los valores de SOUNDEX que son iguales. El valor devuelto puede oscilar entre 0 y 4, donde 0 indica una similitud escasa o inexistente, y 4 indica una elevada similitud o los mismos valores.  
  
 DIFFERENCE y SOUNDEX distinguen la intercalación.  
  
## <a name="examples"></a>Ejemplos  
 En la primera parte del ejemplo siguiente, se comparan los valores de `SOUNDEX` de dos cadenas muy similares. Para una intercalación Latin1_General `DIFFERENCE` devuelve un valor de `4`. En la segunda parte del ejemplo siguiente, la `SOUNDEX` valores para que se comparan dos cadenas muy diferentes y una intercalación Latin1_General `DIFFERENCE` devuelve un valor de `0`.  
  
```  
-- Returns a DIFFERENCE value of 4, the least possible difference.  
SELECT SOUNDEX('Green'), SOUNDEX('Greene'), DIFFERENCE('Green','Greene');  
GO  
-- Returns a DIFFERENCE value of 0, the highest possible difference.  
SELECT SOUNDEX('Blotchet-Halls'), SOUNDEX('Greene'), DIFFERENCE('Blotchet-Halls', 'Greene');  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----- ----- -----------   
G650  G650  4             
  
(1 row(s) affected)  
  
----- ----- -----------   
B432  G650  0             
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vea también  
 [SOUNDEX & #40; Transact-SQL & #41;](../../t-sql/functions/soundex-transact-sql.md)   
 [Funciones de cadena & #40; Transact-SQL & #41;](../../t-sql/functions/string-functions-transact-sql.md)  
  
  


