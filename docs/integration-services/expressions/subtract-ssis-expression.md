---
title: "- (Restar) (expresión de SSIS) | Microsoft Docs"
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
helpviewer_keywords:
- '- (subtract)'
- subtract operator (-)
ms.assetid: b48da086-37dd-460a-8a4b-912f52c9b158
caps.latest.revision: "32"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f5a677e5a997f1b6d4bb440a60afdfbd65f25d3e
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2017
---
# <a name="--subtract-ssis-expression"></a>- (Restar) (expresión de SSIS)
  Resta la segunda expresión numérica de la primera.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
numeric_expression1 – numeric_expression2  
  
```  
  
## <a name="arguments"></a>Argumentos  
 *expresión_numérica1, expresión_numérica2*  
 Expresión válida de un tipo de datos numérico. Para más información, consulte [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Tipos de resultado  
 Dependen de los tipos de datos de los dos argumentos. Para más información, consulte [Integration Services Data Types in Expressions](../../integration-services/expressions/integration-services-data-types-in-expressions.md).  
  
## <a name="remarks"></a>Comentarios  
 Incluya la expresión unaria menos entre paréntesis para asegurarse de que se evalúa en el orden correcto.  
  
## <a name="remarks"></a>Comentarios  
 Si alguno de los operandos es NULL, el resultado será NULL.  
  
## <a name="expression-examples"></a>Ejemplos de expresiones  
 Este ejemplo resta literales numéricos.  
  
```  
5 - 6.09  
```  
  
 Este ejemplo resta el valor de la columna **StandardCost** del valor de la columna **ListPrice** .  
  
```  
ListPrice - StandardCost  
```  
  
 Este ejemplo resta un valor calculado de la columna **ListPrice** . La variable **Discount%** debe escribirse entre corchetes porque el nombre incluye el carácter %. Para obtener más información, vea [Identificadores &#40;SSIS&#41;](../../integration-services/expressions/identifiers-ssis.md).  
  
```  
ListPrice - (ListPrice * @[Discount%])  
```  
  
## <a name="see-also"></a>Vea también  
 [Precedencia y capacidad de asociación de operadores](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Operadores &#40;expresión de SSIS&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
