---
title: "Comprobación de coherencia | Documentos de Microsoft"
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
helpviewer_keywords:
- descriptors [ODBC], consistency checks
- consistency checks [ODBC]
ms.assetid: deb80efa-ad1f-4ea5-b334-9817cd279e5c
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2b661526c69d6dbe88e47d4eace4f13c603f5e16
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2017
---
# <a name="consistency-check"></a>Comprobación de coherencia
Se realiza una comprobación de coherencia con el controlador automáticamente cada vez que una aplicación establece el campo SQL_DESC_DATA_PTR del APD, descartar o IPD. Cada vez que este campo se establece, el controlador comprueba que el valor del campo SQL_DESC_TYPE y los valores aplicables para el campo SQL_DESC_TYPE en el mismo registro son válidos y coherentes.  
  
 El campo SQL_DESC_DATA_PTR de una IPD no se establece normalmente; Sin embargo, una aplicación puede hacerlo para forzar una comprobación de coherencia de los campos IPD. El valor que el campo SQL_DESC_DATA_PTR de la IPD se establece en no está almacenado realmente y no se puede recuperar mediante una llamada a **SQLGetDescField** o **SQLGetDescRec**; la configuración se realiza solo para forzar la comprobación de coherencia. No se puede realizar una comprobación de coherencia en un IRD.  
  
 Para obtener más información sobre la comprobación de coherencia, consulte [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).
