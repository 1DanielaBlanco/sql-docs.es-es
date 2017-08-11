---
title: Cambiar el texto de un elemento de leyenda (generador de informes y SSRS) | Documentos de Microsoft
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
ms.assetid: 9e82fa34-17ed-494f-b25d-03dcc353a21f
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 8c253794b7b884a3dd7835409e256245ae0dc5a2
ms.contentlocale: es-es
ms.lasthandoff: 08/09/2017

---
# <a name="chart-legend---change-item-text-report-builder"></a>La leyenda del gráfico: elemento cambiar texto (generador de informes)
  Cuando se coloca un campo en el área Valores del gráfico, se genera automáticamente un elemento de leyenda que contiene el nombre de este campo. Cada elemento de leyenda se conecta a una serie individual del gráfico, a excepción de los gráficos de formas, donde la leyenda se conecta a puntos de datos individuales en lugar de a series individuales.  
  
 En los gráficos de formas, puede cambiar el texto de un elemento de leyenda para mostrar más información sobre los puntos de datos individuales. Por ejemplo, si quiere mostrar los valores de los puntos de datos como porcentajes en la leyenda, puede usar una palabra clave como **#PERCENT**. Puede anexar códigos de formato de .NET Framework junto con las palabras clave para aplicar formatos numéricos y de fecha. Para obtener más información sobre las palabras clave, vea [Aplicar formato a los puntos de datos de un gráfico &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/formatting-data-points-on-a-chart-report-builder-and-ssrs.md).  
  
 ![Gráfico de nitidez](../../reporting-services/report-design/media/sharpchart.png "nitidez de gráfico")  
  
 En los gráficos que no son de formas, puede cambiar el texto de un elemento de leyenda. Por ejemplo, si la serie se denomina "Serie1", es posible que desee cambiar el texto por otro más descriptivo como "Ventas para 2008".  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-modify-the-text-that-appears-in-the-legend-on-a-shape-chart"></a>Para modificar el texto que aparece en la leyenda en un gráfico de formas  
  
1.  Haga clic con el botón derecho en una serie o en un campo del área **Valores** y seleccione **Propiedades de la serie**.  
  
2.  Haga clic en **Leyenda** y, en el cuadro **Texto de leyenda personalizado** , escriba una palabra clave.  
  
 En la tabla siguiente se proporcionan ejemplos de palabras clave específicas de los gráficos que pueden usarse para la propiedad **Texto de leyenda personalizado**. Para obtener más información sobre las palabras clave, vea [Aplicar formato a los puntos de datos de un gráfico &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/formatting-data-points-on-a-chart-report-builder-and-ssrs.md).  
  
|Palabra clave|Description|El ejemplo de lo que aparece como texto en la leyenda|  
|-------------|-----------------|---------------------------------------------------|  
|`#PERCENT{P1}`|Muestra el porcentaje del valor total con un decimal.|85.0%|  
|`#VALY`|Muestra el valor numérico real del campo de datos.|17000|  
|`#VALY{C2}`|Muestra el valor numérico real del campo de datos con formato monetario y con dos decimales.|$17000.00|  
|`#AXISLABEL (#PERCENT{P0})`|Muestra la representación de texto del campo de categorías, seguida por el porcentaje que cada categoría representa en el gráfico.|Michael Blythe (85%)|  
  
> [!NOTE]  
>  La palabra clave #AXISLABEL solo se puede evaluar en tiempo de ejecución cuando no se especifica ningún campo en el área **Grupos de la serie** .  
  
### <a name="to-modify-the-text-that-appears-in-the-legend-on-a-non-shape-chart"></a>Para modificar el texto que aparece en la leyenda en un gráfico que no es de formas  
  
1.  Haga clic con el botón derecho en una serie o en un campo del área **Valores** y seleccione **Propiedades de la serie**.  
  
2.  Haga clic en **Leyenda** y, en el cuadro **Texto de leyenda personalizado** , escriba una etiqueta de leyenda. La serie se actualizada con el texto especificado.  
  
## <a name="see-also"></a>Vea también  
 [Aplicar formato a la leyenda de un gráfico de &#40; El generador de informes y SSRS &#41;](../../reporting-services/report-design/chart-legend-formatting-report-builder.md)   
 [Aplicar formato a los colores de serie en un gráfico de &#40; El generador de informes y SSRS &#41;](../../reporting-services/report-design/formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)   
 [Ocultar elementos de leyenda en el gráfico &#40; El generador de informes y SSRS &#41;](../../reporting-services/report-design/chart-legend-hide-items-report-builder.md)  
  
  
