---
title: Características del sitio (modo de SharePoint) y la configuración del sitio de Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e0040fec-e2b7-4099-ae01-3b9bb9128bbd
caps.latest.revision: 9
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: b7d059719b88abec5f3e89793baa7727ec66a962
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37175438"
---
# <a name="reporting-services-site-settings-and-site-featuressharepoint-mode"></a>Valores de configuración del sitio de Reporting Services y características del sitio (modo de SharePoint)
  El modo de SharePoint de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] tiene varias características personalizadas de nivel de sitio y una característica de sitio que se pueden administrar desde la página de configuración del sitio de SharePoint. Los valores de configuración se aplican a todo el sitio y afectan a todas las aplicaciones de servicio de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Debe tener permisos de Administrador de contenido y Administrador del sistema para ver esta página.  
  
|Configuración del sitio|Descripción|  
|------------------|-----------------|  
|Configuración del sitio de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]|En este tema se describe la configuración de todo el sitio.|  
|Administrar alertas de datos|Característica de administración de alertas de datos.|  
|Sincronización de archivos del Servidor de informes|Característica de nivel de sitio que está desactivada de forma predeterminada.<br /><br /> Sincroniza los archivos del servidor de informes (.rdl, .rsds, .smdl, .rsd, .rsc, .rdlx) entre una biblioteca de documentos de SharePoint y el servidor de informes si los archivos se agregan o se actualizan directamente en la biblioteca de documentos.<br /><br /> Para obtener más información, consulte [Activar la característica de sincronización de archivos del servidor de informes en Administración central de SharePoint](../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md).|  
  
## <a name="to-open-the-reporting-services-site-settings-page"></a>Para abrir la página Configuración del sitio de Reporting Services  
  
1.  En el menú **Acciones del sitio** del sitio de SharePoint, haga clic en **Configuración del sitio**.  
  
2.  En la sección **Reporting Services** , haga clic en **Configuración del sitio de Reporting Services**.  
  
## <a name="options-for-reporting-services-site-settings"></a>Opciones de configuración del sitio de Reporting Services  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Habilitar la descarga del control ActiveX de RSClientPrint**|El control muestra un cuadro de diálogo de impresión personalizado compatible con características comunes a otros cuadros de diálogo de impresión, incluida la vista previa de impresión, selecciones de páginas para especificar páginas e intervalos de páginas, márgenes y orientación. Para obtener más información acerca del control, vea [Using the RSClientPrint Control in Custom Applications](report-server-web-service/net-framework/using-the-rsclientprint-control-in-custom-applications.md)|  
|**Habilitar los errores remotos en modo local**|Muestre u oculte mensajes de error detallados en equipos remotos cuando la ejecución se realice en modo local. Si ve un mensaje de error similar al siguiente, es posible que habilitar errores remotos pueda ser de utilidad:<br /><br /> `For more information about this error navigate to the report server on the local server machine or enable remote errors`|  
|**Habilitar los metadatos de accesibilidad para los informes**|Activa los metadatos de accesibilidad de la salida HTML en los informes|  
|**Habilitar el tamaño exacto de ajuste de visualización de datos en los informes**|Configure el comportamiento de ajuste para la visualización de datos cuando esté en un Tablix, para corregir con exactitud. Esto incluye un gráfico, un medidor y un mapa. Cuando se deshabilita el comportamiento, se hace para que las visualizaciones de datos se ajusten aproximadamente, lo cual podría dejar algún espacio vacío. Este valor de configuración solo se aplica a las representaciones del elemento web del visor de informes. Para administrar este comportamiento en la representación del lado servidor, debe modificar el archivo **rsreportserver.config** . Para obtener más información, vea:<br /><br /> [Archivo de configuración RSReportServer](report-server/rsreportserver-config-configuration-file.md).<br /><br /> [Personalizar la representación de los parámetros de extensión en RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md).<br /><br /> [HTML Device Information Settings](html-device-information-settings.md).<br /><br /> Si se habilita Exacto, podría repercutir en el rendimiento porque el procesamiento para determinar el tamaño exacto puede conllevar más tiempo que un ajuste aproximado.|  
  
## <a name="see-also"></a>Vea también  
 [Administración de una aplicación de servicio de SharePoint para Reporting Services](../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md)  
  
  
