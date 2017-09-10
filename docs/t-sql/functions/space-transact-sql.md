---
title: ESPACIO (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SPACE_TSQL
- SPACE
dev_langs:
- TSQL
helpviewer_keywords:
- strings [SQL Server], repeated spaces
- repeated spaces
- SPACE function
ms.assetid: b4fac3b8-2d47-4c11-a6a6-009e5a538f40
caps.latest.revision: 38
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f5de41d3d7619af5f83fa2bee8cd30f980f291b7
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="space-transact-sql"></a>SPACE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Devuelve una cadena de espacios repetidos.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
SPACE ( integer_expression )  
```  
  
## <a name="arguments"></a>Argumentos  
 *integer_expression*  
 Es un entero positivo que indica el número de espacios. Si *integer_expression* es negativo, se devuelve una cadena nula.  
  
 Para obtener más información, vea [expresiones &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
  
## <a name="return-types"></a>Tipos devueltos  
 **varchar**  
  
## <a name="remarks"></a>Comentarios  
 Para incluir espacios en datos Unicode o para devolver más de 8.000 espacios de caracteres, utilice REPLICATE en lugar de SPACE.  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se eliminan los apellidos y se concatena una coma, dos espacios y los nombres de las personas que aparecen en la tabla `Person` de `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT RTRIM(LastName) + ',' + SPACE(2) +  LTRIM(FirstName)  
FROM Person.Person  
ORDER BY LastName, FirstName;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Ejemplos: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] y[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 En el ejemplo siguiente se eliminan los apellidos y se concatena una coma, dos espacios y los nombres de las personas que aparecen en la tabla `DimCustomer` de `AdventureWorksPDW2012`.  
  
```  
-- Uses AdventureWorks  
  
SELECT RTRIM(LastName) + ',' + SPACE(2) +  LTRIM(FirstName)  
FROM dbo.DimCustomer  
ORDER BY LastName, FirstName;  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [REPLICATE &#40; Transact-SQL &#41;](../../t-sql/functions/replicate-transact-sql.md)   
 [Funciones de cadena &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)   
 [Funciones integradas &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)  
  
  



