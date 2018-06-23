---
title: Dirección URL del Administrador de informes (modo nativo de SSRS) | Documentos de Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rsconfigtool.reportmanagervirtualdirectory.f1
ms.assetid: 45768952-23a6-45a5-b541-e7bf192b4a78
caps.latest.revision: 7
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 1469d877b992638119ad60bafadc1023a4ed5fc7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36106678"
---
# <a name="report-manager-url-ssrs-native-mode"></a>Dirección URL del Administrador de informes (Modo nativo de SSRS)
  Utilice la página Dirección URL del Administrador de informes para configurar o modificar la dirección URL que se usa para el acceso al Administrador de informes. De forma predeterminada, la dirección URL del Administrador de informes hereda el prefijo, la dirección IP y el puerto de la dirección URL de servicio web del servidor de informes. Esto se debe a que el Administrador de informes proporciona acceso front-end a un servicio web que se ejecuta dentro del mismo servicio del servidor de informes. Si está aislando las aplicaciones de servicio y usa el Administrador de informes para tener acceso a un servicio web del servidor de informes en un equipo diferente, debe modificar el archivo RSReportServer.config para que dirija al Administrador de informes a una instancia diferente. Para obtener más información acerca de cómo configurar una conexión de administrador de informes a un servidor de informes remoto, consulte [Reporting Services Configuration Manager &#40;modo nativo&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Si está configurando el servidor de informes para ejecutarlo en el modo integrado de SharePoint, no cree una dirección URL del Administrador de informes. El Administrador de informes no se admite en un servidor de informes que se ejecuta en el modo integrado de SharePoint. Si ya existe una dirección URL para el Administrador de informes, dejará de estar disponible después de configurar el servidor de informes para ejecutarse en el modo integrado de SharePoint.  
  
 Para abrir esta página, inicie la [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager y haga clic en **Report Manager URL** en el panel de navegación. Para obtener más información sobre cómo iniciar el Administrador de configuración, consulte [Reporting Services Configuration Manager &#40;modo nativo&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
> [!NOTE]  
>  Si el Administrador de informes no está habilitado, no puede establecer las opciones de esta página. Para obtener más información acerca de cómo habilitar el Administrador de informes, consulte [Reporting Services Configuration Manager &#40;modo nativo&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
## <a name="options"></a>Opciones  
 **Directorio virtual**  
 Especifica el nombre del directorio virtual del Administrador de informes. Solo puede tener un nombre de directorio virtual para cada instancia del Administrador de informes del mismo equipo.  
  
 **Direcciones URL**  
 Muestra la dirección URL definida para la instancia actual del Administrador de informes.  
  
 **Avanzadas**  
 Agregue una dirección URL adicional para la instancia actual del Administrador de informes.  
  
## <a name="see-also"></a>Vea también  
 [Configurar una dirección URL &#40;Administrador de configuración de SSRS&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)   
 [Las direcciones URL en archivos de configuración &#40;Administrador de configuración de SSRS&#41;](../../reporting-services/install-windows/urls-in-configuration-files-ssrs-configuration-manager.md)   
 [Configurar las direcciones URL del servidor de informes &#40;Administrador de configuración de SSRS&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
  
  