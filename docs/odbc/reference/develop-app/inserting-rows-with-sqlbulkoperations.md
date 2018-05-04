---
title: Insertar filas con SQLBulkOperations | Documentos de Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLBulkOperations function [ODBC], inserting rows
- data updates [ODBC], SQLBulkOperations
- updating data [ODBC], SQLBulkOperations
ms.assetid: ed585ea7-4d56-4df9-8dc3-53ca82382450
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0f18f0e300b8f97c51f76c0d026d2d8c237ca979
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="inserting-rows-with-sqlbulkoperations"></a>Insertar filas con SQLBulkOperations
Insertar datos con **SQLBulkOperations** es similar a la actualización de datos con **SQLBulkOperations** porque utiliza datos de los búferes de aplicación enlazadas.  
  
 Para que cada columna de la nueva fila tiene un valor, todas las columnas con un valor de longitud/indicador de SQL_COLUMN_IGNORE enlazadas y todas las columnas sin enlazar deben aceptar valores NULL o tener un valor predeterminado.  
  
 Para insertar filas con **SQLBulkOperations**, la aplicación hace lo siguiente:  
  
1.  Establece el atributo de instrucción de SQL_ATTR_ROW_ARRAY_SIZE en el número de filas para insertar y coloca los nuevos valores de datos en los búferes de aplicación enlazadas. Para obtener información sobre cómo enviar datos largos con **SQLBulkOperations**, consulte [datos de tipo Long y SQLSetPos y SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
2.  Establece el valor en el búfer de longitud/indicador de cada columna según sea necesario. Se trata de la longitud de bytes de los datos o SQL_NTS de las columnas enlazadas a los búferes de cadena, la longitud de bytes de los datos de las columnas enlazadas a búferes binarios y SQL_NULL_DATA de las columnas que se establece en NULL. La aplicación establece el valor en el búfer de longitud/indicador de las columnas que se van a establecer en su valor predeterminado (si existe) o NULL (si no lo hace) para SQL_COLUMN_IGNORE.  
  
3.  Llamadas **SQLBulkOperations** con el *operación* establecido en SQL_ADD.  
  
 Después de **SQLBulkOperations** devuelve, no se ha modificado la fila actual. Si está enlazada la columna de marcador (columna 0), **SQLBulkOperations** devuelve los marcadores de las filas insertadas en el búfer de conjunto de filas enlazados a esa columna.
