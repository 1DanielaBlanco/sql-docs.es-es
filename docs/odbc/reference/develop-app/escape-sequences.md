---
title: Secuencias de escape | Documentos de Microsoft
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
- SQL statements [ODBC], interoperability
- escape sequences [ODBC], determining if supported
- interoperability of SQL statements [ODBC], escape sequences
ms.assetid: 5913abfa-d280-43e4-a2f1-05a924388bf9
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a2e9dc60d4cb598c777527aa6825ef2ee3a35b2b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="escape-sequences"></a>Secuencias de escape
ODBC define secuencias de escape que contienen gramática estándar para fecha, hora, marca de tiempo y literales de intervalo de fecha y hora, llamadas a funciones escalares, **como** predicado caracteres de escape, combinaciones externas y llamadas a procedimiento. Aplicaciones interoperables deben usar estas secuencias siempre que sea posible.  
  
 Para determinar si un controlador es compatible con las secuencias de escape para fecha, hora, marca de hora o literales de intervalo de fecha y hora, una aplicación llama **SQLGetTypeInfo**. Si el origen de datos admite una fecha, hora, marca de tiempo o tipo de datos del intervalo de fecha y hora, también debe admitir la secuencia de escape correspondiente. Para determinar si se admiten las otras secuencias de escape, llama a una aplicación **SQLGetInfo**.  
  
 Para obtener más información, consulte [secuencias de Escape de ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md), más adelante en esta sección.
