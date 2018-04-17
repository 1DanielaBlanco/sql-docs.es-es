---
title: Desplazamiento y captura filas | Documentos de Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-cursors
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- scrollable cursors [SQL Server]
- SQL Server Native Client ODBC driver, cursors
- SQLFetchScroll function
- ODBC applications, cursors
- cursors [ODBC], fetching rows
- ODBC cursors, fetching rows
- cursors [ODBC], scrolling rows
- fetching [ODBC]
- ODBC cursors, scrolling rows
ms.assetid: 9109f10d-326b-4a6d-8c97-831f60da8c4c
caps.latest.revision: 34
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 3b2824c0b21c845fe2925fec00e58ea46d0cf4d8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="scrolling-and-fetching-rows"></a>Desplazamiento y captura de filas
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Para utilizar un cursor desplazable, una aplicación ODBC debe:  
  
-   Establecer las capacidades de cursor con [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
-   Abrir el cursor mediante **SQLExecute** o **SQLExecDirect**.  
  
-   Desplazarse y capturar filas mediante **SQLFetch** o [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md).  
  
 Ambos **SQLFetch** y **SQLFetchSroll** pueden capturar bloques de filas a la vez. El número de filas devueltas se especifica mediante **SQLSetStmtAttr** para establecer el parámetro SQL_ATTR_ROW_ARRAY_SIZE.  
  
 Aplicaciones ODBC pueden utilizar **SQLFetch** para capturar filas mediante un cursor de solo avance.  
  
 **SQLFetchScroll** se utiliza para desplazarse por un cursor. **SQLFetchScroll** admite la captura de la siguiente, conjuntos de filas de anterior, primero y último además una captura relativa (capturar el conjunto de filas *n* filas desde el principio del conjunto de filas actual) y una captura absoluta (captura el conjunto de filas a partir de fila *n*). Si *n* es negativo en una captura absoluta, las filas se cuentan desde el final del conjunto de resultados. Una captura absoluta de la fila -1 significa que se capturará el conjunto de filas que empieza con la última fila del conjunto de resultados.  
  
 Las aplicaciones que utilizan **SQLFetchScroll** únicamente para su bloque de capacidades de cursor, como informes, están probable que atraviesen el conjunto de resultados de una sola vez, utilizando solo la opción para capturar el siguiente conjunto de filas. Las aplicaciones basadas en la pantalla, por otro lado, pueden aprovechar todas las capacidades de **SQLFetchScroll**. Si la aplicación establece el tamaño del conjunto de filas en el número de filas que se muestran en la pantalla y enlaza los búferes de pantalla al conjunto de resultados, pueden traducir las operaciones de la barra de desplazamiento directamente en llamadas a **SQLFetchScroll**.  
  
|Funcionamiento de la barra de desplazamiento|Opción de desplazamiento de SQLFetchScroll|  
|--------------------------|-------------------------------------|  
|Re Pág|SQL_FETCH_PRIOR|  
|AV PÁG|SQL_FETCH_NEXT|  
|Línea arriba|SQL_FETCH_RELATIVE con FetchOffset igual a -1|  
|Línea abajo|SQL_FETCH_RELATIVE con FetchOffset igual a 1|  
|Cuadro de desplazamiento hacia arriba|SQL_FETCH_FIRST|  
|Cuadro de desplazamiento hacia abajo|SQL_FETCH_LAST|  
|Posición del cuadro de desplazamiento aleatoria|SQL_FETCH_ABSOLUTE|  
  
## <a name="in-this-section"></a>En esta sección  
  
-   [Marcar filas en ODBC](../../relational-databases/native-client-odbc-cursors/scrolling-and-fetching-rows-bookmarking-rows-in-odbc.md)  
  
## <a name="see-also"></a>Vea también  
 [Usar cursores & #40; ODBC & #41;](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
