---
title: Controlador Microsoft OLE DB para SQL Server | Microsoft Docs
description: Instalar y desinstalar el controlador de OLE DB para SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, uninstalling
- MSOLEDBSQL, installing
- MSOLEDBSQL, uninstalling
- Setup [OLE DB Driver for SQL Server]
- uninstalling OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], uninstalling OLE DB Driver for SQL Server
- installing OLE DB Driver for SQL Server
- OLE DB Driver for SQL Server, installing
- data access [OLE DB Driver for SQL Server], installing OLE DB Driver for SQL Server
- removing OLE DB Driver for SQL Server
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 10bf2ce673543cbad21bccdac35ac863647e910a
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "43019154"
---
# <a name="installing-ole-db-driver-for-sql-server"></a>Instalación del controlador OLE DB para SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

Para instalar al controlador OLE DB para SQL Server necesita a msoledbsql.msi instalador.
Ejecute al instalador y realice las selecciones preferidas. El controlador OLE DB para SQL Server puede ser instalado por en paralelo con versiones anteriores de los proveedores OLE DB de Microsoft.

El controlador OLE DB para los archivos de SQL Server (msoledbsql.dll, msoledbsqlr.rll) se instalan en `%SYSTEMROOT%\system32\` . Además, el x64 msoledbsql.msi instala los archivos binarios de 32 bits en `%SYSTEMROOT%\SysWOW64\`.

> [!NOTE]  
> Todas las configuraciones del Registro adecuados para el controlador OLE DB para SQL Server se realizan como parte del proceso de instalación.  

El controlador OLE DB para SQL Server encabezado y biblioteca de archivos (msoledbsql.h y msoledbsql.lib) se instalan en `%PROGRAMFILES%\Microsoft SQL Server\Client SDK\OLEDB\181\SDK`. Además, el x64 msoledbsql.msi instala los mismos archivos de `%PROGRAMFILES(x86)%\Microsoft SQL Server\Client SDK\OLEDB\181\SDK`.  

Puede distribuir el controlador OLE DB para SQL Server a través de msoledbsql.msi. Es posible que deba instalar el controlador de OLE DB para SQL Server al implementar una aplicación. Una manera de instalar varios paquetes en lo que al usuario le parece ser una instalación única es usar tecnología de encadenador y arranque. Para obtener más información, vea [Authoring a Custom Bootstrapper Package for Visual Studio 2005](http://go.microsoft.com/fwlink/?LinkId=115667) (Crear un paquete de arranque personalizado para Visual Studio 2005) y [Adding Custom Prerequisites](http://go.microsoft.com/fwlink/?LinkId=115668) (Agregar requisitos previos personalizados).  
  
El x64 msoledbsql.msi también instala la versión de 32 bits del controlador de OLE DB para SQL Server. Si la aplicación tiene como destino una plataforma distinta a la que se desarrolló, puede descargar las versiones de msoledbsql.msi para x64 y x86.

Cuando se invoca a msoledbsql.msi, solo los componentes cliente se instalan de forma predeterminada. Los componentes cliente son archivos que permiten la ejecución de una aplicación que se ha desarrollado mediante el controlador OLE DB para SQL Server. Para instalar también los componentes SDK, especifique `ADDLOCAL=All` en la línea de comandos. Por ejemplo:  

`msiexec /i msoledbsql.msi ADDLOCAL=ALL`  

## <a name="silent-install"></a>Instalación silenciosa  
 Si usa las opciones /passive, /qn, /qb o /qr con msiexec, también debe especificar IACCEPTMSOLEDBSQLLICENSETERMS=YES para indicar explícitamente que acepta los términos de la licencia de usuario final. Esta opción se debe especificar con todas las letras mayúsculas.  

## <a name="installing-ole-db-driver-for-sql-server-as-a-dependency"></a>Instalar el controlador OLE DB para SQL Server como una dependencia  
Es importante no desinstalar el controlador OLE DB para SQL Server hasta que se desinstalen todas las aplicaciones dependientes. Para proporcionar a los usuarios con una advertencia de que la aplicación depende de controlador de OLE DB para SQL Server, use la opción de instalación APPGUID en su MSI, como se indica a continuación:  

 `msiexec /i msoledbsql.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  

El valor pasado a APPGUID es su código de producto específico. Se debe crear un código de producto al usar Microsoft Installer para empaquetar su programa de instalación de la aplicación.
La opción APPGUID requiere ejecutando el programa de instalación desde un símbolo del sistema con privilegios elevados.

## <a name="see-also"></a>Ver también  
 [Compilación de aplicaciones con el controlador OLE DB para SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)   
