---
title: "Recopilar segmentos peque&#241;os en un gr&#225;fico circular (Generador de informes y SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 21c2b8cb-b9ca-4bc0-bf49-50ba432562f6
caps.latest.revision: 10
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 8
---
# Recopilar segmentos peque&#241;os en un gr&#225;fico circular (Generador de informes y SSRS)
  Si los gráficos circulares muestran demasiados puntos de datos, pueden parecer desordenados. Para resolver este problema, puede mostrar como un único sector en el gráfico circular todos los datos que estén por debajo de un determinado valor.  
  
 Para recopilar sectores pequeños en un solo sector, en primer lugar debe decidir si el umbral de recopilación de sectores pequeños será un porcentaje del gráfico circular o un valor fijo. A continuación, establezca las propiedades CollectedThreshold y CollectedThresholdUsePercent. Establezca la propiedad CollectedThreshold como el porcentaje del gráfico de un valor que debe quedarse por debajo para que se realice la recopilación o el valor de datos del umbral real de la colección. Establezca la propiedad CollectedThresholdUsePercent en **True** para usar un porcentaje o **False** para utilizar un valor real.  
  
 También puede recopilar sectores pequeños en un segundo gráfico circular al que se llamará desde un sector recopilado del primer gráfico circular. El segundo gráfico circular se dibuja a la derecha del gráfico circular original.  
  
 En los gráficos de embudo y en los piramidales, no es posible combinar varios sectores en uno solo.  
  
 Un ejemplo de este gráfico está disponible como informe de ejemplo. Para más información acerca de cómo descargar este y otros informes de ejemplo, consulte el tema sobre [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][informes de ejemplo del Generador de informes y el Diseñador de informes](http://go.microsoft.com/fwlink/?LinkId=198283).  
  
### Para recopilar sectores pequeños en un solo sector de un gráfico circular  
  
1.  Abra el panel de propiedades.  
  
2.  En la superficie de diseño, haga clic en cualquier sector del gráfico circular. Las propiedades de la serie se muestran en el panel de propiedades.  
  
3.  En la sección **General** , expanda el nodo **CustomAttributes** .  
  
4.  Establezca la propiedad CollectedStyle en **SingleSlice**.  
  
5.  Establezca el valor del umbral de recopilación y el tipo de umbral. En los ejemplos siguientes se muestran formas habituales de establecer umbrales de recopilación.  
  
    -   **Por porcentaje.** Por ejemplo, para recopilar en un solo sector cualquier sector del gráfico circular que esté por debajo del 10%:  
  
         Establezca la propiedad CollectedThresholdUsePercent en **True**.  
  
         Establezca la propiedad CollectedThreshold en **10**.  
  
        > [!NOTE]  
        >  Si establece CollectedStyle en **SingleSlice**, CollectedThreshold en un valor mayor que **100**, y CollectedThresholdUsePercent es **True**, el gráfico iniciará una excepción porque no se puede calcular el porcentaje. Para resolver este problema, establezca CollectedThreshold en un valor menor que **100**.  
  
    -   **Por valor de datos.** Por ejemplo, para recopilar en un solo sector cualquier sector del gráfico circular que esté por debajo de 5000:  
  
         Establezca la propiedad CollectedThresholdUsePercent en **False**.  
  
         Establezca la propiedad CollectedThreshold en **5000**.  
  
6.  Establezca la propiedad CollectedLabel en una cadena que represente la etiqueta de texto que se mostrará en el sector recopilado.  
  
7.  (Opcional) Establezca las propiedades CollectedSliceExploded, CollectedColor, CollectedLegendText y CollectedToolTip. Estas propiedades cambian el aspecto, el color, el texto de la etiqueta, el texto de la leyenda y la información sobre herramientas del sector simple.  
  
### Para recopilar sectores pequeños en un gráfico circular secundario con llamada  
  
1.  Siga los pasos 1 a 3 descritos anteriormente.  
  
2.  Establezca la propiedad CollectedStyle en **CollectedPie**.  
  
3.  Establezca la propiedad CollectedThreshold en un valor que represente el umbral de recopilación de los sectores pequeños en un solo sector. Cuando la propiedad CollectedStyle se establece en **CollectedPie**, la propiedad CollectedThresholdUsePercent siempre se establece en **True** y el umbral de recopilación siempre se mide como porcentaje.  
  
4.  (Opcional) Establezca las propiedades CollectedColor, CollectedLabel, CollectedLegendText y CollectedToolTip. El resto de las propiedades denominadas "Collected" no se aplican al gráfico circular recopilado.  
  
> [!NOTE]  
>  El gráfico circular secundario se calcula en función de los sectores pequeños existentes en los datos, por lo que solo se ve en Vista previa. No aparece en la superficie de diseño.  
  
> [!NOTE]  
>  No puede dar formato al gráfico circular secundario. Por esta razón, a la hora de recopilar sectores del gráfico circular se recomienda el uso del primer enfoque.  
  
## Vea también  
 [Gráficos circulares &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)   
 [Aplicar formato a los puntos de datos de un gráfico &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
 [Mostrar las etiquetas de los puntos de datos fuera de un gráfico circular &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md)   
 [Mostrar valores de porcentaje en un gráfico circular &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md)   
 [Agregar efectos 3D a un gráfico &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/add-3d-effects-to-a-chart-report-builder-and-ssrs.md)  
  
  