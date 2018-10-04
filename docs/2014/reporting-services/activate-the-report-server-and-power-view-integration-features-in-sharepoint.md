---
title: Activar el servidor de informes y Power View Integration Features in SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: c7f64a54-c555-4d31-bf99-3abe57dc8626
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 1ab486390e8da36d14d5aac1e1049a5836dd2be9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2018
ms.locfileid: "48081835"
---
# <a name="activate-the-report-server-and-power-view-integration-features-in-sharepoint"></a>Activar las características de integración del servidor de informes y Power View en SharePoint
  Las características de colección de sitios de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] se generan normalmente de forma predeterminada una vez se ha instalado el complemento de [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] para productos de SharePoint. En algunas situaciones, tendrá que activar las características de forma manual.  
  
 Si instala el complemento de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] para productos de SharePoint 2010 después de instalar el producto de SharePoint, la característica de integración del servidor de informes y la característica de integración de la vista avanzada se activarán únicamente para colecciones de sitios raíz. Para las demás colecciones de sitios, deberá activar manualmente las características. Por ejemplo, si tiene una colección de sitios **http://[my nombre de servidor] / Sites / [nombre de la colección de sitios]** deberá activar manualmente la [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] características de colección de sitios.  
  
 Cuando no hay ninguna colección de sitios raíz, el [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] complemento registrará un mensaje similar al siguiente.  
  
 “La aplicación web 80 de Sharepoint no tiene colección de sitios raíz”  
  
 El mensaje se encuentra en el registro de instalación del complemento, “RS_SP_#.log”, donde # es un número que se incrementa. El archivo de registro se encuentra en la carpeta Temp de los usuarios actuales, por ejemplo: C:\Usuarios\\[nombre del usuario]\AppData\Local\Temp. Para obtener más información sobre las opciones de registro con el complemento, vea [instalar o desinstalar el complemento Reporting Services para SharePoint &#40;SharePoint 2010 y SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).  
  
 En este tema:  
  
-   [Para activar las características de colección de sitios de integración del servidor de informes y de la vista avanzada:](#bkmk_features)  
  
-   [Para activar o desactivar la característica de colección de sitios de Administración central de Reporting Services:](#bkmk_centraladmin)  
  
##  <a name="bkmk_features"></a> Para activar las características de colección de sitios de integración del servidor de informes y de la vista avanzada:  
  
1.  Abra el explorador en el sitio donde desea que estén activas las características de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
2.  Haga clic en **Acciones del sitio**.  
  
3.  Haga clic en **Configuración del sitio**.  
  
4.  Haga clic en **Características de la colección de sitios** en el grupo Administración de la colección de sitios.  
  
5.  Busque **Característica de integración del servidor de informes** o **Característica de integración de Power View** en la lista.  
  
6.  Haga clic en **Activar**.  
  
 Para desactivar las características, puede usar el mismo procedimiento y hacer clic en **Desactivar** en lugar de en **Activar**.  
  
##  <a name="bkmk_centraladmin"></a> Para activar o desactivar la característica de colección de sitios de Administración central de Reporting Services:  
  
1.  Abra el explorador en Administración central de SharePoint.  
  
2.  Haga clic en **Acciones del sitio**.  
  
3.  Haga clic en **Configuración del sitio**.  
  
4.  Haga clic en **Características de la colección de sitios** en el grupo Administración de la colección de sitios.  
  
5.  Busque la **Característica de administración central del servidor de informes** en la lista.  
  
6.  Haga clic en **Activar**.  
  
 Para desactivar la característica, puede usar el mismo procedimiento y hacer clic en **Desactivar** en lugar de en **Activar**.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Una vez activada la característica, puede continuar con la integración del servidor.  
  
## <a name="see-also"></a>Vea también  
 [Instalar o desinstalar el complemento Servicios de informes para SharePoint &#40;SharePoint 2010 y SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
