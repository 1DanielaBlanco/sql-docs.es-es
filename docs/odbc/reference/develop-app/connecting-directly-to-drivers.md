---
title: Conexión directa a controladores | Documentos de Microsoft
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
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], SqlDriverConnect
- SQLDriverConnect function [ODBC], connecting directly to drivers
- connecting to driver [ODBC], drivers
ms.assetid: f86e198f-a088-4401-9106-aa62a0eb8f6e
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f85b319ec264f9784953f12f93100660db614cbb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="connecting-directly-to-drivers"></a>Conectar directamente a los controladores
Tal y como se explicó en [elegir un origen de datos o el controlador](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md), anteriormente en esta sección, algunas aplicaciones no desean usar un origen de datos en absoluto. En su lugar, desean conectarse directamente a un controlador. **SQLDriverConnect** proporciona una manera para que la aplicación para conectarse directamente a un controlador sin especificar un origen de datos. Conceptualmente, un origen de datos temporal se crea en tiempo de ejecución.  
  
 Para conectarse directamente a un controlador, la aplicación especifica la **controlador** palabra clave en la cadena de conexión en lugar de la **DSN** palabra clave. El valor de la **controlador** palabra clave es la descripción del controlador devuelto por **SQLDrivers**. Por ejemplo, suponga que un controlador con la descripción del controlador de Paradox y requiere que el nombre de un directorio que contiene los archivos de datos. Para conectarse a este controlador, la aplicación puede usar cualquiera de las cadenas de conexión siguientes:  
  
```  
DRIVER={Paradox Driver};Directory=C:\PARADOX;  
DRIVER={Paradox Driver};  
```  
  
 Con la primera cadena, el controlador no necesitará información adicional. Con la segunda cadena, el controlador necesitaría solicitar el nombre del directorio que contiene los archivos de datos.
