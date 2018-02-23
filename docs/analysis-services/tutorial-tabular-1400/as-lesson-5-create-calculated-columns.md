---
title: "Lección de Analysis Services tutorial 5: crear columnas calculadas | Documentos de Microsoft"
description: "Describe cómo crear columnas calculadas en el proyecto de tutorial de Analysis Services."
ms.prod_service: analysis-services, azure-analysis-services
services: analysis-services
ms.suite: pro-bi
documentationcenter: 
author: Minewiskan
manager: kfile
editor: 
tags: 
ms.assetid: 
ms.service: analysis-services
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: na
ms.date: 02/20/2018
ms.author: owend
ms.openlocfilehash: daed9d78d8b88bcf8088d8b19b4a34ba3a9f16c0
ms.sourcegitcommit: 7ed8c61fb54e3963e451bfb7f80c6a3899d93322
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2018
---
# <a name="create-calculated-columns"></a>Crear columnas calculadas

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

En esta lección, creará datos en el modelo agregando columnas calculadas. Puede crear columnas calculadas (como columnas personalizadas) cuando se usa obtener datos, mediante el Editor de consultas o más adelante en el tipo de diseñador de modelo hace aquí. Para obtener más información, consulte [columnas calculadas](../tabular-models/ssas-calculated-columns.md).
  
Crear cinco nuevas columnas calculadas en tres tablas diferentes. Los pasos son ligeramente diferentes para cada tarea que muestra varias maneras para crear las columnas, cambiarles el nombre y colocarlos en varias ubicaciones en una tabla.  

En esta lección también es donde se utilizar expresiones de análisis de datos (DAX). DAX es un lenguaje especial para crear expresiones de fórmula altamente personalizables para los modelos tabulares. En este tutorial, DAX se usa para crear columnas calculadas, medidas y filtros de rol. Para obtener más información, consulte [DAX en modelos tabulares](../tabular-models/understanding-dax-in-tabular-models-ssas-tabular.md). 
  
Tiempo estimado para completar esta lección: **15 minutos**  
  
## <a name="prerequisites"></a>Requisitos previos  

Este artículo forma parte de un tutorial de modelado tabular, que se debe completar en orden. Antes de realizar las tareas en esta lección, debe haber completado la lección anterior: [lección 4: crear relaciones](../tutorial-tabular-1400/as-lesson-4-create-relationships.md). 
  
## <a name="create-calculated-columns"></a>Crear columnas calculadas  
  
#### <a name="create-a-monthcalendar-calculated-column-in-the-dimdate-table"></a>Crear una columna calculada MonthCalendar en la tabla DimDate  
  
1.  Haga clic en el **modelo** menú > **vista de modelo** > **vista de datos**.  
  
    Las columnas calculadas solo se pueden crear mediante el diseñador de modelos en la Vista de datos.  
  
2.  En el Diseñador de modelos, haga clic en el **DimDate** tabla (pestaña).  
  
3.  Haga clic en el **CalendarQuarter** encabezado de columna y, a continuación, haga clic en **Insertar columna**.  
  
    Una nueva columna denominada **Columna calculada 1** se inserta a la izquierda de la columna **Calendar Quarter** .  
  
4.  En la barra de fórmulas situada encima de la tabla, escriba la siguiente fórmula DAX: Autocompletar le ayuda a escribir los nombres completos de columnas y tablas y enumera las funciones que están disponibles.  
  
    ```  
    =RIGHT(" " & FORMAT([MonthNumberOfYear],"#0"), 2) & " - " & [EnglishMonthName]  
    ``` 
  
    Después, los valores se rellenan para todas las filas de la columna calculada. Si se desplaza hacia abajo por la tabla, verá las filas pueden tener valores diferentes para esta columna se basa en los datos de cada fila.    
  
5.  Cambiar el nombre de esta columna para **MonthCalendar**. 

    ![as-lesson5-newcolumn](../tutorial-tabular-1400/media/as-lesson5-newcolumn.png) 
  
MonthCalendar calcula la columna proporciona un nombre que se puede ordenar por mes.  
  
#### <a name="create-a-dayofweek-calculated-column-in-the-dimdate-table"></a>Crear una columna calculada DayOfWeek en la tabla DimDate  
  
1.  Con el **DimDate** tabla sigue activa, haga clic el **columna** menú y, a continuación, haga clic en **Agregar columna**.  
  
2.  En la barra de fórmulas, escriba la fórmula siguiente:  
    
    ```
    =RIGHT(" " & FORMAT([DayNumberOfWeek],"#0"), 2) & " - " & [EnglishDayNameOfWeek]  
    ```
    
    Cuando haya terminado de crear la fórmula, presione ENTRAR. Se agrega la columna nueva a la derecha de la tabla.  
  
3.  Cambiar el nombre de la columna a **DayOfWeek**.  
  
4.  Haga clic en el encabezado de columna y, a continuación, arrastre la columna entre la **EnglishDayNameOfWeek** columna y la **DayNumberOfMonth** columna.  
  
    > [!TIP]  
    > El movimiento de columnas en la tabla simplifica la navegación.  
  
El DayOfWeek calcula la columna proporciona un nombre ordenable del día de la semana.  
  
#### <a name="create-a-productsubcategoryname-calculated-column-in-the-dimproduct-table"></a>Crear una columna calculada ProductSubcategoryName en la tabla DimProduct  
  
  
1.  En el **DimProduct** tabla, desplácese hasta el extremo derecho de la tabla. Observe que la columna situada más a la derecha se denomina **Agregar columna** (en cursiva); haga clic en el encabezado de columna.  
  
2.  En la barra de fórmulas, escriba la fórmula siguiente:  
    
    ```
    =RELATED('DimProductSubcategory'[EnglishProductSubcategoryName])  
    ```
  
3.  Cambiar el nombre de la columna a **ProductSubcategoryName**.  
  
La columna calculada ProductSubcategoryName se utiliza para crear una jerarquía en la tabla DimProduct, que incluye datos de la columna EnglishProductSubcategoryName en la tabla DimProductSubcategory. Las jerarquías no pueden abarcar más de una tabla. Crear jerarquías más adelante en la lección 9.  
  
#### <a name="create-a-productcategoryname-calculated-column-in-the-dimproduct-table"></a>Crear una columna calculada ProductCategoryName en la tabla DimProduct  
  
1.  Con el **DimProduct** tabla sigue activa, haga clic el **columna** menú y, a continuación, haga clic en **Agregar columna**.  
  
2.  En la barra de fórmulas, escriba la fórmula siguiente:  
  
    ```
    =RELATED('DimProductCategory'[EnglishProductCategoryName]) 
    ```
    
3.  Cambiar el nombre de la columna a **ProductCategoryName**.  
  
La columna calculada ProductCategoryName se utiliza para crear una jerarquía en la tabla DimProduct, que incluye datos de la columna EnglishProductCategoryName en la tabla DimProductCategory. Las jerarquías no pueden abarcar más de una tabla.  
  
#### <a name="create-a-margin-calculated-column-in-the-factinternetsales-table"></a>Crear una columna calculada margen en la tabla FactInternetSales  
  
1.  En el Diseñador de modelos, seleccione la **FactInternetSales** tabla.  
  
2.  Crear una nueva columna calculada entre el **SalesAmount** columna y la **TaxAmt** columna.  
  
3.  En la barra de fórmulas, escriba la fórmula siguiente:  
  
    ```
    =[SalesAmount]-[TotalProductCost]
    ``` 

4.  Cambie el nombre de la columna a **Margen**.  
 
      ![as-lesson5-newmargin](../tutorial-tabular-1400/media/as-lesson5-newmargin.png)
      
    La columna calculada margen se utiliza para analizar los márgenes de beneficios de cada venta.  
  
## <a name="whats-next"></a>¿Qué sigue?

[Lección 6: Crear medidas](../tutorial-tabular-1400/as-lesson-6-create-measures.md).
  
  
  
