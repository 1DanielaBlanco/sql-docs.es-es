---
title: TRIM (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- TRIM
- TRIM_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- TRIM function
ms.assetid: a00245aa-32c7-4ad4-a0d1-64f3d6841153
caps.latest.revision: 4
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2017 || = sqlallproducts-allversions
ms.openlocfilehash: a880c9de5b763386504a4163ffe44aaf62c136b4
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "37981384"
---
# <a name="trim-transact-sql"></a>TRIM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

Quita el carácter de espacio `char(32)` (u otros caracteres especificados) del principio o del final de una cadena.  
 
## <a name="syntax"></a>Sintaxis   
```
TRIM ( [ characters FROM ] string ) 
```
[//]: # "[ BOTH | LEADING | TRAILING ] aún no disponibles."

## <a name="arguments"></a>Argumentos   

caracteres   
Es un literal, una variable o una llamada de función de cualquier tipo de carácter no de LOB (`nvarchar`, `varchar`, `nchar` o `char`) que contiene caracteres que se deben quitar. Los tipos `nvarchar(max)` y `varchar(max)` no se permiten.

string   
Es una expresión de cualquier tipo de carácter (`nvarchar`, `varchar`, `nchar` o `char`) donde se deben quitar caracteres.

## <a name="return-types"></a>Tipos devueltos   
Devuelve una expresión de caracteres con un tipo de argumento de cadena donde el carácter de espacio `char(32)` u otros caracteres especificados se quitan de ambos lados. Devuelve `NULL` si la cadena de entrada es `NULL`.

## <a name="remarks"></a>Notas   
La función `TRIM` quita el carácter de espacio `char(32)` de ambos lados de forma predeterminada. Es equivalente a `LTRIM(RTRIM(@string))`. El comportamiento de la función `TRIM ` con los caracteres especificados es idéntico al comportamiento de la función `REPLACE`, donde los caracteres de inicio o finalización se reemplazan por cadenas vacías.


## <a name="examples"></a>Ejemplos
### <a name="a--removes-the-space-character-from-both-sides-of-string"></a>A.  Quitar el carácter de espacio de ambos lados de la cadena   
En el siguiente ejemplo se quitan los espacios que van antes y después de la palabra `test`.   
```sql
SELECT TRIM( '     test    ') AS Result;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   

`test`


### <a name="b--removes-specified-characters-from-both-sides-of-string"></a>B.  Quitar los caracteres especificados de ambos lados de la cadena   
En el siguiente ejemplo se quita un punto final y los espacios finales.
```sql
SELECT TRIM( '.,! ' FROM  '#     test    .') AS Result;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   
`#     test`


## <a name="see-also"></a>Ver también
 [LEFT &#40;Transact-SQL&#41;](../../t-sql/functions/left-transact-sql.md)  
 [LTRIM &#40;Transact-SQL&#41;](../../t-sql/functions/ltrim-transact-sql.md)  
 [RIGHT &#40;Transact-SQL&#41;](../../t-sql/functions/right-transact-sql.md)  
 [RTRIM &#40;Transact-SQL&#41;](../../t-sql/functions/rtrim-transact-sql.md)  
 [STRING_SPLIT &#40;Transact-SQL&#41;](../../t-sql/functions/string-split-transact-sql.md)  
 [SUBSTRING &#40;Transact-SQL&#41;](../../t-sql/functions/substring-transact-sql.md)  
 [Funciones de cadena &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)   
