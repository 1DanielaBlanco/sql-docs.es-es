---
title: Conectarse a Sybase (SybaseToSQL) | Documentos de Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-sybase
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 524f95ef-10bd-497c-84ca-c06a0ae794fb
caps.latest.revision: "4"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ebf5f7f5c12a8a2e3af85ba2901e2348da92c30b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="connect-to-sybase-sybasetosql"></a>Conectarse a Sybase (SybaseToSQL)
Use la **conectar para Sybase** cuadro de diálogo para conectarse a la instancia de Sybase Adaptive Server Enterprise (ASE) que se va a migrar.  
  
Para tener acceso a este cuadro de diálogo, en la **archivo** menú, seleccione **conectar para Sybase**. Si se ha conectado anteriormente, el comando es **conectarse de nuevo a Sybase**.  
  
## <a name="options"></a>.  
**Proveedor**  
Seleccione cualquiera de lo proveedor instalado en el equipo para conectarse al servidor de Sybase.  
  
**Modo**  
Seleccione cualquier modo de conexión estándar o avanzada. En modo estándar, escriba o seleccione valores para el nombre del servidor, el puerto, el nombre de usuario y la contraseña. En el modo avanzado, proporcionar una cadena de conexión.  
  
**Nombre del servidor**  
Escriba o seleccione el nombre o dirección IP del servidor adaptable. El nombre del servidor predeterminado es el mismo que el nombre del equipo. Se trata de una opción de modo estándar.  
  
**Puerto del servidor**  
Si se usa un puerto no predeterminado para las conexiones a ASE, escriba el número de puerto. El número de puerto predeterminado es 5000. Se trata de una opción de modo estándar.  
  
**User name**  
Escriba el nombre de usuario que se usa para conectarse a ASE. Se trata de una opción de modo estándar.  
  
**Contraseña**  
Escriba la contraseña del nombre de usuario. Se trata de una opción de modo estándar.  
  
**Cadena de conexión**  
Escriba la cadena de conexión completa para la conexión a ASE.  
  
Las cadenas de conexión se componen de pares de nombre y valor de parámetro. Los nombres de los parámetros varían con el proveedor que se va a usar.  
  
**Parámetros de conexión de varios proveedores son los siguientes:**  
  
1.  Parámetros de conexión de **proveedor OLE DB**  
  
    |Configuración|Parámetro de Sybase 12,5|Parámetro de Sybase 15|  
    |-----------|-------------------------|-----------------------|  
    |Nombre del servidor|Nombre del servidor|Servidor|  
    |Puerto|Dirección de puerto del servidor|Puerto|  
    |Nombre de usuario|Id. de usuario|Id. de usuario|  
    |Contraseña|Contraseña|Contraseña|  
    |Proveedor|Proveedor|Proveedor|  
  
    Para Sybase ASE 12,5, una cadena de conexión de ejemplo es la siguiente:  
  
    `Server Name=sybserver;User ID=MyUserID;Password=MyP@$$word;Provider=Sybase.ASEOLEDBProvider;`  
  
    Para Sybase ASE 15, una cadena de conexión de ejemplo es la siguiente:  
  
    `Server=sybserver;User ID=MyUserID;Password=MyP@$$word;Provider=ASEOLEDB;Port=5000;`  
  
2.  Parámetros de conexión de **proveedor ODBC**  
  
    |Configuración|Parámetro de Sybase 12,5/15|  
    |-----------|-----------------------------|  
    |Nombre del controlador|controlador|  
    |Nombre del servidor|Servidor|  
    |Nombre de usuario|UID|  
    |Contraseña|PWD|  
    |Número de puerto|Puerto|  
  
    Para Sybase ASE 12,5 o 15, una cadena de conexión de ejemplo es la siguiente:  
  
    `driver=Adaptive Server Enterprise;Server=sybserver;uid=MyUserID;pwd=MyP@$$word;Port=5000;`  
  
3.  Parámetros de conexión de **proveedor de ADO.NET**  
  
    |Configuración|Parámetro de Sybase 12,5/15|  
    |-----------|-----------------------------|  
    |Nombre del servidor|Servidor|  
    |Nombre de usuario|UID|  
    |Contraseña|PWD|  
    |Número de puerto|Puerto|  
  
    Un ejemplo de la cadena de conexión para el proveedor de ADO.NET es como sigue:  
  
    `Server=sybserver;Port=5000;uid=MyUserID;pwd=MyP@$$word;`  
  
Para obtener más información, consulte la documentación de ASE.  
  
Se trata de una opción de modo avanzado.  
  
