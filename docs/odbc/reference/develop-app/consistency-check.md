---
title: Comprobación de coherencia | Documentos de Microsoft
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
- descriptors [ODBC], consistency checks
- consistency checks [ODBC]
ms.assetid: deb80efa-ad1f-4ea5-b334-9817cd279e5c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7be399dc7f8fda9d5223fa6a1749e1849bc9ee88
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="consistency-check"></a>Comprobación de coherencia
Se realiza una comprobación de coherencia con el controlador automáticamente cada vez que una aplicación establece el campo SQL_DESC_DATA_PTR del APD, descartar o IPD. Cada vez que este campo se establece, el controlador comprueba que el valor del campo SQL_DESC_TYPE y los valores aplicables para el campo SQL_DESC_TYPE en el mismo registro son válidos y coherentes.  
  
 El campo SQL_DESC_DATA_PTR de una IPD no se establece normalmente; Sin embargo, una aplicación puede hacerlo para forzar una comprobación de coherencia de los campos IPD. El valor que el campo SQL_DESC_DATA_PTR de la IPD se establece en no está almacenado realmente y no se puede recuperar mediante una llamada a **SQLGetDescField** o **SQLGetDescRec**; la configuración se realiza solo para forzar la comprobación de coherencia. No se puede realizar una comprobación de coherencia en un IRD.  
  
 Para obtener más información sobre la comprobación de coherencia, consulte [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).
