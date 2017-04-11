---
title: "Ver y leer los archivos de registro de instalaci&#243;n de SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ver registros"
  - "mostrar archivos de registro"
  - "programa de instalación [SQL Server], registros"
  - "archivos de registro de instalación [SQL Server]"
  - "instalación de SQL Server, registros"
  - "errores [SQL Server], programa de instalación"
  - "registros [SQL Server], programa de instalación"
ms.assetid: 9d77af64-9084-4375-908a-d90f99535062
caps.latest.revision: 54
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 54
---
# Ver y leer los archivos de registro de instalaci&#243;n de SQL Server
  Cada ejecución del programa de instalación crea archivos de registro con una nueva carpeta de registro con marca de tiempo en %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\130\Setup Bootstrap\Log\\. El formato del nombre de la carpeta de registro con marca de tiempo es AAAAMMDD_hhmmss. Cuando el programa de instalación se ejecuta en modo desatendido, los registros se crean en % temp%\sqlsetup*.log. Todos los archivos de la carpeta de registro se almacenan en el archivo Log\*.cab en su carpeta respectiva.  
  
 Una solicitud de instalación típica pasa por tres fases de ejecución:  
  
1.  Texto de reglas globales  
  
2.  Actualización de componentes  
  
3.  Acción solicitada por el usuario  
  
 En cada fase, el programa de instalación genera registros de detalle y de resumen con registros adicionales creados según corresponda. Se llama al programa de instalación al menos tres veces por acción de instalación solicitada por el usuario.  
  
 Los archivos de almacén de datos contienen una instantánea del estado de todos los objetos de configuración sometidos a seguimiento por el proceso de instalación y son útiles para solucionar errores de configuración. Se crean volcados de archivo XML para objetos de almacén de datos para cada fase de ejecución. Se guardan en su propia subcarpeta de registro debajo de la carpeta de registro con marca de tiempo, de la manera siguiente:  
  
-   Datastore_GlobalRules  
  
-   Datastore_ComponentUpdate  
  
-   Datastore  
  
 En las secciones siguientes se describen los archivos de registro de instalación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## Texto de resumen  
  
### Información general  
 Este archivo muestra los componentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que se detectaron durante la instalación, el entorno del sistema operativo, los valores de parámetros de línea de comandos, si se especifican, y el estado general de cada MSI/MSP que se ejecutó.  
  
 El registro se organiza en las secciones siguientes:  
  
-   Un resumen general de la ejecución  
  
-   Las propiedades y la configuración del equipo en el que se ejecutó el programa de instalación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instaladas anteriormente en el equipo  
  
-   Descripción de la versión de instalación y las propiedades del paquete de instalación  
  
-   Configuración de entrada en tiempo de ejecución proporcionada durante la instalación  
  
-   Ubicación del archivo de configuración  
  
-   Detalles de los resultados de la ejecución  
  
-   Reglas globales  
  
-   Reglas específicas del escenario de instalación  
  
-   Reglas con errores  
  
-   Ubicación del archivo de informe de reglas  
  
### Ubicación  
 Se encuentra en %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\130\Setup Bootstrap\Log\\.  
  
 Para encontrar errores en el archivo de texto de resumen, busque en el archivo usando las palabras clave "error" o "failed".  
  
## Summary_engine-base_AAAAMMDD_HHMMss.txt  
  
### Información general  
 El archivo base de registro de resumen es similar al archivo de resumen y se genera durante el flujo de trabajo principal.  
  
### Ubicación  
 Se encuentra en %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\130\Setup Bootstrap\Log\\<AAAAMMDD_HHMM>\\.  
  
## Summary_engine-base_AAAAMMDD_HHMMss_ComponentUpdate.txt  
  
### Información general  
 El archivo de registro de resumen de actualización de componentes es similar al archivo de resumen y se genera durante el flujo de trabajo de actualización de componentes.  
  
### Ubicación  
 Se encuentra en %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\130\Setup Bootstrap\Log\\<AAAAMMDD_HHMM>\\.  
  
## Summary_engine-base_\<VersionNumber>MMDD_HHMMss_GlobalRules.txt  
  
### Información general  
 El archivo de registro de resumen de reglas globales es similar al archivo de resumen y se genera durante el flujo de trabajo de reglas globales.  
  
### Ubicación  
 Se encuentra en %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\130\Setup Bootstrap\Log\\<AAAAMMDD_HHMM>\\.  
  
## Detail.txt  
  
### Información general  
 El archivo Detail.txt se genera durante el flujo de trabajo principal, como la instalación o la actualización, y proporciona los detalles de la ejecución. Los registros del archivo se generan en función del momento en que se invocó cada acción durante la instalación y muestran el orden que se ejecutaron las acciones, y sus dependencias.  
  
### Ubicación  
 Se encuentra en %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\130\Setup.  
  
 Bootstrap\Log\\<AAAAMMDD_HHMM>\Detail.txt.  
  
 Si se produce un error durante el proceso de instalación, la excepción o el error se registran al final de este archivo. Para encontrar los errores en este archivo, examine primero el final del archivo y, a continuación, realice una búsqueda en el mismo utilizando las palabras clave "error" o "exception".  
  
## Detail_ComponentUpdate.txt  
  
### Información general  
 El archivo Detail_ComponentUpdate.txt se genera durante el flujo de trabajo de actualización de componentes y es similar al archivo Detail.txt.  
  
### Ubicación  
 Se encuentra en %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\130\Setup Bootstrap\Log\\<AAAAMMDD_HHMM>\\.  
  
## Detail_GlobalRules.txt  
  
### Información general  
 El archivo Detail_GlobalRules.txt se genera durante la ejecución de las reglas globales y es similar al archivo Detail.txt.  
  
### Ubicación  
 Se encuentra en %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\130\Setup Bootstrap\Log\\<AAAAMMDD_HHMM>\\.  
  
## Archivos de registro de MSI  
  
### Información general  
 Los archivos de registro de MSI proporcionan detalles del proceso de paquete de instalación. Los genera el programa MSIEXEC durante la instalación del paquete especificado.  
  
 Tipos de archivos de registro de MSI:  
  
-   \<Feature>_\<Architecture>\_\<Interation>.log  
  
-   \<Feature>_\<Architecture>\_\<Language>\_\<Interation>.log  
  
-   \<Feature>_\<Architecture>\_\<Interation>\_\<workflow>.log  
  
### Ubicación  
 Los archivos de registro de MSI se encuentran en %Archivos de programa%\\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\130\Setup Bootstrap\Log\\<AAAAMMDD_HHMM>\\<Nombre\>.log.  
  
 Al final del archivo se encuentra un resumen de la ejecución que incluye el estado de corrección o error y las propiedades. Para encontrar el error en el archivo de MSI, busque "value 3" y, normalmente, los errores se mostrarán cerca de la cadena.  
  
## ConfigurationFile.ini  
  
### Información general  
 El archivo de configuración contiene la configuración de entrada que se proporciona durante la instalación. Se puede usar para reiniciar la instalación sin tener que especificar la configuración manualmente. Sin embargo, las contraseñas de las cuentas, los PID y algunos parámetros no se guardan en el archivo de configuración. La configuración se puede agregar al archivo o se puede proporcionar usando la línea de comandos o la interfaz de usuario del programa de instalación. Para obtener más información, vea [Instalar SQL Server 2016 mediante un archivo de configuración](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md).  
  
### Ubicación  
 Se encuentra en %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\130\Setup Bootstrap\Log\\<AAAAMMDD_HHMM>\\.  
  
## SystemConfigurationCheck_Report.htm  
  
### Información general  
 El informe de comprobación de la configuración del sistema contiene una descripción breve de cada regla ejecutada y el estado de ejecución.  
  
### Ubicación  
 Se encuentra en %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\130\Setup Bootstrap\Log\\<AAAAMMDD_HHMM>\\.  
  
## Vea también  
 [Instalar SQL Server 2016](../../database-engine/install-windows/install-sql-server-2016.md)  
  
  