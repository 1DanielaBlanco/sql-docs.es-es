---
title: "POWER (expresión de SSIS) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: expressions
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: POWER function
ms.assetid: db48ae65-bfa6-4db1-8d3c-d0d4f8a399bc
caps.latest.revision: "30"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f505360aa71886a98f0a56f8402507ecef8f4903
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2017
---
# <a name="power-ssis-expression"></a>POWER (expresión de SSIS)
  Devuelve el resultado de elevar una expresión numérica a una determinada potencia. La evaluación del parámetro de potencia debe devolver un entero.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
POWER(numeric_expression,power)  
```  
  
## <a name="arguments"></a>Argumentos  
 *numeric_expression*  
 Expresión numérica válida.  
  
 *power*  
 Expresión numérica válida.  
  
## <a name="result-types"></a>Tipos de resultado  
 DT_R8  
  
## <a name="remarks"></a>Comentarios  
 Los argumentos *numeric_expression* y *power* se convierten al tipo de datos DT_R8 antes de que se calcule la potencia. Para más información, consulte [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
 Si el valor de *numeric_expression* da como resultado cero y el valor de *power* es negativo, el evaluador de expresiones devolverá un error y establecerá el resultado devuelto en NULL.  
  
 Si *numeric_expression* o *power* producen resultados indeterminados, el resultado devuelto será NULL.  
  
 El argumento *power* puede ser una fracción. Por ejemplo, puede utilizar el valor 0,5 como potencia.  
  
## <a name="expression-examples"></a>Ejemplos de expresiones  
 Este ejemplo usa un literal numérico. La función eleva 4 a la potencia 3 y devuelve 64.  
  
```  
POWER(4,3)  
```  
  
 Este ejemplo utiliza la columna **Length** y la variable **DimensionCount** . Si el valor de **Length** es 8 y el de **DimensionCount** es 2, el resultado devuelto es 64.  
  
```  
POWER(Length, @DimensionCount)   
```  
  
## <a name="see-also"></a>Vea también  
 [Funciones &#40;expresión de SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
