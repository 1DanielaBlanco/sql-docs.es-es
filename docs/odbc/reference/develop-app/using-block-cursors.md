---
title: Usar cursores de bloque | Documentos de Microsoft
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
- cursors [ODBC], block
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 2aad7d6b-216e-47e7-b3cb-f95ad096f21a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 51f02b5b243286a650897fecdcac5d8778bd3f40
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="using-block-cursors"></a>Usar cursores de bloque
Compatibilidad con cursores de bloque está integrada en ODBC 3. *x*. **SQLFetch** puede utilizarse solo para capturar varias filas cuando se llama en ODBC 3. *x*; si un ODBC 2. *x* aplicación llama **SQLFetch**, se abrirá un cursor varias filas, solo hacia delante. Cuando un ODBC 3. *x* aplicación llama **SQLFetch** en una API ODBC 2. *x* controlador, devuelve una sola fila, a menos que el controlador admite **SQLExtendedFetch**. Para obtener más información, consulte [compatibilidad con versiones anteriores, los cursores desplazables y cursores de bloque](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) en Apéndice G: controlador directrices para la compatibilidad con versiones anteriores.  
  
 Para utilizar cursores de bloque, la aplicación establece el tamaño del conjunto de filas, enlaza los búferes de conjunto de filas (como se describe en la sección anterior), opcionalmente establece los atributos de instrucción SQL_ATTR_ROWS_FETCHED_PTR y SQL_ATTR_ROW_STATUS_PTR y las llamadas **SQLFetch**  o **SQLFetchScroll** para capturar un bloque de filas. La aplicación puede cambiar el tamaño del conjunto de filas y enlazar nuevos búferes de conjunto de filas (mediante una llamada a **SQLBindCol** o especificando un desplazamiento de bind) incluso después de filas se han capturado.  
  
 Esta sección contiene los temas siguientes.  
  
-   [Tamaño del conjunto de filas](../../../odbc/reference/develop-app/rowset-size.md)  
  
-   [Número de filas recuperadas y estado](../../../odbc/reference/develop-app/number-of-rows-fetched-and-status.md)  
  
-   [SQLGetData y cursores de bloque; curso de bloque](../../../odbc/reference/develop-app/sqlgetdata-and-block-cursors.md)

