---
title: POWER (expresión de SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- POWER function
ms.assetid: db48ae65-bfa6-4db1-8d3c-d0d4f8a399bc
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b949c3191e00d3c6f1fc30f46ababfa2fd868d2f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37245205"
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
  
## <a name="remarks"></a>Notas  
 Los argumentos *numeric_expression* y *power* se convierten al tipo de datos DT_R8 antes de que se calcule la potencia. Para más información, consulte [Integration Services Data Types](../data-flow/integration-services-data-types.md).  
  
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
 [Funciones &#40;expresión de SSIS&#41;](functions-ssis-expression.md)  
  
  
