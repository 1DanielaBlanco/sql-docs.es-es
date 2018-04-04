---
title: Configuración de la información del dispositivo PDF | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: ''
ms.component: reporting-services
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- device information settings [Reporting Services], PDF rendering
- PDF [Reporting Services]
ms.assetid: 9a4aabe5-dbdc-4884-b999-1200983fee47
caps.latest.revision: ''
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0bd2635a54003fd663dadcf6d3bc5991c1841988
ms.sourcegitcommit: ccb05cb5a4cccaf7ffa9e85a4684fa583bab914e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="pdf-device-information-settings"></a>Configuración de la información del dispositivo PDF
  En la tabla siguiente se muestra la configuración de la información de los dispositivos para representar informes en formato PDF.  
  
|Configuración|Valor|  
|-------------|-----------|  
| **AccessiblePDF** | Indica si se debe representar un PDF accesible o etiquetado, que tiene un mayor tamaño, pero que resulta más sencillo de leer y explorar para los lectores de pantalla y otras tecnologías de asistencia. El valor predeterminado es **false**. [Disponible en Power BI Report Server (marzo de 2018) y versiones posteriores] |
|**Columns**|Número de columnas que se van a establecer para el informe. Este valor invalida la configuración original del informe.|  
|**ColumnSpacing**|Espacio entre las columnas que se va a establecer para el informe. Este valor invalida la configuración original del informe.|  
|**DpiX**|La resolución del dispositivo de salida en la dirección de x.|  
|**DpiY**|La resolución del dispositivo de salida en la dirección de y.|  
|**EndPage**|Última página del informe que se va a representar. El valor predeterminado es el de **StartPage**.|  
|**HumanReadablePDF**|Indica si se debe representar un archivo PDF sin comprimir, que es mayor en tamaño, pero más legible en un editor de texto sin formato. El valor predeterminado es **false**.|  
|**MarginBottom**|Valor del margen inferior, en pulgadas, que se va a establecer para el informe. Debe incluir un valor entero o un valor decimal seguido de "in" (por ejemplo, 1in). Este valor invalida la configuración original del informe.|  
|**MarginLeft**|El valor del margen izquierdo, en pulgadas, que se va a establecer para el informe. Debe incluir un valor entero o un valor decimal seguido de "in" (por ejemplo, 1in). Este valor invalida la configuración original del informe.|  
|**MarginRight**|El valor del margen derecho, en pulgadas, que se va a establecer para el informe. Debe incluir un valor entero o un valor decimal seguido de "in" (por ejemplo, 1in). Este valor invalida la configuración original del informe.|  
|**MarginTop**|El valor del margen superior, en pulgadas, que se va a establecer para el informe. Debe incluir un valor entero o un valor decimal seguido de "in" (por ejemplo, 1in). Este valor invalida la configuración original del informe.|  
|**PageHeight**|El alto de la página, en pulgadas, que se va a establecer para el informe. Debe incluir un valor entero o decimal seguido de "in" (por ejemplo, 11in). Este valor invalida la configuración original del informe.|  
|**PageWidth**|El ancho de la página, en pulgadas, que se va a establecer para el informe. Debe incluir un entero o el valor decimal seguido de "en" (por ejemplo, 8.5in). Este valor invalida la configuración original del informe.|  
|**StartPage**|Primera página del informe que se va a representar. El valor **0** indica que se representan todas las páginas. El valor predeterminado es **1**.|  
  
## <a name="see-also"></a>Ver también  
 [Pasar la configuración de información de dispositivo a las extensiones de representación](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personalizar los parámetros de extensión de representación en RSReportServer.Config](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Referencia técnica &#40;SSRS&#41;](../reporting-services/technical-reference-ssrs.md)  
  
  
