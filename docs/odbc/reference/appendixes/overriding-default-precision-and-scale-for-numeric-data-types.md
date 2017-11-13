---
title: "Invalidar la precisión y escala predeterminadas de tipos de datos numéricos | Documentos de Microsoft"
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
- numeric data type [ODBC], precision and scale
- precision [ODBC], numeric data types
- data types [ODBC], numeric data types
- numeric data type [ODBC]
- numeric literals [ODBC]
ms.assetid: 84292334-0e33-4a1b-84de-8c018dd787f3
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 613ec65d838a525251b6682cca477c5c8d24a162
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="overriding-default-precision-and-scale-for-numeric-data-types"></a>Invalidar la precisión y escala predeterminadas de tipos de datos numéricos
Cuando se establece el campo SQL_DESC_TYPE en un Descartar para SQL_C_NUMERIC, llamando **SQLBindCol** o **SQLSetDescField**, el campo SQL_DESC_SCALE en la descartar se establece en 0 y se establece el campo SQL_DESC_PRECISION con una precisión predeterminada definida por el controlador. Esto también es cierto cuando el campo SQL_DESC_TYPE en un APD se establece en SQL_C_NUMERIC, llamando **SQLBindParameter** o **SQLSetDescField**. Esto es cierto para la entrada, entrada/salida o parámetros de salida.  
  
 Si previamente cualquiera de los valores predeterminados descritos no son aceptable para una aplicación, la aplicación debe establecer el campo SQL_DESC_SCALE o SQL_DESC_PRECISION mediante una llamada a **SQLSetDescField** o **SQLSetDescRec**.  
  
 Si la aplicación llama **SQLGetData** para devolver datos en una estructura SQL_C_NUMERIC, se usan los campos predeterminados SQL_DESC_SCALE y SQL_DESC_PRECISION. Si los valores predeterminados no son aceptables, la aplicación debe llamar a **SQLSetDescRec** o **SQLSetDescField** para establecer los campos y, a continuación, llamar a **SQLGetData** con un *TargetType* de SQL_ARD_TYPE para usar los valores en los campos de descriptor.  
  
 Cuando **SQLPutData** es llama, la llamada usa los campos SQL_DESC_SCALE y SQL_DESC_PRECISION del registro de descriptor que se corresponde con el parámetro de datos en ejecución o una columna, que son campos APD para las llamadas a  **SQLExecute** o **SQLExecDirect**, o campos de Descartar para las llamadas a **SQLBulkOperations** o **SQLSetPos**.

