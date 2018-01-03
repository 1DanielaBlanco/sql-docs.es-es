---
title: Las aplicaciones verticales | Documentos de Microsoft
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
helpviewer_keywords:
- interoperability [ODBC], vertical applications
- vertical applications [ODBC]
- interoperability [ODBC], levels
ms.assetid: d50ea3e6-7a9e-4fb6-8cd8-1d429d2f7b3c
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 81f0b9b75a1431b071e20425ba7f0386fe7a1b00
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="vertical-applications"></a>Aplicaciones verticales
Aplicaciones verticales suelen realizan una tarea bien definida en un DBMS único. Por ejemplo, una aplicación de entrada de pedidos realiza un seguimiento de los pedidos de una empresa. Lo que estos tipos de aplicaciones tienen en común es que el esquema de base de datos normalmente se diseña el desarrollador de aplicaciones y, mientras que la aplicación puede funcionar con un número de diferentes DBMS, funciona con un DBMS único para un único cliente.  
  
 Debido a las aplicaciones verticales suelen requieran cierta funcionalidad, como cursores desplazables o de las transacciones, rara vez admiten todos los DBMS. En su lugar, tienden a ser muy interoperable entre un conjunto limitado de DBMS. Por lo general, los desarrolladores de aplicaciones vertical eligen admitir los DBMS que representan una gran parte del mercado y pasar por alto el resto. Incluso puede optar por la compatibilidad de controladores específicos para los DBMS para reducir las pruebas y los costes de soporte de producto.  
  
 Dado que las aplicaciones verticales pueden admitir un conjunto conocido de DBMS, a veces contienen código específico del controlador o específicos del DBMS. Sin embargo, este código es mejor guardar en un mínimo porque requiere tiempo adicional para mantener.
