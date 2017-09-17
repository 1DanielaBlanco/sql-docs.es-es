---
title: ~ (NOT bit a bit) (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 01/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ~_TSQL
- bitwise
- NOT
- ~
- Bitwise NOT
dev_langs:
- TSQL
helpviewer_keywords:
- NOT keyword
- bitwise NOT (~)
- ~ (bitwise NOT)
ms.assetid: 02da8016-f6c0-41ae-8d59-33eaa02bfc95
caps.latest.revision: 42
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3cfe0944a896548bfd0e0e0612b832ac91417016
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="-bitwise-not-transact-sql"></a>~ (NOT bit a bit) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Lleva a cabo una operación lógica NOT bit a bit en un valor entero.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
~ expression  
```  
  
## <a name="arguments"></a>Argumentos  
 *expression*  
 Se trata de cualquier [expresión](../../t-sql/language-elements/expressions-transact-sql.md) de cualquiera de los tipos de datos de la categoría de tipo de datos entero, el **bits**, o la **binario** o **varbinary** datos tipos. *expresión* se trata como un número binario para la operación bit a bit.  
  
> [!NOTE]  
>  Solo un *expresión* puede ser del **binario** o **varbinary** tipo de datos en una operación bit a bit.  
  
## <a name="result-types"></a>Tipos de resultado  
 **int** si los valores de entrada son **int**.  
  
 **smallint** si los valores de entrada son **smallint**.  
  
 **tinyint** si los valores de entrada son **tinyint**.  
  
 **bit** si los valores de entrada son **bits**.  
  
## <a name="remarks"></a>Comentarios  
 El  **~**  operador bit a bit realiza un operador lógico NOT bit a bit para el *expresión*, toma cada bit a su vez. Si *expresión* tiene un valor de 0, los bits del conjunto de resultados se establecen en 1; de lo contrario, el bit del resultado se borra a un valor de 0. En otras palabras, los unos pasan a los ceros y los ceros pasan a unos.  
  
> [!IMPORTANT]  
>  Cuando se realiza cualquier clase de operación bit a bit, es importante la longitud del almacenamiento de la expresión que se utiliza para la operación bit a bit. Se recomienda utilizar el mismo número de bytes al almacenar los valores. Por ejemplo, almacenar el valor decimal de 5 como un **tinyint**, **smallint**, o **int** genera un valor almacenado con distintos números de bytes: **tinyint** almacena datos con 1 byte; **smallint** almacena los datos utilizando 2 bytes, y **int** almacena los datos con 4 bytes. Por lo tanto, realizar una operación bit a bit en una **int** valor decimal puede producir resultados diferentes de los que utilizan una traducción directa de binaria o hexadecimal, especialmente cuando el  **~**  () NOT bit a bit) se utiliza el operador. La operación NOT bit a bit puede tener lugar en una variable con una longitud menor. En este caso, cuando se convierte a una variable de un tipo de datos más largo, los bits del conjunto de 8 bits superiores no pueden establecerse en el valor previsto. Se recomienda convertir la variable del tipo de datos más pequeño al tipo de datos mayor, y, a continuación, realizar la operación NOT en el resultado.  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se crea una tabla con el **int** tipo para almacenar los valores de datos e inserta los dos valores en una fila.  
  
```  
CREATE TABLE bitwise  
(   
a_int_value int NOT NULL,  
b_int_value int NOT NULL  
);  
GO  
INSERT bitwise VALUES (170, 75);  
GO  
```  
  
 La consulta siguiente realiza la operación NOT bit a bit en las columnas `a_int_value` y `b_int_value`.  
  
```  
SELECT ~ a_int_value, ~ b_int_value  
FROM bitwise;  
```  
  
 El conjunto de resultados es:  
  
```  
--- ---   
-171  -76   
  
(1 row(s) affected)  
```  
  
 La representación binaria de 170 (`a_int_value` o `A`) es `0000 0000 1010 1010`. Al realizar la operación NOT bit a bit con este valor, se obtiene el resultado binario `1111 1111 0101 0101`, que es el -171 en notación decimal. La representación binaria de 75 es `0000 0000 0100 1011`. Realizar la operación NOT bit a bit produce `1111 1111 1011 0100`, que es el decimal -76.  
  
```  
 (~A)     
         0000 0000 1010 1010  
         -------------------  
         1111 1111 0101 0101  
(~B)     
         0000 0000 0100 1011  
         -------------------  
         1111 1111 1011 0100  
```  
  
 
## <a name="see-also"></a>Vea también  
 [Expresiones &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Operadores &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Operadores bit a bit &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-operators-transact-sql.md)  
  
  



