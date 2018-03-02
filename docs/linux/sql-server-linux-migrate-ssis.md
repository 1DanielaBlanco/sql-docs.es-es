---
title: Extraer, transformar y cargar datos en Linux con SSIS | Documentos de Microsoft
description: "Este artículo se describen SQL Server Integration Services (SSIS) para equipos con Linux"
author: leolimsft
ms.author: lle
ms.reviewer: douglasl
manager: craigg
ms.date: 01/09/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.workload: On Demand
ms.openlocfilehash: 87c28ec845a59ea13acce0585bc9b249f100a4a5
ms.sourcegitcommit: 9d0467265e052b925547aafaca51e5a5e93b7e38
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2018
---
# <a name="extract-transform-and-load-data-on-linux-with-ssis"></a>Extraer, transformar y cargar datos en Linux con SSIS

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Este artículo describe cómo ejecutar paquetes de SQL Server Integration Services (SSIS) en Linux. SSIS permite solucionar problemas de integración de datos complejos, extraer datos de varios orígenes y formatos, transformar y limpiar los datos y cargar los datos en varios destinos. 

Paquetes SSIS que se ejecutan en Linux pueden conectarse a Microsoft SQL Server que se ejecutan en Windows local o en la nube, en Linux o en Docker. También pueden conectarse a la base de datos de SQL Azure, almacenamiento de datos de SQL Azure, orígenes de datos ODBC, archivos sin formato y otros orígenes de datos, incluidos los orígenes ADO.NET, archivos XML y los servicios OData.

Para obtener más información acerca de las capacidades de SSIS, vea [SQL Server Integration Services](../integration-services/sql-server-integration-services.md).

## <a name="prerequisites"></a>Requisitos previos

Para ejecutar paquetes SSIS en un equipo Linux, primero tiene que instalar SQL Server Integration Services. SSIS no se incluye en la instalación de SQL Server para los equipos de Linux. Para obtener instrucciones de instalación, consulte [instalar SQL Server Integration Services](sql-server-linux-setup-ssis.md).

También deben tener un equipo de Windows para crear y mantener paquetes. Las herramientas de administración y diseño SSIS son aplicaciones de Windows que no están disponibles actualmente para equipos Linux. 

## <a name="run-an-ssis-package"></a>Ejecutar un paquete SSIS

Para ejecutar un paquete SSIS en un equipo Linux, haga lo siguiente:

1.  Copie el paquete SSIS en el equipo Linux.
2.  Ejecute el siguiente comando:
    ```
    $ dtexec /F \<package name \> /DE <protection password>
    ```

## <a name="run-an-encrypted-password-protected-package"></a>Ejecutar un paquete cifrado (protegidos con contraseña)
Hay tres métodos para ejecutar un paquete SSIS que se cifra con una contraseña:

1.  Establezca el valor de la variable de entorno `SSIS_PACKAGE_DECRYPT`, tal y como se muestra en el ejemplo siguiente:

    ```
    SSIS_PACKAGE_DECRYPT=test /opt/ssis/bin/dtexec /f package.dtsx
    ```

2.  Especifique el `/de[crypt]` opción para especificar la contraseña de forma interactiva, tal como se muestra en el ejemplo siguiente:

    ```
    /opt/ssis/bin/dtexec /f package.dtsx /de
    
    Enter decryption password:
    ```

3.  Especifique el `/de` opción para proporcionar la contraseña en la línea de comandos, tal como se muestra en el ejemplo siguiente. Este método no se recomienda ya que almacena la contraseña de descifrado con el comando del historial de comandos.

    ```
    opt/ssis/bin/dtexec /f package.dtsx /de test
    
    Warning: Using /De[crypt] <password> may store decryption password in command history.
    
    You can use /De[crypt] instead to enter interactive mode,
    or use environment variable SSIS_PACKAGE_DECRYPT to set decryption password.
    ```

## <a name="design-packages"></a>Diseñar paquetes

**Conectarse a orígenes de datos ODBC**. Con SSIS al actualizar los Linux CTP 2.1 y versiones posteriores, paquetes SSIS pueden usar conexiones de ODBC en Linux. Esta funcionalidad se ha probado con el servidor SQL Server y los controladores ODBC de MySQL, pero también se espera que funcione con cualquier controlador de ODBC Unicode que se ajusta a la especificación de ODBC. En tiempo de diseño, puede proporcionar un DSN o una cadena de conexión para conectarse a los datos ODBC; También puede utilizar la autenticación de Windows. Para obtener más información, consulte el [entrada del blog del anuncio de compatibilidad con ODBC en Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).

**Las rutas de acceso**. Proporcionar las rutas de acceso de estilo de Windows en los paquetes SSIS. SSIS en Linux no es compatible con las rutas de acceso basado en Linux, pero las rutas de acceso de estilo de Windows asigna a las rutas de acceso de estilo de Linux en tiempo de ejecución. A continuación, por ejemplo, SSIS en Linux asigna la ruta de acceso de estilo de Windows `C:\test` a la ruta de acceso basado en Linux `/test`.

## <a name="deploy-packages"></a>Implementar paquetes
Solo puede almacenar paquetes en el sistema de archivos en Linux en esta versión. La base de datos de catálogo de SSIS y el servicio SSIS heredado no están disponibles en Linux para el almacenamiento y la implementación del paquete.

## <a name="schedule-packages"></a>Programar paquetes
Puede utilizar el sistema de Linux, como las herramientas de programación `cron` para programar paquetes. No se puede usar el Agente SQL en Linux para programar la ejecución de paquetes en esta versión. Para obtener más información, consulte [paquetes SSIS de programación en Linux con cron](sql-server-linux-schedule-ssis-packages.md).

## <a name="limitations-and-known-issues"></a>Limitaciones y problemas conocidos

Para obtener información detallada sobre las limitaciones y problemas conocidos de SSIS en Linux, consulte [limitaciones y problemas conocidos de SSIS en Linux](sql-server-linux-ssis-known-issues.md).

## <a name="more-info-about-ssis-on-linux"></a>Para obtener más información acerca de SSIS en Linux

Para obtener más información sobre SSIS en Linux, consulte las siguientes entradas de blog:

-   [SSIS en Linux está disponible en SQL Server de 2017 CTP2.1](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/)
-   [ODBC es compatible con SSIS en Linux (actualización de CTP de SQL Server de 2017 2.1)](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/)

## <a name="more-info-about-ssis"></a>Para obtener más información acerca de SSIS

Microsoft SQL Server Integration Services (SSIS) es una plataforma para compilar soluciones de integración de datos de alto rendimiento, incluidos los paquetes de extracción, transformación y carga (ETL) para almacenamiento de datos. Para obtener más información sobre SSIS, vea [SQL Server Integration Services](/sql/integration-services/sql-server-integration-services).

SSIS incluye las siguientes características:
- las herramientas gráficas y asistentes para generar y depurar paquetes en Windows
- una serie de tareas para realizar funciones de flujo de trabajo, como las operaciones de FTP, ejecutar instrucciones SQL y enviar mensajes de correo electrónico
- una variedad de orígenes de datos y destinos para extraer y cargar datos
- una gama de transformaciones para limpiar, agregar, combinar y copiar datos
- interfaces de programación de aplicaciones (API) para ampliar SSIS con sus propios scripts personalizados y componentes

Para empezar a trabajar con SSIS, descargue la versión más reciente de [SQL Server Data Tools (SSDT)](../integration-services/ssis-how-to-create-an-etl-package.md).

Para obtener más información sobre SSIS, vea los siguientes artículos:
- [Obtener más información sobre SQL Server Integration Services](../integration-services/sql-server-integration-services.md)
- [Herramientas de administración y desarrollo de SQL Server Integration Services (SSIS)](../integration-services/integration-services-ssis-development-and-management-tools.md)
- [Tutoriales de SQL Server Integration Services](../integration-services/integration-services-tutorials.md)

## <a name="related-content-about-ssis-on-linux"></a>Contenido relacionado sobre SSIS en Linux
-   [Instalar SQL Server Integration Services (SSIS) en Linux](sql-server-linux-setup-ssis.md)
-   [Configurar SQL Server Integration Services en Linux con ssis-conf](sql-server-linux-configure-ssis.md)
-   [Limitaciones y problemas conocidos de SSIS en Linux](sql-server-linux-ssis-known-issues.md)
-   [Ejecución en Linux con cron del paquete de programación de SQL Server Integration Services](sql-server-linux-schedule-ssis-packages.md)
