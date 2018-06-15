---
title: SQLGetDescField y SQLGetDescRec (biblioteca de cursores) | Documentos de Microsoft
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
- SQLGetDescField function [ODBC], Cursor Library
- SQLGetDescRec function [ODBC], Cursor Library
ms.assetid: 1a801f22-6fea-48aa-a723-3187a2ad852b
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: da57c5fb9f0ddb8d9e45651f9404d7825497d425
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32908810"
---
# <a name="sqlgetdescfield-and-sqlgetdescrec-cursor-library"></a>SQLGetDescField y SQLGetDescRec (biblioteca de cursores)
> [!IMPORTANT]  
>  Esta característica se quitará en una versión futura de Windows. Evite utilizar esta característica en nuevos trabajos de desarrollo y piense en modificar las aplicaciones que actualmente utilizan esta característica. Microsoft recomienda usar la funcionalidad del controlador cursor.  
  
 Este tema describe el uso de la **SQLGetDescField** y **SQLGetDescRec** funciones en la biblioteca de cursores. Para obtener información general acerca de estas funciones, vea [función SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md) y [sqlgetdescrec, función](../../../odbc/reference/syntax/sqlgetdescrec-function.md).  
  
 La biblioteca de cursores ejecuta **SQLGetDescRec** para devolver los metadatos para las columnas de marcador. La biblioteca de cursores ejecuta **SQLGetDescField** para devolver los mismos campos devueltos por **SQLGetDescRec**, que son SQL_DESC_NAME, SQL_DESC_TYPE, SQL_DESC_DATETIME_INTERVAL_CODE, SQL_DESC_OCTET_ LONGITUD, SQL_DESC_PRECISION, SQL_DESC_SCALE y SQL_DESC_NULLABLE. Para mantener la coherencia, **SQLGetDescField** también devuelve SQL_DESC_UNNAMED.  
  
 La biblioteca de cursores ejecuta **SQLGetDescField** cuando se llama para devolver el valor de los siguientes campos que se establecen para columnas de marcadores de enlace: SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR y SQL_DESC_OCTET_LENGTH_PTR, y SQL_DESC_LENGTH.  
  
 La biblioteca de cursores ejecuta **SQLGetDescField** cuando se llama para devolver el valor del campo SQL_DESC_BIND_OFFSET_PTR, SQL_DESC_BIND_TYPE, SQL_DESC_ROW_ARRAY_SIZE o SQL_DESC_ROW_STATUS_PTR. Estos campos se pueden devolver las filas, no solo la fila de marcador.  
  
 Si una aplicación llama **SQLGetDescField** para devolver el valor de cualquier campo que no se ha mencionado anteriormente, la biblioteca de cursores pasa la llamada al controlador.
