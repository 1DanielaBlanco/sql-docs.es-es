---
title: ALL (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server (starting with 2008)
f1_keywords:
- ALL_TSQL
- ALL
dev_langs:
- TSQL
helpviewer_keywords:
- single-column set of values [SQL Server]
- ALL (Transact-SQL)
ms.assetid: 4b0c002e-1ffd-4425-a980-11fdc1f24af7
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 142fbd5b352a73e382f89a61f60fba6373902172
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="all-transact-sql"></a>ALL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Compara un valor escalar con un conjunto de valores de una sola columna.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
scalar_expression { = | <> | != | > | >= | !> | < | <= | !< } ALL ( subquery )  
```  
  
## <a name="arguments"></a>Argumentos  
 *scalar_expression*  
 Es cualquier [expresión](../../t-sql/language-elements/expressions-transact-sql.md) válida.  
  
 { = | <> | != | > | >= | !> | < | <= | !< }  
 Es un operador de comparación.  
  
 *subquery*  
 Es una subconsulta que devuelve un conjunto de resultados de una columna. El tipo de datos de la columna devuelta debe ser igual que el tipo de datos de *scalar_expression*.  
  
 Es una instrucción SELECT restringida en la que no se permiten la cláusula ORDER BY ni la palabra clave INTO.  
  
## <a name="result-types"></a>Tipos de resultado  
 **Boolean**  
  
## <a name="result-value"></a>Valor del resultado  
 Devuelve TRUE cuando la comparación especificada es TRUE para todos los pares (*scalar_expression***,***x)*, donde *x* es un valor del conjunto de una sola columna; en caso contrario, devuelve FALSE.  
  
## <a name="remarks"></a>Notas  
 ALL requiere que *scalar_expression* se compare de forma positiva con cada valor devuelto por la subconsulta. Por ejemplo, si la subconsulta devuelve los valores 2 y 3, *scalar_expression* <= ALL (subconsulta) se evaluaría como TRUE para una *scalar_expression* de 2. Si la subconsulta devuelve los valores 2 y 3, *scalar_expression* = ALL (subconsulta) se evaluaría como FALSE, porque algunos de los valores de la subconsulta (el valor 3) no cumplirían los criterios de la expresión.  
  
 Para instrucciones que requieren que *scalar_expression* se compare de forma positiva con solo un valor devuelto por la subconsulta, vea [SOME &#124; ANY &#40;Transact-SQL&#41;](../../t-sql/language-elements/some-any-transact-sql.md).  
  
 Este tema hace referencia a ALL cuando se utiliza con una subconsulta. ALL también se puede usar con [UNION](../../t-sql/language-elements/set-operators-union-transact-sql.md) y [SELECT](../../t-sql/queries/select-transact-sql.md).  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se crea un procedimiento almacenado que determina si todos los componentes de un valor `SalesOrderID` especificado en la base de datos [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] se pueden fabricar en el número de días especificado. En el ejemplo se usa una subconsulta para crear una lista del número del valor de `DaysToManufacture` para todos los componentes del `SalesOrderID` específico y, a continuación, confirma que todos los `DaysToManufacture` están dentro del número de días especificado.  
  
```  
-- Uses AdventureWorks  
  
CREATE PROCEDURE DaysToBuild @OrderID int, @NumberOfDays int  
AS  
IF   
@NumberOfDays >= ALL  
   (  
    SELECT DaysToManufacture  
    FROM Sales.SalesOrderDetail  
    JOIN Production.Product   
    ON Sales.SalesOrderDetail.ProductID = Production.Product.ProductID   
    WHERE SalesOrderID = @OrderID  
   )  
PRINT 'All items for this order can be manufactured in specified number of days or less.'  
ELSE   
PRINT 'Some items for this order cannot be manufactured in specified number of days or less.' ;  
  
```  
  
 Para probar el procedimiento, ejecútelo con `SalesOrderID 49080`, que tiene un componente que requiere `2` días y dos componentes que requieren 0 días. La primera instrucción que se indica a continuación cumple los criterios. La segunda consulta no los cumple.  
  
```  
EXECUTE DaysToBuild 49080, 2 ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `All items for this order can be manufactured in specified number of days or less.`  
  
```  
EXECUTE DaysToBuild 49080, 1 ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Some items for this order cannot be manufactured in specified number of days or less.`  
  
## <a name="see-also"></a>Ver también  
 [CASE &#40;Transact-SQL&#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [Expresiones &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Funciones integradas &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [LIKE &#40;Transact-SQL&#41;](../../t-sql/language-elements/like-transact-sql.md)   
 [Operadores &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [WHERE &#40;Transact-SQL&#41;](../../t-sql/queries/where-transact-sql.md)   
 [IN &#40;Transact-SQL&#41;](../../t-sql/language-elements/in-transact-sql.md)  
  
  
