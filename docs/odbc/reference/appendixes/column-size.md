---
title: "Tamaño de la columna | Documentos de Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data types [ODBC], column size
- size of data types [ODBC]
- SQL data types [ODBC], column characteristics
- column size of data types [ODBC]
ms.assetid: 541b83ab-b16d-4714-bcb2-3c3daa9a963b
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d7c760c40bfdde79f13285270be5038d67096c09
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2017
---
# <a name="column-size"></a>Tamaño de columna
El tamaño de columna (o parámetro) de los tipos de datos numéricos se define como el número máximo de dígitos que se usan por el tipo de datos de la columna o del parámetro o la precisión de los datos. Para los tipos de carácter, ésta es la longitud en caracteres de los datos; para los tipos de datos binarios, el tamaño de la columna se define como la longitud en bytes de los datos. Para la hora, marca de tiempo y todos los tipos de datos de intervalo, este es el número de caracteres en la representación de caracteres de estos datos. El tamaño de columna definido para cada tipo de datos SQL concisa se muestra en la tabla siguiente.  
  
|Identificador de tipo SQL|Tamaño de columna|  
|-------------------------|-----------------|  
|Todos los tipos de caracteres [a], [b].|El tamaño de columna máxima o definida en caracteres de la columna o parámetro (tal y como figura en el campo de descriptor SQL_DESC_LENGTH). Por ejemplo, el tamaño de columna de una columna de caracteres de byte único que se define como char (10) es 10.|  
|SQL_NUMERIC SQL_DECIMAL DE ODBC|El número definido de dígitos. Por ejemplo, la precisión de una columna definida como NUMERIC(10,3) es 10.|  
|SQL_BIT [c]|1|  
|SQL_TINYINT [c]|3|  
|SQL_SMALLINT [c]|5|  
|SQL_INTEGER [c]|10|  
|SQL_BIGINT [c]|19 (si tiene signo) o 20 (si sin signo)|  
|SQL_REAL [c]|7|  
|SQL_FLOAT [c]|15|  
|SQL_DOUBLE [c]|15|  
|Todos los tipos binarios [a], [b].|La longitud máxima o definida de la en bytes de la columna o parámetro. Por ejemplo, la longitud de una columna definida como Binary (10) es 10.|  
|SQL_TYPE_DATE [c]|10 (el número de caracteres en el *aaaa-mm-dd* formato).|  
|SQL_TYPE_TIME [c]|8 (el número de caracteres en el *hh-mm-ss* formato), o 9 + *s* (el número de caracteres en el *hh*formato [.fff...], donde *s*es la precisión de segundos).|  
|SQL_TYPE_TIMESTAMP|16 (el número de caracteres en el *aaaa-mm-dd hh: mm* formato)<br /><br /> 19 (el número de caracteres en el *aaaa-mm-dd* *hh* formato)<br /><br /> o bien<br /><br /> 20 + *s* (el número de caracteres en el *aaaa-mm-dd hh*formato [.fff...], donde *s* es la precisión de segundos).|  
|SQL_INTERVAL_SECOND|Donde *p* es el intervalo de precisión del principio y *s* es la precisión de segundos, *p* (si *s*= 0) o *p* + *s*+ 1 (si *s*> 0).[d]|  
|SQL_INTERVAL_DAY_TO_SECOND|Donde *p* es el intervalo de precisión del principio y *s* es la precisión de segundos, 9 +*p* (si *s*= 0) o 10 +*p* + *s* (si *s*> 0).[d]|  
|SQL_INTERVAL_HOUR_TO_SECOND|Donde *p* es el intervalo de precisión del principio y *s* es la precisión de segundos, 6 +*p* (si *s*= 0) o 7 +*p* + *s* (si *s*> 0).[d]|  
|SQL_INTERVAL_MINUTE_TO_SECOND|Donde *p* es el intervalo de precisión del principio y *s* es la precisión de segundos, 3 +*p* (si *s*= 0) o 4 +*p* + *s* (si *s*> 0).[d]|  
|SQL_INTERVAL_YEAR SQL_INTERVAL_MONTH SQL_INTERVAL_DAY SQL_INTERVAL_HOUR SQL_INTERVAL_MINUTE|*p*, donde *p* es el intervalo de precisión del principio.[d]|  
|SQL_INTERVAL_YEAR_TO_MONTH SQL_INTERVAL_DAY_TO_HOUR|3 +*p*, donde *p* es el intervalo de precisión del principio.[d]|  
|SQL_INTERVAL_DAY_TO_MINUTE|6 +*p*, donde *p* es el intervalo de precisión del principio.[d]|  
|SQL_INTERVAL_HOUR_TO_MINUTE|3 +*p*, donde *p* es el intervalo de precisión del principio.[d]|  
|SQL_GUID|36 (el número de caracteres en el *aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee* formato)|  
  
 [a] aplicación para un ODBC 1.0, que llama a **SQLSetParam** en un controlador de ODBC 2.0 y, para una aplicación ODBC 2.0, que llama a **SQLBindParameter** en un controlador ODBC 1.0, cuando \*  *StrLen_or_IndPtr* es SQL_DATA_AT_EXEC para un tipo SQL_LONGVARCHAR o SQL_LONGVARBINARY, *ColumnSize* debe establecerse en la longitud total de los datos para su envío, no la precisión tal como se define en esta tabla.  
  
 [b] si el controlador no puede determinar la longitud de columna o parámetro de un tipo de variable, devuelve SQL_NO_TOTAL.  
  
 [c] el *ColumnSize* argumento de **SQLBindParameter** se omite para este tipo de datos.  
  
 [d] para las reglas generales acerca de la longitud de la columna en tipos de datos interval, consulte [longitud del tipo de datos de intervalo](../../../odbc/reference/appendixes/interval-data-type-length.md), anteriormente en este apéndice.  
  
 Los valores devueltos para el tamaño de columna (o parámetro) no se corresponden a los valores de cualquier campo descriptor uno. Los valores pueden proceder de la SQL_DESC_PRECISION o el campo SQL_DESC_LENGTH, según el tipo de datos, como se muestra en la tabla siguiente.  
  
|Tipo SQL|Campo descriptor corresponde a<br /><br /> tamaño de columna o parámetro|  
|--------------|--------------------------------------------------------------------|  
|Todos los tipos de caracteres y binarios|LENGTH|  
|Todos los tipos numéricos|PRECISION|  
|Todos los tipos datetime e interval|LENGTH|  
|SQL_BIT|LENGTH|
