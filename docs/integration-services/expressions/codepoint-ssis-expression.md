---
title: "CODEPOINT (expresión de SSIS) | Microsoft Docs"
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
- CODEPOINT function
- leftmost character of expression
ms.assetid: 0783d05e-7f35-42fb-a2c4-9621c46effd6
caps.latest.revision: "22"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 19af45b2e69490b3573dde39a81fabe103bcf4a0
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2017
---
# <a name="codepoint-ssis-expression"></a>CODEPOINT (expresión de SSIS)
  Devuelve el punto de código Unicode del primer carácter de la izquierda de una expresión de caracteres.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
CODEPOINT(character_expression)  
```  
  
## <a name="arguments"></a>Argumentos  
 *character_expression*  
 Expresión de caracteres de la que se va a evaluar el primer carácter de la izquierda.  
  
## <a name="result-types"></a>Tipos de resultado  
 DT_UI2  
  
## <a name="remarks"></a>Comentarios  
 *character_expression* necesita tener el tipo de datos DT_WSTR.  
  
 CODEPOINT devuelve un resultado NULL si *character_expression* es NULL o una cadena vacía.  
  
## <a name="expression-examples"></a>Ejemplos de expresiones  
 Este ejemplo usa un literal de cadena. El resultado devuelto es 77, el punto de código Unicode correspondiente a la M.  
  
```  
CODEPOINT("Mountain Bike")  
```  
  
 En este ejemplo se utiliza una variable. Si el valor de **Name** es Touring Front Wheel, el resultado devuelto es 84, el punto de código Unicode correspondiente a la T.  
  
```  
CODEPOINT(@Name)  
```  
  
## <a name="see-also"></a>Vea también  
 [Funciones &#40;expresión de SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
