---
title: SQLPrimaryKeys (controlador ODBC de Visual FoxPro) | Documentos de Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQLPrimaryKeys function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 8dbe2903-efdc-45e0-a079-9e357c5fd81b
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e0d7c874fe97f70f5e8d8096a4b03a2f064f2cb1
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2017
---
# <a name="sqlprimarykeys-visual-foxpro-odbc-driver"></a>SQLPrimaryKeys (controlador ODBC de Visual FoxPro)
> [!NOTE]  
>  Este tema contiene información específica del controlador ODBC de Visual FoxPro. Para obtener información general acerca de esta función, vea el tema correspondiente en [referencia de la API de ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Soporte técnico: completo  
  
 Conformidad de la API de ODBC: 2 de nivel  
  
 Devuelve los nombres de columna que componen la clave principal de una tabla. La implementación del controlador ODBC de Visual FoxPro de **SQLPrimaryKeys** se comporta como sigue:  
  
-   Omite la *szTableOwner* y *cbTableOwner* argumentos.  
  
-   Sólo funciona en los orígenes de datos que son [bases de datos](../../odbc/microsoft/visual-foxpro-terminology.md). El controlador devuelve el error "El controlador no admite esta función" si el origen de datos es un directorio de [libre tablas](../../odbc/microsoft/visual-foxpro-terminology.md).  
  
 Para obtener más información, consulte [SQLPrimaryKeys](../../odbc/reference/syntax/sqlprimarykeys-function.md) en el *referencia del programador de ODBC*.
