---
title: Solución de problemas de una instalación de Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e2536f7f-d90c-4571-9ffd-6bbfe69018d6
caps.latest.revision: 9
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 447cab185ce02b83b25af160421391ed73bb7cf6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37248345"
---
# <a name="troubleshoot-a-reporting-services-installation"></a>Solucionar problemas en una instalación de Reporting Services
  Si no puede instalar [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] debido a los errores que se producen durante la instalación, siga las instrucciones que se explican en este tema para abordar las condiciones que probablemente ocasionen esos errores.  
  
 Para obtener la información más reciente sobre los problemas en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], consulte [Reporting Services SQL Server 2012 consejos, trucos y solución de problemas](http://go.microsoft.com/fwlink/?LinkId=221297)  
  
 Para obtener información sobre otros errores y problemas relacionados con [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] vea [SSRS: Solucionar problemas y errores.](http://social.technet.microsoft.com/wiki/contents/articles/ssrs-troubleshooting-issues-and-errors.aspx)  
  
 Examine las [Notas de la versión en línea](http://go.microsoft.com/fwlink/?linkid=236893) en caso de que el problema que tiene se describa en las notas de la versión.  
  
 Este tema contiene la información siguiente:  
  
-   [Compruebe los registros de instalación](#bkmk_setuplogs)  
  
-   [Comprobación de requisitos previos](#bkmk_prereq)  
  
-   [Solucionar problemas relacionados con las instalaciones en modo de SharePoint](#bkmk_tshoot_sharepoint)  
  
-   [Solucionar problemas relacionados con las instalaciones en modo nativo](#bkmk_tshoot_native)  
  
-   [Recursos adicionales](#bkmk_additional)  
  
##  <a name="bkmk_setuplogs"></a> Examinar los registros de instalación  
 Los errores de instalación se escriben en archivos de registro en la carpeta **Archivos de programa\Microsoft SQL Server\110\Setup Bootstrap\Log** . Se crea una subcarpeta cada vez que se ejecuta el programa de instalación. El nombre de la subcarpeta indica la hora y la fecha en que se ejecutó el programa de instalación. Para obtener instrucciones sobre cómo ver los archivos de registro de instalación, vea [Ver y leer los archivos de registro de instalación de SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).  
  
-   Los archivos de registro incluyen una recopilación de archivos.  
  
-   Abra el archivo *_summary.txt para ver información del producto, componente e instancia.  
  
-   Abra el archivo *_errorlog.txt para ver información de los errores generados durante la instalación.  
  
-   Abra el archivo *_RS\_\*_ComponentUpdateSetup.log para ver información sobre la instalación de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
##  <a name="bkmk_prereq"></a> Comprobar los requisitos previos  
 El programa de instalación comprueba si se cumplen los requisitos previos automáticamente. Sin embargo, al solucionar problemas de instalación, es útil saber qué requisitos comprueba dicho programa.  
  
-   Los requisitos relacionados con las cuentas que se necesitan para ejecutar el programa de instalación incluyen la pertenencia al grupo local de administradores. El programa de instalación debe tener permiso para agregar archivos y valores del Registro, crear grupos de seguridad locales y establecer permisos fijos. Si está instalando una configuración predeterminada, el programa de instalación debe tener permiso para crear una base de datos del servidor de informes en la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en la que esté efectuando la instalación.  
  
-   El sistema operativo debe admitir HTTP.SYS 1.1.  
  
-   El servicio HTTP debe estar habilitado y ejecutándose.  
  
-   El Coordinador de transacciones distribuidas (DTC) se debe estar ejecutando si también está instalando el servicio Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Authz.dll debe encontrarse en la carpeta System32.  
  
 El programa de instalación ya no comprueba Internet Information Services (IIS) ni [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] requiere MDAC 2.0 y [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] versión 2.0; el programa de instalación los instalará si no están en el equipo.  
  
##  <a name="bkmk_tshoot_sharepoint"></a> Solucionar los problemas de las instalaciones en modo de SharePoint  
  
-   [El Administrador de configuración de Reporting Services no se inicia](#bkmk_configmanager_notstart)  
  
-   [No se ve el servicio SQL Server Reporting Services en Administración Central de SharePoint después de instalar SQL Server 2012 SSRS en modo de SharePoint](#bkmk_no_ssrs_service)  
  
-   [Los cmdlets de PowerShell de Reporting Services no están disponibles y no se reconocen los comandos](#bkmk_cmdlets_not_recognized)  
  
-   [Aparece un mensaje de error que indica que la dirección URL no está configurada](#bkmk_URL_not_configured)  
  
-   [El programa de instalación produce errores en un equipo con SharePoint instalado pero que no está configurado](#bkmk_sharepoint_not_confiugred)  
  
-   [La página Administración central de SharePoint está en blanco](#bkmk_central_admin_blank)  
  
-   [Ve un mensaje de error al intentar crear un nuevo informe del Generador de informes](#bkmk_reportbuilder_newreport_error)  
  
-   [Ve un mensaje de error que indica que RS_SHP no se admite con PREPAREIMAGE](#bkmk_RS_SHP_notsupported)  
  
###  <a name="bkmk_configmanager_notstart"></a> El Administrador de configuración de Reporting Services no se inicia  
 **Descripción** : este problema se debe al diseño de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] está ahora estructurado para la arquitectura de servicios de SharePoint. El Administrador de configuración ya no es necesario para configurar y administrar [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en modo de SharePoint.  
  
 **Solución alternativa:** use la Administración central de SharePoint para configurar un servidor de informes en modo de SharePoint. Para obtener más información, vea [Administrar una aplicación de servicio de SharePoint para Reporting Services](../../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md).  
  
###  <a name="bkmk_no_ssrs_service"></a> No se ve el servicio SQL Server Reporting Services en Administración Central de SharePoint después de instalar SQL Server 2012 SSRS en modo de SharePoint  
 **Descripción:** si después de instalar correctamente [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en modo de SharePoint y el [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] complementos para SharePoint 2010, no ve "SQL Server Reporting Services" en los dos siguientes menús, a continuación, el [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] no se ha registrado service:  
  
-   Administración central de SharePoint 2010 -> 'Administración de aplicaciones' -> página 'Administrar servicios en el servidor'  
  
-   Administración central de SharePoint 2010 -> ""Administración de aplicaciones" -> "Administrar aplicaciones de servicio" ->menú "Nuevo"  
  
 **Solución alternativa:** para registrar e iniciar [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint Services, realice los pasos siguientes:  
  
1.  En el equipo que ejecuta Administración central de SharePoint 2010  
  
    1.  Abra SharePoint 2010 Management Shell con privilegios de administrador. Haga clic con el botón secundario en el icono y haga clic en 'Ejecutar como administrador'. Ejecute los tres siguientes cmdlets desde el shell:  
  
    2.  ```  
        Install-SPRSService  
        ```  
  
    3.  ```  
        Install-SPRSServiceProxy  
        ```  
  
    4.  ```  
        Get-SPServiceInstance -all |where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
        ```  
  
2.  Compruebe el [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] servicio muestra el estado como "**iniciado**" en la página:-> de Administración Central de SharePoint 2010 "**Application Management**"->"**administrar servicios en Servidor**"  
  
###  <a name="bkmk_cmdlets_not_recognized"></a> Los cmdlets de PowerShell de Reporting Services no están disponibles y no se reconocen los comandos  
 **Descripción** : al intentar ejecutar un cmdlet de PowerShell de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , aparece un mensaje de error similar al siguiente:  
  
-   El término “Install-SPRSServiceInstall-SPRSService” **no se reconoce** como nombre de un cmdlet, función, archivo de script o programa ejecutable. Compruebe si escribió correctamente el nombre o, si incluyó una ruta de acceso, compruebe que dicha ruta es correcta e inténtelo de nuevo. En la línea:1 car:39+ Install-SPRSServiceInstall-SPRSService <<<<    + CategoryInfo          : ObjectNotFound: (Install-SPRSServiceInstall-SPRSService:String) [], CommandNotFoundExcep  
  
 **Solución alternativa:** complete uno de los pasos siguientes:  
  
-   Ejecute el complemento [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] para productos de SharePoint. **rssharepoint.msi**.  
  
-   Instale [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en modo de SharePoint desde los medios de instalación de SQL Server.  
  
 **Nota:** si el **Shell de administración de SharePoint 2013** está abierto cuando completa una de las soluciones alternativas, cierre y vuelva a abrir el shell de administración.  
  
 Para obtener más información, vea:  
  
-   [Dónde encontrar el complemento Reporting Services para Productos de SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
-   [Instalar el modo de SharePoint de Reporting Services para SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)  
  
-   [Instalar el modo de SharePoint de Reporting Services para SharePoint 2013](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md)  
  
###  <a name="bkmk_URL_not_configured"></a> Aparece un mensaje de error que indica que la dirección URL no está configurada  
 **Descripción:** el mensaje de error que aparece es similar al siguiente:  
  
 Esta funcionalidad de SQL Server Reporting Services (SSRS) no se admite. Use Administración central para comprobar y corregir los problemas siguientes: •No se ha configurado una dirección URL del servidor de informes. Use la página de integración de SSRS para establecerla. •El proxy de aplicación de servicios de SSRS no está configurado. Use las páginas de aplicación de servicios de SSRS para configurar el proxy. •La aplicación de servicios de SSRS no se ha asignado a esta aplicación web. Use las páginas de aplicación de servicios de SSRS para asociar el proxy de aplicación de servicios de SSRS al Grupo de proxy de aplicación para esta aplicación web.  
  
 **Solución alternativa:** el mensaje de error contiene tres pasos sugeridos para corregir este problema. La primera sugerencia en el mensaje "No se ha configurado una dirección URL del servidor de informes..." es pertinente cuando se integra con la versión del servidor de informes anterior a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. La configuración de SharePoint para las versiones del servidor de informes anteriores se completa en la página **Configuración de aplicación general** , mediante **SQL Server Reporting Services (2008 y 2008 R2)**.  
  
 **Más información:** este mensaje de error aparecerá si intenta usar cualquier funcionalidad de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] que requiere una conexión al servicio de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Esto incluye:  
  
-   Abrir el Generador de informes de SQL Server desde una biblioteca de documentos de SharePoint.  
  
-   Administrar suscripciones.  
  
-   Administrar una aplicación de servicio.  
  
###  <a name="bkmk_sharepoint_not_confiugred"></a> El programa de instalación produce errores en un equipo con SharePoint instalado pero que no está configurado  
 **Descripción** : si selecciona instalar el modo SharePoint de Reporting Services en un equipo que tiene SharePoint instalado pero no configurado, verá un mensaje similar al siguiente y la instalación se detendrá:  
  
 El programa de instalación de SQL Server ha dejado de funcionar  
  
 **Solución alternativa:** configure SharePoint y, a continuación, ejecute la instalación de SQL Server.  
  
 **Más información:** al instalar [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en una instalación de SharePoint existente, el programa de instalación intenta instalar e iniciar el servicio de SharePoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Si SharePoint no está configurado, la instalación del servicio da error e impide que el programa de instalación se complete.  
  
###  <a name="bkmk_central_admin_blank"></a> La página Administración central de SharePoint está en blanco  
 **Descripción** : pudo instalar SharePoint 2010 correctamente, sin errores de instalación. Sin embargo, al ir a Administración Central, solo ve una página en blanco:  
  
 **Solución alternativa:** este problema no es específico de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , sino que está relacionado con la configuración de permisos de la instalación de SharePoint global. La siguiente es una lista de sugerencias:  
  
-   Revise el tema de SharePoint en entornos de desarrollo. [Cómo configurar el entorno de desarrollo para SharePoint 2010 en Windows Vista, Windows 7 y Windows Server 2008](http://msdn.microsoft.com/library/ee554869\(office.14\).aspx)  
  
-   Revisar la exposición en el foro: [Administración central devuelve una página en blanco después de la instalación en Windows 7](http://social.technet.microsoft.com/Forums/en/sharepoint2010setup/thread/a422a3c8-39f6-4b9e-988a-4c4d1e745694)  
  
-   La cuenta de servicio que está utilizando para los servicios de SharePoint, como el Servicio de Administración central de SharePoint 2010, debería tener los privilegios de administrador en el sistema operativo local.  
  
###  <a name="bkmk_reportbuilder_newreport_error"></a> Ve un mensaje de error al intentar crear un nuevo informe del Generador de informes  
 **Descripción:** ve un mensaje de error similar al siguiente al intentar crear un informe del Generador de informes dentro de una biblioteca de documentos:  
  
 No se admite esta funcionalidad porque una aplicación de servicio de SQL Server Reporting Services no existe o una dirección URL del servidor de informes no se ha configurado en Administración central.  
  
 **Solución alternativa:** compruebe que tiene una aplicación de servicio [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] y que está configurada correctamente. Para obtener más información, vea la sección "crear una aplicación de servicio de Reporting Services" en [instalar Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)  
  
###  <a name="bkmk_RS_SHP_notsupported"></a> Ve un mensaje de error que indica que RS_SHP no se admite con PREPAREIMAGE  
 **Descripción:** al intentar ejecutar PREPAREIMAGE para [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , aparece un mensaje de error similar al siguiente:  
  
 'La característica especificada 'RS_SHP' no se admite al ejecutar la acción PREPAREIMAGE, dado que no es compatible con SysPrep. Quite las características que no son compatibles con SysPrep y ejecute el programa de instalación de nuevo."  
  
 **Solución alternativa:** no hay ninguna. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] no admite SYSPREP (PREPAREIMAGE). [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] no admite SYSPREP.  
  
##  <a name="bkmk_tshoot_native"></a> Solucionar problemas con las instalaciones en modo nativo  
  
###  <a name="PerfCounters"></a> Los contadores de rendimiento no son visibles después de actualizar a Windows Vista o Windows Server 2008  
 Si actualiza el sistema operativo a [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] o [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] en un equipo que ejecuta [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], los contadores de rendimiento de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] no se establecerán después de la actualización.  
  
#### <a name="to-reinstate-reporting-services-performance-counters"></a>Para restablecer los contadores de rendimiento de Reporting Services  
  
1.  Elimine las claves del Registro siguientes:  
  
    -   **HKLM\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service**  
  
    -   **HKLM\SYSTEM\CurrentControlSet\Services\MSRS 2011 Windows Service**  
  
2.  Abra una ventana del símbolo del sistema y escriba el comando siguiente en el símbolo del sistema:  
  
    -   **ejecute \< ** *directorio de .NET 2.0 Framework* **> \InstallUtil.exe \< ** *directorio Bin del servidor de informes* **> \ReportingServicesLibrary.dll**  
  
        > [!NOTE]  
        >  Reemplace \< *directorio de .NET 2.0 Framework*> con la ruta de acceso física de la versión 2.0 de .NET Framework, los archivos y reemplace \< *directorio Bin del servidor de informes*> con la ruta de acceso física de los archivos binarios del servidor de informes.  
  
3.  Reinicie el servicio [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Para comprobar que los pasos funcionaron, abra un explorador web y navegue a la dirección URL del Administrador de informes o del servidor de informes. A continuación, abra el Monitor de rendimiento para comprobar que los contadores funcionan.  
  
#### <a name="to-re-add-the-performance-registry-keys-by-using-registry-editor"></a>Para volver a agregar las claves del Registro de rendimiento con el Editor del Registro  
  
1.  Abra el Editor del Registro:  
  
    1.  Haga clic en **Inicio**y, a continuación, en **Ejecutar**.  
  
    2.  En el **ejecutar** cuadro de diálogo el **abierto** , escriba `regedit`.  
  
2.  En el Editor del registro, seleccione la clave del registro siguiente: `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service\Performance`  
  
3.  Haga clic con el botón derecho en el nodo **Performance** , seleccione **Nuevo**y haga clic en **Valor de cadena múltiple**.  
  
4.  Tipo `Counter Names` y, a continuación, presione ENTRAR.  
  
5.  Repetir para agregar la `Counter Types` clave del registro en este nodo.  
  
6.  Vaya a la siguiente clave del registro: `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service\Performance`  
  
7.  Haga clic con el botón derecho en el nodo **Performance** , seleccione **Nuevo**y haga clic en **Valor de cadena múltiple**.  
  
8.  Tipo `Counter Names` y, a continuación, presione ENTRAR.  
  
9. Repetir para agregar la `Counter Types` clave del registro en este nodo.  
  
 Después de reparar la instancia de 64 bits o volver a agregar las claves del Registro manualmente, puede utilizar el Monitor de Rendimiento para configurar los objetos de rendimiento de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] que desee supervisar.  
  
###  <a name="ConfigPropsMissing"></a> Las propiedades de configuración ReportServerExternalURL y PassThroughCookies no están configuradas después de actualizar SQL Server 2005  
 Al actualizar desde [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] a [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)], `ReportServerExternalURL` y `PassThroughCookies` el proceso de actualización no configura las propiedades de configuración. `ReportServerExternalURL` es una propiedad opcional y se debe establecer únicamente si está utilizando elementos Web de SharePoint 2.0 y desea que los usuarios puedan recuperar un informe y abrirlo en una nueva ventana del explorador. Para obtener más información acerca de `ReportServerExternalURL`, consulte [direcciones URL en archivos de configuración &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/urls-in-configuration-files-ssrs-configuration-manager.md). `PassThroughCookies` se requiere únicamente cuando se usa el método de autenticación personalizada. Para obtener más información acerca de `PassThroughCookies`, consulte [configurar el Administrador de informes para pasar Cookies de autenticación personalizada](../security/configure-the-web-portal-to-pass-custom-authentication-cookies.md).  
  
> [!NOTE]  
>  Al utilizar la autenticación personalizada, se recomienda que migre la instalación en lugar de actualizarla. Para más información sobre cómo migrar [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vea [Migrar una instalación de Reporting Services &#40;modo nativo&#41;](../../reporting-services/install-windows/migrate-a-reporting-services-installation-native-mode.md).  
  
 De forma predeterminada, estas propiedades no existen en la configuración de [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] . Si configuró estas propiedades en [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] y continúa requiriendo la funcionalidad que proporcionan, debe agregarlas manualmente al archivo **RSReportServer.config** después del proceso de actualización. Para más información, vea [Modificar un archivo de configuración de Reporting Services &#40;RSreportserver.config&#41;](../report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md).  
  
###  <a name="Default2005InstallBreaks2008"></a> Se produce un error de instalación para una instancia predeterminada de SQL Server 2005 Reporting Services en un equipo que ejecuta SQL Server 2012 Reporting Services  
 Si intenta instalar una instancia predeterminada de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en un equipo que ya ejecuta una instancia de [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)], [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instancia podrá instalar con el mensaje de error siguiente:  
  
 "Ya hay instalada en este equipo una instancia con el mismo nombre. Para continuar con la instalación de SQL Server, proporcione un nombre de instancia único."  
  
 Este problema se produce independientemente de si la instancia de [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] es una instancia con nombre o predeterminada, e independientemente de si ya existe en el equipo una instancia de [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] con ese nombre.  
  
 Como solución alternativa para este problema, tiene una de las opciones siguientes:  
  
-   Si debe ejecutar [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] como la instancia predeterminada en el equipo, debe instalar la [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instancia antes de la [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] instancia.  
  
-   Si el [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instancia no tiene que ser una instancia predeterminada, puede instalar el [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instancia como una instancia con nombre después de instalar el [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] instancia.  
  
###  <a name="WindowsAuthBreaksAfterUpgrade"></a> 401 error no autorizado al utilizar la autenticación de Windows después de actualizar SQL Server 2005 a SQL Server 2012  
 Si actualiza desde [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] a [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]y usa la autenticación NTLM con una cuenta integrada para la cuenta de servicio del servidor de informes, podría encontrar un error no autorizado 401-al tener acceso el servidor de informes o el Administrador de informes Después de la actualización.  
  
 Esto se debe a un cambio en la configuración de [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] predeterminada para la autenticación de Windows. Negotiate se configura cuando la cuenta de servicio del servidor de informes es Servicio de red o Sistema local. NTLM se configura cuando la cuenta del servicio del servidor de informes no es ninguna de esas cuentas integradas. Para corregir este problema después de actualizar, puede modificar el archivo RSReportServer.config y configurar `AuthenticationType` para que sea `RSWindowsNTLM`. Para obtener más información, consulte [configurar la autenticación de Windows en el servidor de informes](../security/configure-windows-authentication-on-the-report-server.md).  
  
###  <a name="Uninstall32BitBreaks64Bit"></a> Desinstalación de la instancia de 32 bits de SQL Server 2012 Reporting Services en la implementación en paralelo con una instancia de 64 bits de la instancia de 64 bits de saltos  
 Al instalar una instancia de 32 bits y una instancia de 64 bits de [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] en paralelo en un equipo y desinstalar la instancia de 32 bits, se quitan cuatro claves del Registro de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . De esta forma se daña la instancia de 64 bits de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Las claves del Registro de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] que se quitan al desinstalar la instancia de 32 bits son:  
  
 `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service\Performance:Counter Names` `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Windows Service\Performance:Counter Names` `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service\Performance:Counter Types` `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Windows Service\Performance:Counter Types`  
  
 Para corregir este problema, puede reparar la instancia de 64 bits. Aunque se recomienda utilizar la reparación, puede volver a agregar las claves del Registro manualmente utilizando el Editor del Registro.  
  
> [!CAUTION]  
>  Una modificación incorrecta del Registro puede provocar daños graves en el sistema. Antes de efectuar cambios en el Registro, debe realizar una copia de seguridad de los datos importantes del equipo.  
  
##  <a name="bkmk_additional"></a> Recursos adicionales  
 A continuación se indican recursos adicionales que puede revisar como ayuda para la solución de problemas:  
  
-   Wiki de TechNet: temas de solución de problemas [Solución de problemas de SQL Server Reporting Services (SSRS) en el modo integrado de SharePoint](http://social.technet.microsoft.com/wiki/contents/articles/troubleshoot-sql-server-reporting-services-ssrs-in-sharepoint-integrated-mode.aspx)  
  
-   [Foro de SQL Server Reporting Services](http://social.msdn.microsoft.com/Forums/sqlreportingservices/threads)  
  
 ![Configuración de SharePoint](../../../2014/analysis-services/media/as-sharepoint2013-settings-gear.gif "configuración de SharePoint") [enviar comentarios e información de contacto a través de Microsoft SQL Server Connect](https://connect.microsoft.com/SQLServer/Feedback) (https://connect.microsoft.com/SQLServer/Feedback).  
  
  
