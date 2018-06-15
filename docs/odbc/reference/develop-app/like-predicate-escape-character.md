---
title: COMO carácter de Escape de predicado | Documentos de Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- LIKE predicate [ODBC]
- escape sequences [ODBC], LIKE predicate
ms.assetid: 185d6109-48cf-4981-bc40-ec2a4a90cafc
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 38fa73fb069f7b7a037a61af711474b277cfa0d7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32911870"
---
# <a name="like-predicate-escape-character"></a>COMO carácter de Escape de predicado
En un **como** predicado, el signo de porcentaje (%) de coincidencias con cero o más de un carácter y el carácter de subrayado (_) coincide con cualquier carácter. Para hacer coincidir un signo de porcentaje real o carácter de subrayado en un **como** predicado, un carácter de escape debe aparecer antes del signo de porcentaje o un carácter de subrayado. La secuencia de escape que define la **como** carácter de escape de predicado es:  
  
 **{escape '** *carácter de escape* **'}**  
  
 donde *carácter de escape* es cualquier carácter compatible con el origen de datos.  
  
 Para obtener más información sobre el tipo de secuencia de escape, vea [como secuencia de Escape](../../../odbc/reference/appendixes/like-escape-sequence.md) en Apéndice C: SQL gramática.  
  
 Por ejemplo, las siguientes instrucciones SQL crean el mismo conjunto de resultados de cliente nombres que empiezan con los caracteres "% AAA". La primera instrucción utiliza la sintaxis de la secuencia de escape. La segunda instrucción utiliza la sintaxis nativo para Microsoft® Access y no es interoperable. Observe que el segundo carácter de porcentaje de cada **como** predicado es un carácter comodín que coincide con cero o más de un carácter.  
  
```  
SELECT Name FROM Customers WHERE Name LIKE '\%AAA%' {escape '\'}  
  
SELECT Name FROM Customers WHERE Name LIKE '[%]AAA%'  
```  
  
 Para determinar si la **como** caracteres de escape de predicado es compatible con un origen de datos, las llamadas de una aplicación **SQLGetInfo** con la opción SQL_LIKE_ESCAPE_CLAUSE.
