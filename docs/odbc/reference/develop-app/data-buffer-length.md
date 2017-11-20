---
title: "Longitud del búfer de datos | Documentos de Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data buffers [ODBC], length
- buffers [ODBC], data
- length of data buffers [ODBC]
- buffers [ODBC], length
ms.assetid: 7288d143-f9e5-4f90-9b31-2549df79c109
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 84bacf4e45760b14515d44a9d81f46de4485ee5f
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="data-buffer-length"></a>Longitud del búfer de datos
La aplicación pasa la longitud de bytes del búfer de datos para el controlador de un argumento, denominado *BufferLength* o un nombre similar. Por ejemplo, en la siguiente llamada a **SQLBindCol**, la aplicación especifica la longitud de la *ValuePtr* búfer (**sizeof (***ValuePtr***)**):  
  
```  
SQLCHAR      ValuePtr[50];  
SQLINTEGER   ValueLenOrInd;  
SQLBindCol(hstmt, 1, SQL_C_CHAR, ValuePtr, sizeof(ValuePtr), &ValueLenOrInd);  
```  
  
 Un controlador siempre devolverá el número de bytes, no el número de caracteres, en el argumento de longitud de búfer de cualquier función que tiene un argumento de cadena de salida.  
  
 Longitud del búfer de datos solo es necesarias para los búferes de salida; el controlador usa para evitar escribir más allá del final del búfer. Sin embargo, el controlador comprueba la longitud del búfer de datos sólo cuando el búfer contiene datos de longitud variable, como datos de caracteres o binarios. Si el búfer contiene datos de longitud fija, como una estructura de entero o una fecha, el controlador pasa por alto la longitud del búfer de datos y se da por supuesto que el búfer es lo suficientemente grande como para contener los datos; es decir, nunca trunca los datos de longitud fija. Por lo tanto, es importante para la aplicación asignar un búfer lo suficientemente grande como para datos de longitud fija.  
  
 Cadenas de resultados de un truncamiento de datos no se produce (como el nombre del cursor devuelto para **SQLGetCursorName**), la longitud devuelta en el argumento de longitud de búfer es la longitud máxima de caracteres posible.  
  
 Longitud del búfer de datos no es necesarios para los búferes de entrada porque el controlador no escribe en estos búferes.  
  
 Esta sección contiene los temas siguientes.  
  
-   [Uso de valores de longitud/indicador](../../../odbc/reference/develop-app/using-length-and-indicator-values.md)  
  
-   [Longitud de los datos, la longitud de búfer y truncamiento](../../../odbc/reference/develop-app/data-length-buffer-length-and-truncation.md)  
  
-   [Datos de caracteres y cadenas de c.](../../../odbc/reference/develop-app/character-data-and-c-strings.md)

