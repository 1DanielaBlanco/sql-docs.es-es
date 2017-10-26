---
title: Crear y terminar subprocesos | Documentos de Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- terminating threads [ODBC]
- threads [ODBC]
- multithreaded applications [ODBC]
ms.assetid: a2cf98ef-1c71-4742-8ee2-b53fd8e04333
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7a30fbe976ac3de550f8067cca82732631f698ac
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="creating-and-terminating-threads"></a>Crear y terminar subprocesos
Aplicaciones multiproceso que utilicen ODBC deben llamar a las funciones de biblioteca de tiempo de ejecución de Microsoft® Visual C++® **_beginthread** y **_endthread** (o **_beginthreadex** y **_endthreadex**) para crear y terminar subprocesos que llaman a Administrador de controladores ODBC. Si las aplicaciones llaman a las funciones de Microsoft Windows NT® **CreateThread** y **EndThread** en su lugar, funciones de memoria pérdidas se producen porque el Administrador de controladores y algunos controladores ODBC llaman a tiempo de ejecución de C no funcionará en un subproceso creado mediante una llamada a **CreateThread**. Para obtener más información, consulte la documentación de Microsoft Windows®.

