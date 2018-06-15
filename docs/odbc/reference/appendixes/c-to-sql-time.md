---
title: 'C a SQL: tiempo | Documentos de Microsoft'
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
- data conversions from C to SQL types [ODBC], time
- time data type [ODBC]
- converting data from c to SQL types [ODBC], time
ms.assetid: a8da43c9-d9a5-45e5-bd9a-1dd633db2ee0
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 381a0ee578b17c37c5646e495025a17538956085
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32906120"
---
# <a name="c-to-sql-time"></a>C a SQL: hora
El identificador para el tipo de datos de hora ODBC C es:  
  
 SQL_C_TYPE_TIME  
  
 La siguiente tabla muestra los tipos de datos a la que se pueden convertir los datos en tiempo de C de ODBC SQL. Para obtener una explicación de las columnas y los términos de la tabla, vea [convertir datos de C a tipos de datos de SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Identificador de tipo SQL|Prueba|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Longitud de bytes de la columna > = 8<br /><br /> Columna de longitud de bytes < 8<br /><br /> Valor de datos no es válida|n/d<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Longitud de caracteres de la columna > = 8<br /><br /> Longitud < 8 de caracteres de la columna<br /><br /> Valor de datos no es válida|n/d<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_TIME|Valor de datos es una hora válida<br /><br /> Valor de datos no es válida|n/d<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|Valor de datos es una hora válida [a]<br /><br /> Valor de datos no es válida|n/d<br /><br /> 22007|  
  
 [a] de la fecha en la parte de la marca de tiempo se establece en la fecha actual y las fracciones de segundo parte de la marca de tiempo se establece en cero.  
  
 Para obtener información acerca de qué valores son válidos en una estructura SQL_C_TYPE_TIME, consulte [tipos de datos C](../../../odbc/reference/appendixes/c-data-types.md), anteriormente en este apéndice.  
  
 Cuando los datos en tiempo de C se convierten en datos de SQL de caracteres, los datos de caracteres resultante están en la "*hh*:*mm*:*ss*" formato.  
  
 El controlador omite el valor de longitud/indicador al convertir datos desde el momento en el tipo de datos de C y se da por supuesto que el tamaño del búfer de datos es el tamaño del tipo de datos C de tiempo. El valor de longitud/indicador se pasa en el *StrLen_or_Ind* argumento en **SQLPutData** y en el búfer especificado con el *StrLen_or_IndPtr* argumento en **SQLBindParameter**. El búfer de datos se especifica con el *DataPtr* argumento en **SQLPutData** y *ParameterValuePtr* argumento en **SQLBindParameter**.
