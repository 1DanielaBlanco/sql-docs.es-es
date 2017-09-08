---
title: "AGRUPACIÓN (Transact-SQL) | Documentos de Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GROUPING
- GROUPING_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- null values [SQL Server], GROUPING function
- grouping columns
- ROLLUP operator
- GROUP BY clause, GROUPING function
- GROUPING function
- CUBE operator
ms.assetid: 4efa3868-1fc4-4626-8fb1-e863cc03e422
caps.latest.revision: 32
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d83b68d9d5fb52c67ca3a1910fe9541dfd6f5552
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="grouping-transact-sql"></a>GROUPING (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Indica si una expresión de columna especificada en una lista GROUP BY es agregada o no. GROUPING devuelve 1 para agregado y 0 para no agregado, en el conjunto de resultados. AGRUPACIÓN puede usarse solo en la instrucción SELECT \<seleccione > enumerar, HAVING y se ORDENA por cláusulas cuando se especifica GROUP BY.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
GROUPING ( <column_expression> )  
```  
  
## <a name="arguments"></a>Argumentos  
 \<expresióndecolumna >  
 Es una columna o una expresión que contiene una columna de un [GROUP BY](../../t-sql/queries/select-group-by-transact-sql.md) cláusula.  
  
## <a name="return-types"></a>Tipos devueltos  
 **tinyint**  
  
## <a name="remarks"></a>Comentarios  
 GROUPING se utiliza para distinguir entre los valores NULL devueltos por ROLLUP, CUBE o GROUPING SETS y los valores NULL normales. El valor NULL devuelto como resultado de una operación ROLLUP, CUBE o GROUPING SETS es un uso especial de NULL. Actúa como marcador de posición de columna en el conjunto de resultados y significa "todos".  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se agrupa `SalesQuota` y se agregan las cantidades de `SaleYTD` en la base de datos [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. La función `GROUPING` se aplica a la columna `SalesQuota`.  
  
```  
SELECT SalesQuota, SUM(SalesYTD) 'TotalSalesYTD', GROUPING(SalesQuota) AS 'Grouping'  
FROM Sales.SalesPerson  
GROUP BY SalesQuota WITH ROLLUP;  
GO  
```  
  
 El conjunto de resultados muestra dos valores NULL bajo `SalesQuota`. El primer valor `NULL` representa el grupo de valores NULL de esta columna en la tabla. El segundo valor `NULL` se encuentra en la fila de resumen que agrega la operación ROLLUP. La fila de resumen muestra la `TotalSalesYTD` cantidades para todos los `SalesQuota` agrupa y se indica mediante `1` en la `Grouping` columna.  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `SalesQuota     TotalSalesYTD       Grouping`  
  
 `------------   -----------------   --------`  
  
 `NULL           1533087.5999          0`  
  
 `250000.00      33461260.59           0`  
  
 `300000.00      9299677.9445          0`  
  
 `NULL           44294026.1344         1`  
  
 `(4 row(s) affected)`  
  
## <a name="see-also"></a>Vea también  
 [GROUPING_ID &#40; Transact-SQL &#41;](../../t-sql/functions/grouping-id-transact-sql.md)   
 [GROUP BY &#40; Transact-SQL &#41;](../../t-sql/queries/select-group-by-transact-sql.md)  
  
  
