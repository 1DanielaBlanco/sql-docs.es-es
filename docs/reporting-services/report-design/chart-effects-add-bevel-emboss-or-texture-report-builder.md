---
title: "Agregar estilos con bisel, relieve y textura a un gráfico (Generador de informes y SSRS) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-design
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 737cfc80-b39e-497c-817b-b46693deb58f
caps.latest.revision: "6"
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ce27503bed40b45359d8c65c6eeec7674e1ce486
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2018
---
# <a name="chart-effects---add-bevel-emboss-or-texture-report-builder"></a>Efectos de gráfico: agregar bisel, relieve o textura (Generador de informes)
  Cuando use determinados tipos de gráficos, puede especificar efectos de dibujo que aumenten el impacto visual del gráfico. Estos efectos de dibujo solamente se aplican a las series del gráfico. No afectan a ningún otro elemento del gráfico.  
  
 Cuando use cualquier variante de un gráfico circular o de anillos, puede especificar un estilo de dibujo de borde suave o cóncavo, similar a los efectos de bisel o de relieve que se pueden aplicar a una imagen.  
  
 Cuando use cualquier variante de un gráfico de barras o de columnas, puede aplicar estilos de textura, como cilindros, cuñas y degradados a barras o columnas individuales.  
  
 Además de estos estilos de dibujo, puede agregar bordes y sombras a muchos elementos del gráfico para crear una sensación de profundidad. Para más información sobre otras maneras de dar formato al gráfico, vea [Aplicar formato a un gráfico &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-bevel-or-emboss-styles-to-a-pie-or-doughnut-chart"></a>Para agregar estilos de bisel y de relieve a un gráfico circular o de anillos  
  
1.  En la pestaña **Vista** , seleccione **Propiedades** para abrir el panel Propiedades.  
  
2.  Seleccione el gráfico circular o de anillos que desea mejorar. Seleccione un campo de datos en el gráfico, no en el gráfico entero.  
  
3.  En el panel de propiedades, expanda el nodo **CustomAttributes** .  
  
4.  Para PieDrawingStyle, seleccione un estilo en la lista desplegable.  
  
> [!NOTE]  
>  No puede tener estilos de relieve o bisel, y 3D en el mismo gráfico. Si ha habilitado 3D para el gráfico, no verá la propiedad PieDrawingStyle.  
  
 ![Gráfico circular con estilo de dibujo cóncavo](../../reporting-services/report-design/media/rs-piedrawingeffects-concave.gif "Gráfico circular con estilo de dibujo cóncavo")  
  
### <a name="to-add-texture-styles-to-a-bar-or-column-chart"></a>Para agregar estilos de textura a un gráfico de barras o de columnas  
  
1.  Seleccione el gráfico de barras o de columnas que desea mejorar. Seleccione un campo de datos en el gráfico, no en el gráfico entero.  
  
2.  Abra el panel de propiedades.  
  
3.  Expanda el nodo **CustomAttributes** .  
  
4.  Para DrawingStyle, seleccione un estilo en la lista desplegable.  
  
> [!NOTE]  
>  No puede tener estilos de relieve o bisel, y 3D en el mismo gráfico. Si ha habilitado 3D para el gráfico, no verá la propiedad PieDrawingStyle.  
  
 ![Gráfico de barras con efecto de dibujo LightToDark](../../reporting-services/report-design/media/rs-bardrawingeffects-lighttodark.gif "Gráfico de barras con efecto de dibujo LightToDark")  
  
## <a name="see-also"></a>Ver también  
 [Gráficos de barras &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/bar-charts-report-builder-and-ssrs.md)   
 [Gráficos de columnas &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/column-charts-report-builder-and-ssrs.md)   
 [Gráficos circulares &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)   
 [Aplicar formato a un gráfico &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)  
  
  
