---
title: 'Paso 1: Conectar al origen de datos | Documentos de Microsoft'
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
helpviewer_keywords:
- application process [ODBC], connecting to data source
- data sources [ODBC], connections
- connecting to data source [ODBC], steps
ms.assetid: 84298664-4523-4149-b821-7b2e42c85281
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 05cf6b5d89b136be487951e1729a8e2cc40fae3d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="step-1-connect-to-the-data-source"></a>Paso 1: Conectar al origen de datos
Es el primer paso en cualquier aplicación para conectarse al origen de datos. Esta fase, incluidas las funciones que requiere, se muestra en la siguiente ilustración.  
  
 ![Conectarse al origen de datos en una aplicación ODBC](../../../odbc/reference/develop-app/media/pr11.gif "pr11")  
  
 El primer paso para conectarse al origen de datos es cargar el Administrador de controladores y asignar el identificador de entorno con **SQLAllocHandle**. Para obtener más información, consulte [asignar el entorno de controlar](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).  
  
 La aplicación, a continuación, registra la versión de ODBC a la que se ajusta mediante una llamada a **SQLSetEnvAttr** con el atributo de entorno SQL_ATTR_APP_ODBC_VER. Para obtener más información, consulte [declarar ODBC versión la aplicación](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md) y [compatibilidad con versiones anteriores y el cumplimiento de estándares](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
 A continuación, la aplicación asigna un identificador de conexión con **SQLAllocHandle** y se conecta al origen de datos con **SQLConnect**, **SQLDriverConnect**, o **SQLBrowseConnect**. Para obtener más información, consulte [asignar un identificador de conexión](../../../odbc/reference/develop-app/allocating-a-connection-handle-odbc.md) y [establecer una conexión](../../../odbc/reference/develop-app/establishing-a-connection.md).  
  
 La aplicación, a continuación, Establece los atributos de conexión, por ejemplo, si se debe confirmar manualmente las transacciones. Para obtener más información, consulte [atributos de conexión](../../../odbc/reference/develop-app/connection-attributes.md).
