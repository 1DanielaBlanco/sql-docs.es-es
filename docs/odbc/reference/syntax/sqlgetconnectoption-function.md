---
title: Función SQLGetConnectOption | Documentos de Microsoft
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
- SQLGetConnectOption
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetConnectOption
helpviewer_keywords:
- SQLGetConnectOption function [ODBC]
ms.assetid: 59cde899-7957-4b5e-8677-f34d3b859bfd
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 079ab02fdc7ff44012c5c2a13a0fd369577ace0f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="sqlgetconnectoption-function"></a>SQLGetConnectOption (función)
**Conformidad**  
 Versión introdujo: Cumplimiento de estándares 1.0 de ODBC: en desuso  
  
 **Resumen**  
 En ODBC 3 *.x*, la API ODBC 2 *.x* función **SQLGetConnectOption** se ha reemplazado por **SQLGetConnectAttr**. Para obtener más información, consulte [SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md).  
  
> [!NOTE]  
>  Para obtener más información sobre lo que el Administrador de controladores se asigna esta función cuando una API ODBC 2 *.x* aplicación está trabajando con una aplicación ODBC 3 *.x* controladores, consulte [asignación de funciones en desuso](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)en Apéndice G: controlador directrices para la compatibilidad con versiones anteriores.  
  
> [!NOTE]  
>  No admite el atributo SQL_ASYNC_DBC_FUNCTION_ENABLE introducidas en ODBC 3.8 **SQLGetConnectOption**. Las aplicaciones que usan la operación asincrónica en un identificador de conexión deben utilizar **SQLGetConnectAttr**.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de la API de ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Archivos de encabezado de ODBC](../../../odbc/reference/install/odbc-header-files.md)
