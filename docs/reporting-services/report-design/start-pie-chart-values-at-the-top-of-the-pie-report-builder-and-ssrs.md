---
title: "Iniciar los valores del gr&#225;fico circular desde la parte superior del gr&#225;fico (Generador de informes y SSRS) | Microsoft Docs"
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
ms.assetid: d0e6fb59-ca4e-4d70-97cb-0ad183da21d3
caps.latest.revision: 7
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 7
---
# Iniciar los valores del gr&#225;fico circular desde la parte superior del gr&#225;fico (Generador de informes y SSRS)
En los gráficos circulares de los informes paginados de [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)], el primer valor del conjunto de datos se inicia de forma predeterminada en 90 grados desde la parte superior del círculo. 

![generador-informes-gráfico-circular-inicia-en-90](../../reporting-services/media/report-builder-pie-chart-start-at-90.png)

*Los valores del gráfico se inician en 90 grados.*

En su lugar, podría interesarle que el primer valor se inicie en la parte superior. 

![generador-informes-gráfico-circular-inicia-parte-superior](../../reporting-services/media/report-builder-pie-chart-start-at-top.png)

*Los valores del gráfico se inician en la parte superior del gráfico.*
  
## Iniciar el gráfico circular desde la parte superior del círculo  
  
1.  Haga clic en el círculo.  
  
2.  Si el panel **Propiedades** no está abierto, en la pestaña **Ver** haga clic en **Propiedades**.  
  
3.  En el panel **Propiedades** , en **Atributos personalizados**, cambie **PieStartAngle** de **0** a **270**.  
  
4.  Haga clic en **Ejecutar** para obtener una vista previa del informe.  
  
 El primer valor se inicia ahora en la parte superior del gráfico circular.  
  
## Vea también  
 [Aplicar formato a un gráfico &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
 [Gráficos circulares &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)  
  
  