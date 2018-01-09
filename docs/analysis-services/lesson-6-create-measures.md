---
title: "Lección 7: Crear medidas | Documentos de Microsoft"
ms.custom: 
ms.date: 03/27/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: 01bd2ad7-09b7-49ae-ad80-83f25da301aa
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: f3eaadefd65c49f86e4081ba0547f5ca05ae0514
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="lesson-6-create-measures"></a>Lección 6: Crear medidas
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

En esta lección, creará medidas para incluirlas en su modelo. De forma similar a las columnas calculadas que creó en la lección anterior, una medida es un cálculo creado usando una fórmula DAX. Sin embargo, a diferencia de las columnas calculadas, las medidas se evalúan en función de un *filtro*seleccionado por el usuario; por ejemplo, una columna o una segmentación de datos determinada agregada al campo Etiquetas de filas en una tabla dinámica. A continuación, la medida aplicada calcula un valor para cada celda del filtro. Las medidas son cálculos eficaces y flexibles que deseará incluir en casi todos los modelos tabulares para realizar cálculos dinámicos sobre datos numéricos. Para obtener más información, consulte [medidas](../analysis-services/tabular-models/measures-ssas-tabular.md).  
  
Para crear medidas, usará el *cuadrícula de medidas*. De manera predeterminada, cada tabla tiene una cuadrícula de medidas vacía, pero normalmente no creará medidas para todas las tablas. La cuadrícula de medidas aparece debajo de una tabla en el diseñador de modelos en la vista de datos. Para mostrar u ocultar la cuadrícula de medidas de una tabla, haga clic en el menú **Tabla** y en **Mostrar cuadrícula de medidas**.  
  
Puede crear una medida haciendo clic en una celda vacía de la cuadrícula de medidas y escribiendo después una fórmula DAX en la barra de fórmulas. Al hacer clic en ENTRAR para completar la fórmula, la medida aparecerá en la celda. También puede crear medidas mediante una función de agregación estándar. Para ello, haga clic en una columna y, después, en el botón de autosuma (**∑**) en la barra de herramientas. Las medidas creadas mediante la característica de Autosuma aparecerán en la celda de cuadrícula de medidas directamente debajo de la columna, pero se pueden mover.  
  
En esta lección, creará medidas escribiendo una fórmula DAX en la barra de fórmulas y usando la característica de autosuma.  
  
Tiempo estimado para completar esta lección: **30 minutos**  
  
## <a name="prerequisites"></a>Prerequisites  
Este tema es parte de un tutorial de creación de modelos tabulares, que se debe completar en orden. Antes de realizar las tareas en esta lección, debe haber completado la lección anterior: [lección 5: crear columnas calculadas](../analysis-services/lesson-5-create-calculated-columns.md).  
  
## <a name="create-measures"></a>Crear medidas  
  
#### <a name="to-create-a-dayscurrentquartertodate-measure-in-the-dimdate-table"></a>Para crear una medida DaysCurrentQuarterToDate en la tabla DimDate  
  
1.  En el Diseñador de modelos, haga clic en el **DimDate** tabla.  
  
2.  En la cuadrícula de medidas, haga clic en la celda vacía superior izquierda.  
  
3.  En la barra de fórmulas, escriba la fórmula siguiente:  
  
    ```
    DaysCurrentQuarterToDate:=COUNTROWS( DATESQTD( 'DimDate'[Date])) 
    ```
  
    Observe que la celda superior izquierda contiene ahora un nombre de medida, **DaysCurrentQuarterToDate**, seguido del resultado, **92**.
    
      ![como-tabular-lesson6-newmeasure](../analysis-services/media/as-tabular-lesson6-newmeasure.png) 
    
    A diferencia de las columnas calculadas, con fórmulas de medida puede escribir el nombre de medida, seguido por una coma, seguida de la expresión de la fórmula.

  
#### <a name="to-create-a-daysincurrentquarter-measure-in-the-dimdate-table"></a>Para crear una medida DaysInCurrentQuarter en la tabla DimDate  
  
1.  Con el **DimDate** tabla sigue activa en el Diseñador de modelos, en la cuadrícula de medidas, haga clic en la celda vacía situada debajo de la medida que acaba de crear.  
  
2.  En la barra de fórmulas, escriba la fórmula siguiente:  
  
    ```
    DaysInCurrentQuarter:=COUNTROWS( DATESBETWEEN( 'DimDate'[Date], STARTOFQUARTER( LASTDATE('DimDate'[Date])), ENDOFQUARTER('DimDate'[Date])))
    ```
  
    Al crear un coeficiente de comparación entre un período incompleto y el período anterior, la fórmula debe tener en cuenta la parte del período que ha transcurrido y compararla con la misma parte del período anterior. En este caso, [DaysCurrentQuarterToDate] / [DaysInCurrentQuarter] ofrece la proporción transcurrido en el período actual.  
  
#### <a name="to-create-an-internetdistinctcountsalesorder-measure-in-the-factinternetsales-table"></a>Para crear una medida InternetDistinctCountSalesOrder en la tabla FactInternetSales  
  
1.  Haga clic en el **FactInternetSales** tabla.   
  
2.  Haga clic en el **SalesOrderNumber** encabezado de columna.  
  
3.  En la barra de herramientas, haga clic en la flecha abajo situada junto al botón de autosuma (**∑**) y, después, seleccione **DistinctCount**.  
  
    La característica de autosuma crea automáticamente una medida para la columna seleccionada usando la fórmula estándar de agregación DistinctCount.  
    
       ![como-tabular-lesson6-newmeasure2](../analysis-services/media/as-tabular-lesson6-newmeasure2.png)
  
4.  En la cuadrícula de medidas, haga clic en la nueva medida y, a continuación, en la **propiedades** ventana, en **nombre de medida**, cambiar el nombre de la medida a **InternetDistinctCountSalesOrder**. 
 
  
#### <a name="to-create-additional-measures-in-the-factinternetsales-table"></a>Para crear medidas adicionales en la tabla FactInternetSales  
  
1.  Con la característica de autosuma, cree y asigne un nombre a las medidas siguientes:  
  
    |Nombre de medida|columna|Autosuma (∑)|Fórmula|  
    |----------------|----------|-----------------|-----------|  
    |InternetOrderLinesCount|SalesOrderLineNumber|Count|=CountA([SalesOrderLineNumber])|  
    |InternetTotalUnits|OrderQuantity|SUM|=SUM([OrderQuantity])|  
    |InternetTotalDiscountAmount|DiscountAmount|SUM|=SUM([DiscountAmount])|  
    |InternetTotalProductCost|TotalProductCost|SUM|=SUM([TotalProductCost])|  
    |InternetTotalSales|SalesAmount|SUM|=SUM([SalesAmount])|  
    |InternetTotalMargin|Margen|SUM|=SUM([Margen])|  
    |InternetTotalTaxAmt|TaxAmt|SUM|=SUM([TaxAmt])|  
    |InternetTotalFreight|Freight|SUM|=SUM([Cargos])|  
  
2.  Haciendo clic en una celda vacía de la cuadrícula de medidas y mediante el uso de la barra de fórmulas, cree y asigne nombre a las medidas siguientes en orden:  
  
      ```
      InternetPreviousQuarterMargin:=CALCULATE([InternetTotalMargin],PREVIOUSQUARTER('DimDate'[Date]))
      ```
      
      ```
      InternetCurrentQuarterMargin:=TOTALQTD([InternetTotalMargin],'DimDate'[Date])
      ```
  
      ```
      InternetPreviousQuarterMarginProportionToQTD:=[InternetPreviousQuarterMargin]*([DaysCurrentQuarterToDate]/[DaysInCurrentQuarter])
      ```
  
      ```
      InternetPreviousQuarterSales:=CALCULATE([InternetTotalSales],PREVIOUSQUARTER('DimDate'[Date]))
      ```
  
      ```
      InternetCurrentQuarterSales:=TOTALQTD([InternetTotalSales],'DimDate'[Date])
      ```
      
      ```
      InternetPreviousQuarterSalesProportionToQTD:=[InternetPreviousQuarterSales]*([DaysCurrentQuarterToDate]/[DaysInCurrentQuarter])
      ```
  
Las medidas creadas para la tabla FactInternetSales se pueden utilizar para analizar datos financieros críticos como ventas, costos y margen de beneficio para los elementos definidos por el filtro seleccionado de usuario.  
  
## <a name="whats-next"></a>¿Qué sigue?
Vaya a la siguiente lección: [lección 7: crear indicadores clave de rendimiento](../analysis-services/lesson-7-create-key-performance-indicators.md).  

  
