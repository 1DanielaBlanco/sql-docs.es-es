---
title: Desinstalar el Generador de informes | Microsoft Docs
ms.custom: 
ms.date: 05/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: install-windows
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 009538c6-4941-4393-b14b-9144cffdbdaf
caps.latest.revision: "10"
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 2ca635948940ec0a8921444d2b7928d53e16c70f
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2018
---
# <a name="uninstall-report-builder"></a>Desinstalar el Generador de informes

Podrá desinstalar la versión independiente del Generador de informes desde el panel de control o la línea de comandos.

La desinstalación del Generador de informes desde la línea de comandos utiliza una sintaxis que es idéntica a la que se utiliza para instalar el Generador de informes, excepto en que se usa la opción /x en lugar de la opción /i. Las líneas de comandos para desinstalar también pueden incluir la opción /quiet y otras opciones estándar. Si se ha quitado el paquete de Windows Installer para el Generador de informes (ReportBuilder3_x86.msi), no podrá utilizar con facilidad la línea de comandos para desinstalar el Generador de informes. Para aprender cómo podría quitar el Generador de informes mediante su GUID, vea la documentación del programa msiexec en [Opciones de la línea de comandos](https://msdn.microsoft.com/library/windows/desktop/aa367988.aspx).  

Si las carpetas utilizadas por el Generador de informes incluyen archivos personalizados, las carpetas y archivos se conservan cuando se quita el Generador de informes. Solamente se quitan los archivos del Generador de informes.  

### <a name="to-uninstall-report-builder-from-the-control-panel"></a>Para desinstalar el Generador de informes desde el panel de control

1.  En el menú **Inicio** , haga clic en **Panel de control**.  
  
2.  En el Panel de control, haga clic en **Programas y características**.  
  
3.  Busque Generador de informes de [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQL Server 2016 en la lista **Nombre** y haga clic en él.  
  
4.  Haga clic en **Desinstalar**.  
  
5.  Si se le solicita que confirme la desinstalación del Generador de informes, haga clic en **Sí**.  
  
### <a name="to-uninstall-report-builder-from-the-command-line"></a>Para desinstalar el Generador de informes desde la línea de comandos  
  
1.  En el menú **Inicio** , haga clic en **Ejecutar**.  
  
2.  En el cuadro de texto **Abrir** , escriba **cmd.**  
  
3.  En la ventana del símbolo del sistema, navegue hasta la carpeta con ReportBuilder3_x86.msi.  
  
4.  Escriba una línea de comandos básica similar a esta:  
  
 `msiexec /x ReportBuilder3_x86.msi /quiet /l*v install.log`  
  
 Si puede, utilice una línea de comandos como la siguiente para incluir el registro:  
  
 `msiexec /x ReportBuilder3_x86.msi /quiet /l*v c:\junk\install.log`  
  
5.  Presione **ENTRAR**.  

## <a name="next-steps"></a>Pasos siguientes

[Instalación del Generador de informes](../../reporting-services/install-windows/install-report-builder.md)  

¿Tiene alguna pregunta más? [Puede plantear sus dudas en el foro de Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
