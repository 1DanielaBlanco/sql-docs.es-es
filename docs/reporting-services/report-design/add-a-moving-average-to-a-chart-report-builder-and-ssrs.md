---
title: "Agregar una media m&#243;vil a un gr&#225;fico (Generador de informes y SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 166cf9c1-0750-4866-8381-542e4fbfe65a
caps.latest.revision: 13
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 9
---
# Agregar una media m&#243;vil a un gr&#225;fico (Generador de informes y SSRS)
Una media móvil es una media de los datos de la serie, calculada en un período de tiempo definido. En los informes paginados de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], la media móvil se puede mostrar en el gráfico para identificar tendencias significativas.  

![report-builder-column-chart-tutorial](../../reporting-services/media/report-builder-column-chart-tutorial.png)
  
 La fórmula de la media móvil es el indicador de precio más habitual en los análisis técnicos. También se pueden derivar de una serie del gráfico muchas otras fórmulas, como el promedio, la mediana y la desviación estándar. Al especificar una media móvil, cada fórmula puede tener uno o varios parámetros que deberá especificar.  
  
 Cuando se agrega una fórmula de media móvil en modo de diseño, la serie de líneas que se agrega es solo un marcador de posición visual. El gráfico calculará los puntos de datos de cada fórmula durante el procesamiento del informe.  
  
 En [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], no está disponible la compatibilidad integrada para las líneas de tendencia.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## Para agregar una media móvil calculada a una serie del gráfico  
  
1.  Haga clic con el botón secundario en el área **Valores** y, a continuación, haga clic en **Agregar serie calculada**. Se abre el cuadro de diálogo **Propiedades de la serie calculada** .  
  
2.  Seleccione la opción **Media móvil** en la lista desplegable **Fórmula**.  
  
3.  Especifique un valor entero para el **Período** que representa el período de la media móvil.  
  
    > [!NOTE]  
    >  El período es el número de días usado para calcular una media móvil. Si en el eje X no se especifican valores de fecha y hora, el período de tiempo lo representa el número de puntos de datos usados para calcular una media móvil. Si solo hay un punto de datos, la fórmula de la media móvil no se calcula. La media móvil se calcula a partir del segundo punto. Si especifica la opción **Empezar desde el primer punto** , el gráfico iniciará la media móvil en el primer punto. Si solo hay un punto de datos, el punto de la media móvil calculada será idéntico al primer punto de la serie original.  
  
## Vea también  
 [Aplicar formato a un gráfico &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
 [Gráficos &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [Agregar puntos vacíos al gráfico &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/add-empty-points-to-a-chart-report-builder-and-ssrs.md)  
  
  