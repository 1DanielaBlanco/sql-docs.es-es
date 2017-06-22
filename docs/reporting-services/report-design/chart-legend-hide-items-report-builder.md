---
title: "Ocultar elementos de leyenda en el gráfico (generador de informes y SSRS) | Documentos de Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 92256240-0cd5-4be4-8904-d1e3b93cb6b3
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 06f1cf8cde2eb9a9c9aa261188e64aa2fc7afe4b
ms.contentlocale: es-es
ms.lasthandoff: 06/22/2017

---
# <a name="chart-legend---hide-items-report-builder"></a>Leyenda del gráfico - ocultar elementos (generador de informes)
De forma predeterminada, cualquier serie que se agregue a un gráfico que no sea un gráfico de formas en un informe paginado de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] se agregará como elemento en la leyenda. En los gráficos circulares, de anillos, de embudo y piramidales, cualquier serie que se agregue al gráfico agregará puntos de datos individuales a la leyenda.  
  
 Puede ocultar cualquier elemento de la leyenda. Aunque oculte un elemento de leyenda, este seguirá apareciendo en el gráfico. Esto resulta de gran utilidad en situaciones donde no se desea mostrar más información sobre una serie agregada al gráfico. Por ejemplo, si ha agregado al gráfico una serie calculada, como una media móvil, puede ser que le interese ocultar esta entrada en la leyenda para que solo se muestre más información sobre la serie original.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-hide-an-item-from-display-in-the-legend"></a>Para ocultar un elemento en la leyenda  
  
1.  Haga clic con el botón derecho en la serie que quiere ocultar y seleccione **Propiedades de la serie**.  
  
2.  Haga clic en **Leyenda**. Seleccione la opción **No mostrar esta serie en una leyenda** .  
  
    > [!NOTE]  
    >  No puede ocultar una serie para un grupo y dejarla visible para los demás. Si ha agregado un campo al área **Grupos de series** , se ocultarán todas las series que pertenecen a este grupo.  
  
## <a name="see-also"></a>Vea también  
 [Aplicar formato a la leyenda de un gráfico &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/chart-legend-formatting-report-builder.md)   
 [Aplicar formato a los puntos de datos de un gráfico &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
 [Cambiar el texto de un elemento de leyenda &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/chart-legend-change-item-text-report-builder.md)   
 [Agregar una media móvil a un gráfico &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/add-a-moving-average-to-a-chart-report-builder-and-ssrs.md)   
 [Cuadro de diálogo de Propiedades de la leyenda, General &#40;Generador de informes y SSRS&#41;](http://msdn.microsoft.com/library/db718f8f-f185-422f-871c-96f0749e5893)  
  
  
