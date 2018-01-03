---
title: "Función SQLTransact | Documentos de Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLTransact
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLTransact
helpviewer_keywords: SQLTransact function [ODBC]
ms.assetid: 496249e0-8eff-4c60-8358-5543bc3ead9c
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d4aa10349035d7a9d5d16c979701c39ead96e8f2
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="sqltransact-function"></a>SQLTransact (función)
**Conformidad**  
 Versión introdujo: Cumplimiento de estándares 1.0 de ODBC: en desuso  
  
 **Resumen**  
 En ODBC 3. *x*, la API ODBC 2*.x* función **SQLTransact** se ha reemplazado por **SQLEndTran**. Para obtener más información, consulte [SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
> [!NOTE]  
>  El atributo SQL_ASYNC_DBC_FUNCTION_ENABLE, que se introdujo en ODBC 3.8, no es compatible con **SQLTransact**. Las aplicaciones que usan una operación asincrónica en un identificador de conexión deben utilizar **SQLEndTran**.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de la API de ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Archivos de encabezado de ODBC](../../../odbc/reference/install/odbc-header-files.md)
