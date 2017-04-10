---
title: "&amp; (AND bit a bit) (expresi&#243;n de SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "AND, AND bit a bit"
  - "& (AND bit a bit)"
  - "AND bit a bit (&)"
ms.assetid: 06d2958e-66a5-44d8-8bc4-56209ebe1ff2
caps.latest.revision: 40
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 40
---
# &amp; (AND bit a bit) (expresi&#243;n de SSIS)
  Lleva a cabo una operación AND bit a bit entre dos valores enteros. Compara cada bit del primer operando con el bit correspondiente del segundo operando. Si ambos bits son 1, el bit de resultado correspondiente se establece en 1. De lo contrario, se establece en 0.  
  
 Ambas condiciones deben ser de tipo entero con signo o de tipo entero sin signo.  
  
## Sintaxis  
  
```  
  
integer_expression1 & integer_expression2  
  
```  
  
## Argumentos  
 *integer_expression1, integer_expression2*  
 Cualquier expresión válida de tipo entero con o sin signo. Para más información, consulte [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## Tipos de resultado  
 Determinados por los tipos de datos de los dos argumentos. Para más información, consulte [Integration Services Data Types in Expressions](../../integration-services/expressions/integration-services-data-types-in-expressions.md).  
  
## Comentarios  
 Si alguna de las condiciones es NULL, el resultado de la expresión será NULL.  
  
## Ejemplos de expresiones  
 Este ejemplo realiza una operación AND bit a bit entre las columnas **NumberA** y **NumberB**. **NumberA** contiene 3 (0000011) y la columna **NumberB** contiene 7 (00000111).  
  
```  
NumberA & NumberB  
```  
  
 El resultado de evaluar la expresión es 3 (00000011).  
  
 00000011  
  
 00000111  
  
 ----------\-  
  
 00000011  
  
 Este ejemplo realiza una operación AND bit a bit entre las columnas **ReorderPoint** y **SafetyStockLevel** .  
  
```  
ReorderPoint & SafetyStockLevel  
```  
  
 Si el valor de **ReorderPoint** es 10 y el valor de **SafetyStockLevel** es 8, la expresión da como resultado 8 (00001000).  
  
 00001010  
  
 00001000  
  
 ----------\-  
  
 00001000  
  
 Este ejemplo realiza una operación AND bit a bit entre dos enteros.  
  
```  
3 & 5   
```  
  
 El resultado de evaluar la expresión es 1 (00000001).  
  
 00000011  
  
 00000101  
  
 ----------\-  
  
 00000001  
  
## Vea también  
 [&& &#40;AND lógico&#41; &#40;expresión de SSIS&#41;](../../integration-services/expressions/logical-and-ssis-expression.md)   
 [Precedencia y capacidad de asociación de operadores](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Operadores &#40;expresión de SSIS&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  