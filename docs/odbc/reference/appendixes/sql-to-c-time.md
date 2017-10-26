---
title: 'SQL a la hora C: | Documentos de Microsoft'
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- converting data from SQL to C types [ODBC], time
- time data type [ODBC]
- data conversions from SQL to C types [ODBC], time
ms.assetid: 6dc59973-7bb5-40f1-87c8-5bf68b3bf2ee
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b424acc8e42f94c23e793a8b811b0c2347a313a1
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="sql-to-c-time"></a>SQL a la hora C:
El identificador de la hora es de tipo de datos SQL de ODBC:  
  
 SQL_TYPE_TIME  
  
 La siguiente tabla muestra los tipos de datos a la que se pueden convertir los datos SQL de tiempo de la C de ODBC. Para obtener una explicación de las columnas y los términos de la tabla, vea [convertir datos de SQL a tipos de datos C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Identificador de tipo de C|Prueba|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > longitud de bytes de caracteres<br /><br /> *9* <= *BufferLength* < = longitud de bytes de caracteres<br /><br /> *BufferLength* < 9|data<br /><br /> Datos truncados [a]<br /><br /> No definido|Longitud de los datos en bytes<br /><br /> Longitud de los datos en bytes<br /><br /> No definido|n/d<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*BufferLength* > longitud de caracteres<br /><br /> *9* <= *BufferLength* < = longitud de caracteres<br /><br /> *BufferLength* < 9|data<br /><br /> Datos truncados [a]<br /><br /> No definido|Longitud de datos de caracteres<br /><br /> Longitud de datos de caracteres<br /><br /> No definido|n/d<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|Longitud de bytes de datos < = *BufferLength*<br /><br /> Longitud de bytes de datos > *BufferLength*|data<br /><br /> No definido|Longitud de los datos en bytes<br /><br /> No definido|n/d<br /><br /> 22003|  
|SQL_C_TYPE_TIME|Ninguno [b]|data|6 [d]|n/d|  
|SQL_C_TYPE_TIMESTAMP|Ninguno [b]|Datos [c]|16 [d]|n/d|  
  
 [a] se truncan las fracciones de segundo del tiempo.  
  
 [b], el valor de *BufferLength* se pasa por alto para esta conversión. El controlador se da por supuesto que el tamaño de **TargetValuePtr* es el tamaño del tipo de datos C.  
  
 [c], los campos de fecha de la estructura de marca de tiempo se establecen en la fecha actual y el campo de fracciones de segundo de la estructura de marca de tiempo se establece en cero.  
  
 [d] es el tamaño del tipo de datos C correspondiente.  
  
 Cuando los datos de SQL de tiempo se convierte en datos de caracteres C, la cadena resultante es en el "*hh*:*mm*:*ss*" formato. Este formato no se ve afectado por el valor de país Windows®.

