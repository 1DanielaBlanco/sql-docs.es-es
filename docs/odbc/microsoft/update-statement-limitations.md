---
title: "Limitaciones de la instrucción de actualización | Documentos de Microsoft"
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
helpviewer_keywords:
- UPDATE statement limitations [ODBC]
- ODBC SQL grammar, UPDATE statement limitations
ms.assetid: 14700aac-e135-4dc0-9138-4b01224461d5
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 502315916781ae5624f94e099c0cd95c52ffe8a8
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2017
---
# <a name="update-statement-limitations"></a>Limitaciones de la instrucción de actualización
Para que el controlador de Paradox actualizar una tabla, la tabla debe tener un índice único (clave principal Paradox). Cuando se usa el controlador de Paradox sin necesidad de implementar el motor de base de datos de Borland, no es posible actualizar una tabla de Paradox.  
  
 No se admite el controlador de texto.  
  
 Cuando se utiliza el controlador de Microsoft Excel, es posible actualizar los valores, pero no se puede eliminar una fila de una tabla basada en una hoja de cálculo de Microsoft Excel. Como resultado, la instrucción UPDATE no se considera compatible oficialmente con el controlador de Microsoft Excel. Solo la instrucción INSERT se considera compatible.
