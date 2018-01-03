---
title: Restricciones del calendario gregoriano | Documentos de Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data types [ODBC], Gregorian calendar
- Gregorian calendar [ODBC]
ms.assetid: 70667410-c582-4369-8e06-9d98e21cd2bf
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7ac773945c5c138ab6834aa7914d4028d1d5e156
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="constraints-of-the-gregorian-calendar"></a>Restricciones del calendario gregoriano
Tipos de datos de fecha y la fecha y hora y los campos al final de los tipos de datos interval, deben ajustarse a las restricciones del calendario gregoriano. Estas restricciones son los siguientes:  
  
-   El valor del campo de mes debe ser entre 1 y 12, ambos inclusive.  
  
-   El valor del campo de días debe ser en el intervalo comprendido entre 1 y el número de días del mes. El número de días del mes se determina a partir de los valores de los campos de año y meses y puede ser 28, 29, 30 o 31. (El número de días del mes también puede depender de si es un año bisiesto).  
  
-   El valor del campo de hora debe ser entre 0 y 23, ambos inclusive.  
  
-   El valor del campo minuto debe ser entre 0 y 59, ambos inclusive.  
  
-   En el campo de segundos al final de los tipos de datos interval, el valor del campo de segundos debe estar entre 0 y 59.9 (*n*), ambos inclusive, donde  *n*  es el número de dígitos en el precisión de fracciones de segundo.  
  
-   En el campo de segundos al final de los tipos de datos de fecha y hora, el valor del campo de segundos debe estar entre 0 y 61,9 (*n*), ambos inclusive, donde  *n*  especifica el número de "9" dígitos y el valor de  *n*  es la precisión de fracciones de segundo. (El intervalo de segundos permite como máximo dos segundos intercalares para mantener la sincronización de tiempo de sidereal).
