---
title: "Ejemplo de diagnóstico del Administrador de controladores | Documentos de Microsoft"
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
- driver manager [ODBC], diagnostic messages
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: af8f2d35-d1bf-495c-af25-630654542b7d
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 23fac7bede1173a27b61da3940864b4842cc6ff3
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="driver-manager-diagnostic-example"></a>Ejemplo de diagnóstico del Administrador de controladores
El Administrador de controladores también puede generar mensajes de diagnóstico. Por ejemplo, si una aplicación pasa una opción de dirección no válida para **SQLDataSources**, el Administrador de controladores podría dar formato y devolver los valores siguientes de **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "HY103"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Driver Manager]Direction option out of range"  
```  
  
 Debido al error en el Administrador de controladores, agregar los prefijos para el mensaje de diagnóstico para su proveedor ([Microsoft]) y su identificador ([Administrador de controladores ODBC]).
