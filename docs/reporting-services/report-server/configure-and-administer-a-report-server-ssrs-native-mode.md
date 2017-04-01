---
title: "Configurar y administrar un servidor de informes (modo nativo de SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/18/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Reporting Services, componentes"
  - "implementar [Reporting Services], opciones de componente"
  - "servidores de informes [Reporting Services], opciones de componente"
  - "opciones de configuración [Reporting Services]"
  - "administrar Reporting Services"
  - "componentes [Reporting Services], configurar"
  - "configurar servidores [Reporting Services]"
ms.assetid: cfec012b-56f1-4346-9814-247acf22351c
caps.latest.revision: 51
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 51
---
# Configurar y administrar un servidor de informes (modo nativo de SSRS)
  En este tema se resumen los métodos que se pueden usar para configurar [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. También se incluye una lista de temas en los que se explica cómo configurar determinados componentes, características o funciones del servidor. Para configurar [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], puede:  
  
-   Usar el Administrador de configuración de Reporting Services. En muchos de los temas de esta sección se proporciona información acerca de la configuración de determinadas características mediante esta herramienta.  
  
-   Use [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] para personalizar las propiedades del servidor, habilitar Mis informes, habilitar los registros de seguimiento y establecer los valores predeterminados de todo el sitio. Para más información sobre la configuración del sitio, vea [Servidor de informes de Reporting Services &#40;modo nativo&#41;](../../reporting-services/report-server/reporting-services-report-server-native-mode.md) para Management Studio. Tenga en cuenta que se puede crear y ejecutar un script que establece las propiedades del servidor mediante programación. Para más información, vea [Script para tareas administrativas y de implementación](../../reporting-services/tools/script-deployment-and-administrative-tasks.md) y [Propiedades del sistema del servidor de informes](../Topic/Report%20Server%20System%20Properties.md).  
  
-   Use el Administrador de informes para conceder permisos para tener acceso al servidor de informes. Los permisos se conceden a través de las asignaciones de roles que define para cada cuenta de grupo o usuario. Para más información, vea [Roles y permisos &#40;Reporting Services&#41;](../../reporting-services/security/roles-and-permissions-reporting-services.md).  
  
-   También puede modificar archivos de configuración para cambiar la configuración de la aplicación. Para obtener más información acerca de cada archivo así como directrices para modificarlos, vea [Reporting Services Configuration Files](../../reporting-services/report-server/reporting-services-configuration-files.md).  
  
## En esta sección  
 [Configurar las direcciones URL del servidor de informes &#40;Administrador de configuración de SSRS&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
 Describe cómo definir las direcciones URL que se usan para tener acceso al servidor de informes y al Administrador de informes.  
  
 [Configurar la cuenta de servicio del servidor de informes &#40;Administrador de configuración de SSRS&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)  
 Proporciona recomendaciones y pasos sobre cómo modificar la contraseña y la cuenta de servicio.  
  
 [Crear una base de datos del servidor de informes &#40;Administrador de configuración de SSRS&#41;](../../reporting-services/install-windows/create-a-report-server-database-ssrs-configuration-manager.md)  
 Describe cómo crear una base de datos del servidor de informes, necesaria para almacenar objetos y metadatos de servidor.  
  
 [Configurar una conexión a la base de datos del servidor de informes &#40;Administrador de configuración de SSRS&#41;](../../reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
 Describe cómo modificar la cadena de conexión que utiliza el servidor de informes para conectarse a la base de datos del servidor de informes.  
  
 [Configurar un servidor de informes para la entrega de correo electrónico (Administrador de configuración de SSRS)](http://msdn.microsoft.com/es-es/b838f970-d11a-4239-b164-8d11f4581d83)  
 Describe cómo configurar un servidor de informes para permitir la distribución de informes por correo electrónico.  
  
 [Configurar la cuenta de ejecución desatendida &#40;Administrador de configuración de SSRS&#41;](../../reporting-services/install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)  
 Describe cómo configurar una cuenta de usuario para procesar informes en modo desatendido.  
  
## Vea también  
 [Configurar el acceso al Generador de informes](../../reporting-services/report-server/configure-report-builder-access.md)   
 [Archivos de configuración de Reporting Services](../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [Administrador de configuración de Reporting Services &#40;modo nativo&#41;](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)   
 [Seguridad y protección de Reporting Services](../../reporting-services/security/reporting-services-security-and-protection.md)   
 [Servidor de informes de Reporting Services &#40;modo nativo&#41;](../../reporting-services/report-server/reporting-services-report-server-native-mode.md)  
  
  