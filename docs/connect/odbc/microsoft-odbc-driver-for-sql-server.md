---
title: Microsoft ODBC Driver for SQL Server | Documentos de Microsoft
ms.custom: ''
ms.date: 08/09/2017
ms.prod: sql
ms.prod_service: drivers
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 9f2ae91b-06af-4c9a-9d24-062df7bc4662
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7f7d037b0080b754e8a0ba65efc22a92ce43873b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="microsoft-odbc-driver-for-sql-server"></a>Controlador ODBC de Microsoft para SQL Server

[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

ODBC es la API de acceso de datos nativo principal para aplicaciones escritas en C y C++ para SQL Server. No hay un controlador ODBC para la mayoría de los orígenes de datos. Otros lenguajes que pueden usar ODBC incluyen COBOL, Perl, PHP y Python. ODBC se usa ampliamente en escenarios de integración de datos.

El controlador ODBC incluye herramientas como [ **sqlcmd** ](../../tools/sqlcmd-utility.md) y [ **bcp**](../../tools/bcp-utility.md). El **sqlcmd** utilidad le permite ejecutar instrucciones Transact-SQL, procedimientos del sistema y secuencias de comandos SQL. El **bcp** forma masiva copia los datos entre una instancia de Microsoft SQL Server y un archivo de datos en un formato que elija. Puede usar **bcp** para importar muchas filas nuevas en tablas de SQL Server o para exportar datos de tablas a archivos de datos.  

## <a name="code-example-in-c"></a>Ejemplo de código de C++

El siguiente ejemplo de C++ muestra cómo usar las API de ODBC para conectarse y tener acceso a una base de datos:

- [Ejemplo de código de C++, con ODBC](../../odbc/reference/sample-odbc-program.md)

## <a name="download"></a>Descargar

- ![Descarga-CTRL+MAYÚS+TAB-dentro de un círculo](../../ssdt/media/download.png)[para descargar el controlador ODBC](download-odbc-driver-for-sql-server.md)

## <a name="documentation"></a>Documentación

### <a name="features"></a>Características

- [Proveedores de almacén de claves personalizados](../../connect/odbc/custom-keystore-providers.md)
- [DSN y palabras clave de cadena de conexión y atributos](dsn-connection-string-attribute.md)
- [SQL Server Native Client](../../relational-databases/native-client/features/sql-server-native-client-features.md) (las características disponibles también se aplican, sin OLEDB, ODBC Driver for SQL Server)
- [Siempre usar cifrado](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)
- [Con Azure Active Directory](../../connect/odbc/using-azure-active-directory.md)
- [Utilizando la resolución de IP de red transparente](../../connect/odbc/using-transparent-network-ip-resolution.md)

### <a name="linux-and-macos"></a>Linux y Mac OS

- [Instalar el controlador](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)
- [Conexión a SQL Server](../../connect/odbc/linux-mac/connection-string-keywords-and-data-source-names-dsns.md)
- [Conectar con **bcp**](../../connect/odbc/linux-mac/connecting-with-bcp.md)
- [Conectar con **sqlcmd**](../../connect/odbc/linux-mac/connecting-with-sqlcmd.md)
- [Seguimiento de acceso a datos](../../connect/odbc/linux-mac/data-access-tracing-with-the-odbc-driver-on-linux.md)
- [Preguntas más frecuentes](../../connect/odbc/linux-mac/frequently-asked-questions-faq-for-odbc-linux.md)
- [Instalación del Administrador de controladores](../../connect/odbc/linux-mac/installing-the-driver-manager.md)
- [Problemas conocidos](../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)
- [Instrucciones de programación](../../connect/odbc/linux-mac/programming-guidelines.md)
- [Notas de la versión](../../connect/odbc/linux-mac/release-notes.md)
- [Compatibilidad con alta disponibilidad y recuperación ante desastres](../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md)
- [Mediante la autenticación integrada (Kerberos)](../../connect/odbc/linux-mac/using-integrated-authentication.md)

### <a name="windows"></a>Windows

- [Ejemplo de ejecución asincrónica (método de notificación)](../../connect/odbc/windows/asynchronous-execution-notification-method-sample.md)
- [Resistencia de conexión en el controlador Windows ODBC](../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md)
- [Agrupación de conexiones dependientes del controlador](../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md)
- [Características y cambios de comportamiento](../../connect/odbc/windows/features-of-the-microsoft-odbc-driver-for-sql-server-on-windows.md)
- [Notas de la versión](../../connect/odbc/windows/release-notes.md)
- [Requisitos del sistema, instalación y archivos del controlador](../../connect/odbc/windows/system-requirements-installation-and-driver-files.md)



## <a name="community"></a>Comunidad  
- [Blog del equipo de Microsoft ODBC Driver for SQL Server](http://blogs.msdn.com/sqlnativeclient/default.aspx)  
- [Foro para el acceso a los datos de SQL Server](http://social.technet.microsoft.com/Forums/en/sqldataaccess/threads)  
