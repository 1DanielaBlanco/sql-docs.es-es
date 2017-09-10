---
title: "Preguntas más frecuentes sobre actualización e instalación (SQL Server R Services) | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 001e66b9-6c3f-41b3-81b7-46541e15f9ea
caps.latest.revision: 59
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: fa3cf5a36af30be655286a2e883d2408a6a3de90
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="upgrade-and-installation-faq-sql-server-r-services"></a>Preguntas más frecuentes sobre actualización e instalación (SQL Server R Services)

Este tema proporciona respuestas a algunas preguntas comunes acerca de la instalación de servicios de SQL Server de aprendizaje automático. Además se ocupa de las preguntas habituales acerca de las actualizaciones. Se producen algunos problemas sólo con las actualizaciones de versiones preliminares. Por lo tanto, se recomienda identificar la versión y edición primero y actualice a la versión más reciente o una versión de servicio tan pronto como sea posible.

**Se aplica a:** (en bases de datos) de servicios de aprendizaje de automático de SQL Server 2016 R Services, SQL Server de 2017

## <a name="performing-setup-for-the-first-time"></a>Llevar a cabo el programa de instalación para la primera vez

Siga los procedimientos para configurar [! INCLUDEssCurrent] y los componentes de R, como se describe aquí: 

+ [Configurar SQL Server R Services o Machine Learning Services en bases de datos](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)
+ [Configurar SQL Server 2017 con Python](../python/setup-python-machine-learning-services.md)
+ [Crear un R Server independiente](create-a-standalone-r-server.md)

Después de haber instalado SQL Server, para usar scripts de R o Python externos, debe realizar algunos pasos de configuración adicionales. Eso es porque la característica de ejecución de script externo no está habilitada de forma predeterminada, para reducir el área expuesta.

> [!NOTE]
> No utilice instrucciones de configuración que se publicaron antes de la versión pública de SQL Server 2016. El proceso de instalación completamente cambiado entre las versiones iniciales y la versión de lanzamiento oficial. 

### <a name="requirements-and-restrictions"></a>Requisitos y restricciones

Dependiendo de la compilación de servicios de R que se va a instalar, se podrían aplicar algunas de las siguientes limitaciones.

- En las versiones anteriores de SQL Server 2016 R Services, se requería la notación de tiene el formato 8.3 en la unidad que contiene el directorio de trabajo. Si instaló una versión preliminar, al actualizar a SQL Server 2016 Service Pack 1 debe quitar este requisito.

- No se puede instalar [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] en un clúster de conmutación por error. 

- En una máquina virtual de Azure, alguna configuración adicional puede ser necesario. Por ejemplo, deberá crear una excepción de firewall para permitir el acceso remoto.

- Instalación de en paralelo con otra versión de R, o con otras versiones de Revolution Analytics, no se admite.

- Ya no se admite la instalación nueva de ninguna versión preliminar de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] . Si está utilizando una versión preliminar, actualizar tan pronto como sea posible.

- Deshabilitar el antivirus antes de comenzar el programa de instalación. Una vez completada la instalación, se recomienda suspender en las carpetas utilizadas por SQL Server, preferiblemente todo el árbol de análisis de virus.

### <a name="licensing-agreements-for-unattended-installs"></a>Contratos de licencia para las instalaciones desatendidas

Si usa la línea de comandos para actualizar una instancia de SQL Server, asegúrese de que la línea de comandos incluye el nuevo parámetro de contrato de licencia, */IACCEPTROPENLICENSEAGREEMENT*. Si no se usa el argumento correcto puede hacer que el programa de instalación producirá un error.

### <a name="offline-installation-of-r-components-for-localized-version-of-sql-server"></a>Instalación sin conexión de los componentes de R para una versión localizada de SQL Server

Cuando se instalación R Services en un equipo que no tiene acceso a Internet, debe realizar dos pasos adicionales: debe descargar el instalador de componentes de R en una carpeta local antes de la instalación de SQL Server se ejecuta y debe editar el archivo de instalador para asegurarse de que la l correcto anguage está instalado.

El identificador de idioma utilizado para los componentes de R debe ser el mismo que el idioma de instalación de SQL Server, o la **siguiente** botón estará deshabilitado y no se puede completar el programa de instalación.

Para obtener más información, consulte [Instalación de componentes de R sin acceso a Internet](../../advanced-analytics/r-services/installing-ml-components-without-internet-access.md).

## <a name="post-installation-configuration"></a>Configuración posterior a la instalación

Para usar el aprendizaje automático con R o Python, se requiere alguna configuración adicional después de ejecutar el programa de instalación de SQL Server. Pueden requerirse pasos adicionales según el nivel de seguridad del servidor y de las bases de datos y la instancia de SQL Server. Revise estos pasos de las instrucciones de instalación para determinar si podría ser necesaria ninguna configuración adicional.

[Establecer la seguridad de Sql Server R Services en bases de datos](set-up-sql-server-r-services-in-database.md)

- La característica que admite la ejecución de scripts externos, como R o Python, está deshabilitada de forma predeterminada para la seguridad de base de datos y debe estar habilitada.

- Asegúrese de que las cuentas de trabajo que se utilizan por Launchpad para ejecutar R o Python tienen acceso a la instancia. Consulte [habilitar la autenticación implícita para el grupo de cuentas de Launchpad]

- Deberá habilitar el acceso remoto en el servidor o crear una regla de firewall que permita la comunicación entrante con SQL Server.

- Dependiendo de la carga de trabajo planeado, tendrá que optimizar el servidor para las tareas de aprendizaje automático. 

## <a name="upgrades-or-uninstallation"></a>Las actualizaciones o la desinstalación

Esta sección contiene instrucciones detalladas para escenarios de actualización específicos.

Ya no se admiten actualizaciones de versión preliminar de SQL Server 2016 R Services. Le recomendamos que desinstale y, a continuación, instalar una versión de lanzamiento tan pronto como sea posible.

### <a name="support-for-slipstream-upgrades"></a>Compatibilidad con actualizaciones de instalación integrada

Por instalación integrada se entiende la capacidad de aplicar una revisión o actualización a una instalación de instancia con errores con el propósito de reparar problemas existentes. La ventaja de este método es que el servidor SQL Server se actualiza al mismo tiempo que se realiza la instalación, lo que evita un reinicio independiente más adelante.

Si el servidor no tiene acceso a Internet, asegúrese de descargar al instalador de SQL Server. También debe descargar por separado las versiones que coinciden con los instaladores de componentes de R **antes de** comenzar el proceso de actualización. 

Para consultar las ubicaciones de descarga, consulte [Instalación de componentes de R sin acceso a Internet](installing-ml-components-without-internet-access.md).

Después de copiar todos los archivos de instalación en un directorio local, inicie la utilidad de instalación escribiendo SETUP.EXE en la línea de comandos.

- Use el argumento */UPDATESOURCE* para especificar la ubicación de un archivo local que contiene la actualización de SQL Server, como una versión Actualización acumulativa o Service Pack.

- Use el argumento */MRCACHEDIRECTORY* para especificar la carpeta que contiene los archivos CAB de los componentes de R.

Para obtener más información, consulte este blog del equipo de soporte técnico: [implementar R Services en equipos sin acceso a Internet](https://blogs.msdn.microsoft.com/sqlcat/2016/10/20/do-it-right-deploying-sql-server-r-services-on-computers-without-internet-access/)

### <a name="upgrading-r-components-offline"></a>Actualizar componentes de R sin conexión

Si instala o actualiza servidores que no están conectados a Internet, debe descargar manualmente una versión actualizada de los componentes de R antes de poder comenzar la actualización. Para obtener más información, consulte [Instalación de componentes de R sin acceso a Internet](../../advanced-analytics/r-services/installing-ml-components-without-internet-access.md).

### <a name="schedule-for-update-of-r-components"></a>Programación de actualización de componentes de R

A medida que se publiquen las revisiones o mejoras en SQL Server 2016, componentes de R se actualiza o se actualizan, si la instancia ya incluye la característica de R Services.

Si usas SQL Server 2017, se instalan automáticamente las actualizaciones de los componentes de R.

A partir de 2016 de diciembre, también es posible actualizar componentes de R a un ritmo más rápido que el ciclo de versiones de SQL Server, por *enlace* una instancia de R Services a la directiva de ciclo de vida de Software modernas. Actualmente se admiten solo para la actualización de instancias de 2016. Sin embargo, cuando se lanza una nueva versión del servidor de R, podrán realizar también para las instancias de 2017 actualizado.

Para más información, vea [Usar SqlBindR.exe para actualizar una instancia de R Services](../../advanced-analytics/r-services/use-sqlbindr-exe-to-upgrade-an-instance-of-r-services.md).

### <a name="upgrading-from-a-pre-release-version-of-sql-server-2016"></a>Actualizar desde una versión preliminar de SQL Server 2016

En general, no se admiten actualizaciones en contexto para las versiones preliminares.

Para instalar correctamente Servicios de R, debe desinstalar las versiones anteriores de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] y sus componentes de R relacionados, incluidos SQL Server 2016 CTP3, CTP3.1, CTP 3.2, RC0 o RC1.

Desinstalación de una versión preliminar puede ser compleja y requiere la ejecución de un script especial; se recomienda que póngase en contacto con el soporte técnico para obtener ayuda.

Las siguientes versiones se instalaron con versiones preliminares de SQL Server 2016.

| Versión | Compilar         |
|---------|---------------|
| CTP 3.0 | 13.0.xxx      |
| CTP 3.1 | 13.0.801.12   |
| CTP 3.2 | 13.0.900.73   |
| CTP 3.3 | 13.0.1000.281 |
| RC1     | 13.0.1200.242 |
| RC2     | 13.0.1300.275 |
| RC3     | 13.0.1400.361 |

Si tiene alguna duda sobre a qué versión está utilizando, ejecute `@@VERSION` desde SQL Server Management Studio.

### <a name="problems-with-setup-of-r-server-standalone"></a>Problemas con el programa de instalación de R Server (independiente)

Esta sección describen los problemas específicos de la instalación de Microsoft R Server (independiente) utilizando el programa de instalación de SQL Server 2016. Para los problemas más generales relacionados con actualizaciones de servidor de R, visite el sitio MSDN para [Microsoft R Server](https://msdn.microsoft.com/microsoft-r/).

#### <a name="failure-to-install-localized-versions"></a>Error al instalar las versiones localizadas

Al realizar sin conexión la instalación de servidor de R, versiones preliminares no le permiten utilizar los idiomas localizados.

En general, cuando el servidor no tiene acceso a Internet, antes de ejecutar el programa de instalación debe descargar todos los paquetes de instalación para el servidor de R y, a continuación, especifique la ubicación de los archivos durante la instalación.

Sin embargo, si el identificador de idioma asociado con el paquete del instalador no es el mismo que el idioma de instalación de SQL Server, cuando llegue a la página de la instalación de componentes de R, el **siguiente** botón está deshabilitado y no puede continuar con la instalación. Como alternativa, puede cambiar el nombre del paquete para utilizar un identificador de búsqueda de coincidencias.

Por ejemplo, podría ser el nombre de los paquetes de instalación `SRO_3.2.2.0_1031.cab`.
Para instalar el idioma 104 en SQL Server, cambie el nombre del archivo a `SRO_3.2.2.0_1041.cab`.

#### <a name="installing-r-services-and-r-server-standalone-on-the-same-computer"></a>Instalar servicios de R y R Server independiente en el mismo equipo

Por lo general, no se recomienda instalar R Services (In-Database) y R Server (independiente) en el mismo equipo. Sin embargo, si el servidor tiene una capacidad suficiente, R Server independiente puede resultar útil como una herramienta de desarrollo. También tendrá que utilizar las características de puesta en marcha de R Server y tener acceso a datos de SQL Server del servidor de R sin movimiento de datos.

Tenga en cuenta que si instala el servidor de R y R Services en el mismo equipo, se instalan dos conjuntos diferentes de las mismas bibliotecas de R: uno para su uso por la instancia de SQL server y otro para el desarrollo de usar o use R Server.

En versiones anteriores de SQL Server 2016, instalar R Server (independiente) y R Services (In-Database) al mismo tiempo podría hacer que el programa de instalación producirá un error con un mensaje de "acceso denegado". Este problema se corrigió en el Service Pack 1 para SQL Server 2016.

Si este error y que deba actualizar estas características, se recomienda que realice una instalación integrada de SQL Server 2016 con SP1. Hay dos maneras de resolver el problema, tanto de los que requieren desinstalar y volver a instalar.

1. Desinstale R Services (In-Database) y asegúrese de que se quitan las cuentas de usuario para SQLRUserGroup.

2. Reinicie el servidor y, a continuación, vuelva a instalar R Server (independiente).

3. Ejecutar SQL Server el programa de instalación una vez más, y esta vez seleccione **agregar características a SQL Server existente**.

4. Elija la instancia y, a continuación, seleccione la **R Services (In-Database)** opción para agregar.

En algunos casos, se producirá un error de este procedimiento borrar el error anterior en la instalación. En ese caso, debe desinstalar y volver a instalar los siguientes:

1. Desinstale R Services (In-Database) y R Server (independiente) al mismo tiempo.

2. Quite las cuentas de usuario local (SQLRUserGroup).

3. Reinicie el servidor.

4. Ejecute el programa de instalación de SQL Server y agregar sólo la función de R Services (In-Database). No seleccione **R Server (independiente)**.

## <a name="see-also"></a>Vea también

 [Introducción a SQL Server R Services](../r/getting-started-with-sql-server-r-services.md)

 [Introducción a Microsoft R Server independiente](../r/getting-started-with-microsoft-r-server-standalone.md)

