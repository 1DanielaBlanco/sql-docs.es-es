---
title: Función SQLSetScrollOptions | Documentos de Microsoft
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
apiname:
- SQLSetScrollOptions
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetScrollOptions
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC]
ms.assetid: 2a825ba7-7942-4c23-bcdb-c80dc12f8c86
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 79ab0c408748fcbea30fdc2c792e433db8a4309d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsetscrolloptions-function"></a>SQLSetScrollOptions (función)
**Conformidad**  
 Versión introdujo: Cumplimiento de estándares 1.0 de ODBC: en desuso  
  
 **Resumen**  
 En ODBC 3 *.x*, la función de ODBC 2.0 **SQLSetScrollOptions** se ha reemplazado por las llamadas a **SQLGetInfo** y **SQLSetStmtAttr**.  
  
> [!NOTE]  
>  Para obtener más información sobre lo que el Administrador de controladores se asigna esta función cuando una API ODBC 2 *.x* aplicación está trabajando con una aplicación ODBC 3 *.x* controladores, consulte [asignación de funciones en desuso](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)en Apéndice G: controlador directrices para la compatibilidad con versiones anteriores.  
  
> [!NOTE]  
>  Cuando se asigna el Administrador de controladores **SQLSetScrollOptions** para una aplicación que trabaja con una aplicación ODBC 3 *.x* controlador que no es compatible con **SQLSetScrollOptions**, el controlador El administrador establece la opción de instrucción SQL_ROWSET_SIZE, no el atributo de instrucción de SQL_ATTR_ROW_ARRAY_SIZE, para la *RowsetSize* argumento en **SQLSetScrollOption**. Como resultado, **SQLSetScrollOptions** no se puede usar una aplicación al capturar varias filas mediante una llamada a **SQLFetch** o **SQLFetchScroll**. Se puede utilizar solo cuando se captura varias filas mediante una llamada a **SQLExtendedFetch**.  
  
## <a name="remarks"></a>Comentarios  
 Si la aplicación se ejecutará en un sistema operativo de 64 bits, consulte [información ODBC de 64 bits](../../../odbc/reference/odbc-64-bit-information.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia de la API de ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Archivos de encabezado de ODBC](../../../odbc/reference/install/odbc-header-files.md)
