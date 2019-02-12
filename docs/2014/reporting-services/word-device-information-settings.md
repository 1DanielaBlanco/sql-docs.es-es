---
title: Configuración de la información del dispositivo Word | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Word [Reporting Services]
- device information settings [Reporting Services], Word
ms.assetid: 28146498-fae7-4b13-b47f-6ec05aa8e057
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 494bf45f2aeb4fce5ed3b259665b1e7759879184
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2019
ms.locfileid: "56022346"
---
# <a name="word-device-information-settings"></a>Configuración de la información del dispositivo web
  En la tabla siguiente se muestra la configuración de la información de los dispositivos para la representación en formato de [!INCLUDE[ofprword](../includes/ofprword-md.md)] .  
  
|Parámetro|Valor|  
|-------------|-----------|  
|`AutoFit`|`False`  AutoFit está establecido en `false` en cualquier tabla de Word.<br /><br /> `True`  AutoaFit está establecido en `true` en cada tabla de Word.<br /><br /> `Never`  Los valores de AutoFit no están establecidos en ninguna tabla de Word y el comportamiento revierte al predeterminado de Word.<br /><br /> `Default`  AutoFit se establece en las tablas que son más estrechas que el área física de dibujo (ancho de página física excepto los márgenes) por la página lógica.|  
|`ExpandToggles`|Indica si todos los elementos que se pueden alternar deberían representarse en su estado totalmente expandido. El valor predeterminado es `false`.|  
|`FixedPageWidth`|Indica si el ancho de página escrito en el archivo DOC crecerá para alojar el ancho de la página más grande en el cuerpo del informe. El valor predeterminado es `false`.|  
|**OmitHyperlinks**|Indica si omitir la acción Hyperlink en todos los elementos donde se establezca. El valor predeterminado es `false`|  
|`OmitDrillthroughs`|Indica si omitir la acción de obtención de detalles en todos los elementos donde se establezca. El valor predeterminado es `false`|  
  
## <a name="see-also"></a>Vea también  
 [Pasar la configuración de información de dispositivo a las extensiones de representación](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personalizar los parámetros de extensión de representación en RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Referencia técnica &#40;SSRS&#41;](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
