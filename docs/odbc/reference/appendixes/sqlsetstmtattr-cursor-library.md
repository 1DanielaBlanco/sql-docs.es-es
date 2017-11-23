---
title: SQLSetStmtAttr (biblioteca de cursores) | Documentos de Microsoft
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
helpviewer_keywords: SQLSetStmtAttr function [ODBC], Cursor Library
ms.assetid: 6018a733-c2c8-4047-92ec-92cf85031767
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 603a01d46e83b98622b7d143ef162fd5cfbc6518
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2017
---
# <a name="sqlsetstmtattr-cursor-library"></a>SQLSetStmtAttr (biblioteca de cursores)
> [!IMPORTANT]  
>  Esta característica se quitará en una versión futura de Windows. Evite utilizar esta característica en nuevos trabajos de desarrollo y piense en modificar las aplicaciones que actualmente utilizan esta característica. Microsoft recomienda usar la funcionalidad del controlador cursor.  
  
 Este tema describe el uso de la **SQLSetStmtAttr** función en la biblioteca de cursores. Para obtener información general sobre **SQLSetStmtAttr**, consulte [función SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md).  
  
 La biblioteca de cursores es compatible con los siguientes atributos de instrucción con **SQLSetStmtAttr**:  
  
|||  
|-|-|  
|SQL_ATTR_CONCURRENCY|SQL_ATTR_ROW_BIND_OFFSET_PTR|  
|SQL_ATTR_CURSOR_TYPE|SQL_ATTR_ROW_BIND_TYPE|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|SQL_ATTR_ROWSET_ARRAY_SIZE|  
|SQL_ATTR_PARAM_BIND_OFFSET_PTR|SQL_ATTR_SIMULATE_CURSOR|  
|SQL_ATTR_PARAM_BIND_TYPE|SQL_ATTR_USE_BOOKMARKS|  
  
 La biblioteca de cursores admite solo los valores SQL_CURSOR_FORWARD_ONLY y SQL_CURSOR_STATIC del atributo de instrucción SQL_ATTR_CURSOR_TYPE.  
  
 Para los cursores de solo avance, la biblioteca de cursores es compatible con el valor SQL_CONCUR_READ_ONLY del atributo de instrucción SQL_ATTR_CONCURRENCY. Para los cursores estáticos, la biblioteca de cursores es compatible con los valores SQL_CONCUR_READ_ONLY y SQL_CONCUR_VALUES del atributo de instrucción SQL_ATTR_CONCURRENCY.  
  
 La biblioteca de cursores admite sólo el valor SQL_SC_NON_UNIQUE del atributo de instrucción SQL_ATTR_SIMULATE_CURSOR.  
  
 Aunque la especificación de ODBC admite llamadas a **SQLSetStmtAttr** con los atributos SQL_ATTR_PARAM_BIND_TYPE o SQL_ATTR_ROW_BIND_TYPE después **SQLFetch** o **SQLFetchScroll**  se ha llamado, el cursor biblioteca no. Antes de que puede cambiar el tipo de enlace en la biblioteca de cursores, la aplicación debe cerrar el cursor. La biblioteca de cursores admite el cambio de la SQL_ATTR_ROW_BIND_OFFSET_PTR, SQL_ATTR_PARAM_BIND_OFFSET_PTR, SQL_ATTR_ROWS_FETCHED_PTR y atributos de instrucción SQL_ATTR_PARAMS_PROCESSED_PTR cuando un cursor está abierto.  
  
 Una aplicación puede llamar a **SQLSetStmtAttr** con una **atributo** de SQL_ATTR_ROW_ARRAY_SIZE para cambiar el tamaño de conjunto de filas mientras el cursor está abierto. El nuevo tamaño de conjunto de filas surtirán efecto la próxima vez que **SQLFetchScroll** o **SQLFetch** se llama.  
  
 La biblioteca de cursores es compatible con el establecimiento del atributo de instrucción SQL_ATTR_PARAM_BIND_OFFSET_PTR o SQL_ATTR_ROW_BIND_OFFSET_PTR para habilitar los desplazamientos de enlace. El desplazamiento de enlace no se usará para las llamadas a **SQLFetch** cuando se utiliza la biblioteca de cursores con una API ODBC 2. *x* controlador.  
  
 La biblioteca de cursores admite establecer el atributo de instrucción de SQL_ATTR_USE_BOOKMARKS como SQL_UB_VARIABLE.
