---
title: Instalar los componentes de R y Python sin acceso a internet de aprendizaje de automático de SQL Server | Microsoft Docs
description: Sin conexión o desconectada R de Machine Learning y Python el programa de instalación en la instancia de SQL Server aislado.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/02/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 94aa87c0ecad8be94498bf5571e6e4b7ed7e1af9
ms.sourcegitcommit: 9528843359cc43b9c66afac363f542ae343266e9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "40437655"
---
# <a name="install-sql-server-machine-learning-r-and-python-on-computers-with-no-internet-access"></a>Instalar SQL Server de aprendizaje automático R y Python en equipos sin acceso a internet
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

De forma predeterminada, los instaladores de conecten a sitios de descarga de Microsoft para obtener necesarios y los componentes actualizados para aprendizaje automático en SQL Server. Si las restricciones de firewall impide que el instalador de llegar a estos sitios, puede usar un dispositivo conectado a internet para descargar archivos, transferir archivos a un servidor sin conexión y, a continuación, ejecute el programa de instalación.

Análisis en bases de datos constan de instancia del motor de base de datos, además de otros componentes de integración de R y Python, según la versión de SQL Server. 

+ SQL Server 2017 incluye R y Python. 
+ SQL Server 2016 es solo para R. 

En un servidor aislado, aprendizaje automático y las características específicas del lenguaje de R o Python se agregan a través de los archivos CAB. 

## <a name="sql-server-2017-offline-install"></a>Instalación sin conexión de SQL Server 2017

Para instalar SQL Server 2017 Machine Learning Services (R y Python) en un servidor aislado, comience por descargar la versión inicial de SQL Server y compatibilidad con los correspondientes archivos CAB de R y Python. Incluso si tiene previsto actualizar inmediatamente el servidor para usar la actualización acumulativa más reciente, primero debe instalarse una versión inicial.

> [!Note]
> SQL Server 2017 no tiene los service packs. Es la primera versión de SQL Server para usar la versión inicial como la única línea de base, con el mantenimiento de las actualizaciones acumulativas solo. 

### <a name="1---download-2017-cabs"></a>1: descargar archivos CAB de 2017

En un equipo que tiene una conexión a internet, descargue los archivos CAB que proporciona funciones de R y Python para la versión inicial y los medios de instalación de SQL Server 2017. 

Versión  |Vínculo de descarga  |
---------|---------------|
Microsoft R Open     |[SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
Microsoft R Server      |[SRS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851507)|
Apertura de Python de Microsoft     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502) |
Servidor de Python de Microsoft    |[SPS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851508) |

###  <a name="2---get-sql-server-2017-installation-media"></a>2 - obtener medios de instalación de SQL Server 2017

1. En un equipo que tiene una conexión a internet, descargue el [programa de instalación de SQL Server 2017](https://www.microsoft.com/sql-server/sql-server-downloads). 

2. Haga doble clic en el programa de instalación y elija el **descargar medios** tipo de instalación. Con esta opción, el programa de instalación crea un archivo .iso (o .cab) local que contiene el medio de instalación.

   ![Elegir tipo de instalación de los medios de descarga](media/offline-download-tile.png "descargar archivos multimedia")

## <a name="sql-server-2016-offline-install"></a>Instalación sin conexión de SQL Server 2016

Análisis en bases de datos de SQL Server 2016 es sólo R, con sólo dos CAB los archivos de paquetes de productos y la distribución de Microsoft de R de código abierto, respectivamente. Comience por instalar cualquiera de estas versiones: RTM, Service Pack 1, SP 2. Una vez que una instalación básica está en su lugar, se pueden aplicar las actualizaciones acumulativas como paso siguiente.

En un equipo que tiene una conexión a internet, descargue los archivos CAB que se usa el programa de instalación para instalar el análisis en bases de datos en SQL Server 2016. 

### <a name="1---download-2016-cabs"></a>1: descargar archivos CAB de 2016

Versión  | Microsoft R Open | Microsoft R Server |
---------|-----------------|---------------------|
**SQL Server 2016 RTM**     | [SRO_3.2.2.803_1033.cab](https://go.microsoft.com/fwlink/?LinkId=761266) |[SRS_8.0.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=735051) |
**SQL Server 2016 SP 1**     | [SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879) |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881) | 
**SQL Server 2016 Service Pack 2**  |[SRO_3.2.2.20000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866039) |[SRS_8.0.3.20000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866038) |

### <a name="2---get-sql-server-2016-installation-media"></a>2 - obtener medios de instalación de SQL Server 2016

Puede instalar SQL Server 2016 RTM, Service Pack 1 o Service Pack 2 como la primera instalación en el equipo de destino. Cualquiera de estas versiones puede aceptar una actualización acumulativa.

Es una manera de obtener un archivo .iso que contiene el medio de instalación a través de [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/). Inicie sesión y, a continuación, utilice el **descargas** vínculo para buscar la versión de SQL Server 2016 que desea instalar. La descarga está en forma de un archivo .iso, que puede copiar en el equipo de destino para una instalación sin conexión.

## <a name="transfer-files"></a>Transferencia de archivos

Copie los medios de instalación de SQL Server (.iso o .cab) y los archivos de análisis en bases de datos CAB en el equipo de destino. Coloque los archivos CAB y el archivo de medios de instalación en la misma carpeta en el equipo de destino, como **descargas** o la carpeta temp * % del usuario del programa de instalación.

Captura de pantalla siguiente muestra los archivos CAB de SQL Server 2017 e ISO. Descargas de SQL Server 2016 tienen un aspecto distintas: es el nombre de archivo menos archivos (sin Python) y los medios de instalación para 2016.

![Lista de archivos que se transferirá](media/offline-file-list.png "lista de archivos")

## <a name="run-setup"></a>Ejecute el programa de instalación

Al ejecutar el programa de instalación de SQL Server en un equipo conectado a internet, el programa de instalación agrega un **instalación sin conexión** paginar en el Asistente para que pueda especificar la ubicación de los archivos .cab que copió en el paso anterior.

1. Para comenzar la instalación, haga doble clic en el archivo .iso o .cab para tener acceso a los medios de instalación. Debería ver el **setup.exe** archivo.

2. Haga clic en **setup.exe** y ejecutar como administrador.

3. Cuando el Asistente para la instalación muestra la página de licencia para componentes de R o Python de código abierto, haga clic en **Accept**. Aceptación de términos de licencia le permite continuar con el paso siguiente.

4. Cuando llegue a la **instalación sin conexión** página **ruta de instalación**, especifique la carpeta que contiene los archivos CAB que copió anteriormente.

   ![Página del Asistente para la selección de carpeta cab](media/screenshot-sql-offline-cab-page.png "carpeta CAB")

5. Continuar siguientes las indicaciones en pantalla para completar la instalación.

## <a name="post-install-configuration"></a>Configuración posterior a la instalación

Una vez finalizada la instalación, reinicie el servicio y, a continuación, configure el servidor para habilitar la ejecución del script:

+ [Habilitar la ejecución de scripts externos (SQL Server 2017)](sql-machine-learning-services-windows-install.md#bkmk_enableFeature)
+ [Habilitar la ejecución de scripts externos (SQL Server 2016)](sql-r-services-windows-install.md#bkmk_enableFeature)

Una instalación sin conexión inicial de SQL Server 2017 Machine Learning Services o SQL Server 2016 R Services requiere la misma configuración que una instalación en línea:

+ [Comprobar la instalación](sql-machine-learning-services-windows-install.md#verify-installation) (para SQL Server 2016, haga clic en [aquí](sql-r-services-windows-install.md#verify-installation)).
+ [Configuración adicional según sea necesario](sql-machine-learning-services-windows-install.md#additional-configuration) (para SQL Server 2016, haga clic en [aquí](sql-r-services-windows-install.md#bkmk_FollowUp)).

<a name="slipstream-upgrades"></a>

## <a name="slipstream-upgrades"></a>Actualizaciones de instalación integrada

Por instalación integrada se entiende la capacidad de aplicar una revisión o actualización a una instalación de instancia con errores con el propósito de reparar problemas existentes. La ventaja de este método es que el servidor SQL Server se actualiza al mismo tiempo que se realiza la instalación, lo que evita un reinicio independiente más adelante.

Cuando un servidor no tiene acceso a Internet, se aplican las actualizaciones del servicio mediante la descarga de un servidor SQL Server actualizado instalador y las versiones correspondientes de los archivos CAB específicos del idioma. 

1. Comience con una instancia de la línea base. Acerca de estas versiones de SQL Server, se admiten actualizaciones de instalación integrada:

  + Versión inicial de SQL Server 2017
  + Versión inicial de SQL Server 2016
  + Service Pack 1 de SQL Server 2016
  + SQL Server 2016 Service Pack 2

2. Obtenga una versión actualizada del instalador de SQL Server para una determinada actualización acumulativa. Es cualquier actualización de las características de machine learning (R y Python) junto con una actualización acumulativa de la instancia del motor de base de datos subyacente.

  + [Actualizaciones de SQL Server 2016](https://sqlserverupdates.com/sql-server-2016-updates/)
  + [Actualizaciones de SQL Server 2017](https://sqlserverupdates.com/sql-server-2017-updates/)

3. Obtener archivos CAB correspondientes para R y Python. Para obtener vínculos de descarga, vea [CAB descargas para las actualizaciones acumulativas en el análisis en bases de datos de SQL Server en instancias](sql-ml-cab-downloads.md).

4. Coloque todos los archivos en la misma carpeta, ejecute el programa de instalación. Durante la instalación, deberá elegir la ubicación de carpeta para los archivos CAB actualizados.

## <a name="next-steps"></a>Pasos siguientes

Para comprobar el estado de instalación de la instancia y corregir los problemas comunes, consulte [informes personalizados para SQL Server R Services](../r/monitor-r-services-using-custom-reports-in-management-studio.md).

Para obtener ayuda con todos los mensajes no conocidos o las entradas del registro, consulte [actualización e instalación preguntas más frecuentes - Machine Learning Services](../r/upgrade-and-installation-faq-sql-server-r-services.md).

