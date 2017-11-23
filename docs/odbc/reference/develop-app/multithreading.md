---
title: "Subprocesamiento múltiple | Documentos de Microsoft"
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
- ODBC drivers [ODBC], thread-safe
- thread-safe drivers [ODBC]
- multithreaded applications [ODBC]
ms.assetid: cdfebdf5-12ff-4e28-8055-41f49b77f664
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 86ef8e539354dce2d0cd349d75053b05a7ca59ca
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2017
---
# <a name="multithreading"></a>Subprocesamiento múltiple
En sistemas operativos multiproceso, controladores deben ser seguro para subprocesos. Es decir, debe ser posible que las aplicaciones utilizar el mismo identificador en más de un subproceso. Cómo lograrlo es específico del controlador, y es probable que los controladores serializará cualquier intento de utilizar el mismo identificador simultáneamente en dos subprocesos diferentes.  
  
 Las aplicaciones suelen usar varios subprocesos en lugar de procesamiento asincrónico. La aplicación crea un subproceso independiente, llama a una función ODBC en él y, a continuación, continúa el procesamiento en el subproceso principal. En lugar de tener que sondear continuamente la función asincrónica, como es el caso cuando se usa el atributo de instrucción de SQL_ATTR_ASYNC_ENABLE, la aplicación puede simplemente dejar que el subproceso recién creado Finalizar.  
  
 Las funciones que aceptan un identificador de instrucción se ejecutan en un subproceso pueden cancelarse mediante una llamada a **SQLCancel** con la misma instrucción controlar desde otro subproceso. Aunque los controladores no deben serializar el uso de **SQLCancel** de esta manera, no hay ninguna garantía de que la llamada a **SQLCancel** realmente se cancelará la función que se ejecuta en otro subproceso.
