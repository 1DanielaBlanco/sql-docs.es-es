---
title: Página filtros, cuadros de diálogo de gráfico (generador de informes y SSRS) | Documentos de Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rtp.rptdesigner.categorygroupproperties.filters.f1
- "10409"
- sql12.rtp.rptdesigner.seriesgroupproperties.filters.f1
- "10401"
- sql12.rtp.rptdesigner.chartproperties.filters.f1
- "10165"
ms.assetid: fab97b2f-d53f-42f2-900c-c159653d89ed
caps.latest.revision: 14
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 5b695b45a43f388a7dabf64bad327404ef4f6510
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36197099"
---
# <a name="filters-page-chart-dialog-boxes-report-builder-and-ssrs"></a>Cuadros de diálogo de Gráfico, página Filtros (Generador de informes y SSRS)
  Haga clic en **Filtros** en  
  
-   el cuadro de diálogo**Propiedades del grupo de categorías** para filtrar los puntos de datos de una serie que ha sido agrupada por categoría.  
  
-   El cuadro de diálogo**Chart Properties** para definir las opciones de filtrado para el gráfico.  
  
-   El cuadro de diálogo**Propiedades del grupo de series** para limitar el número de series del grupo seleccionado.  
  
## <a name="options"></a>Opciones  
 **Agregar**  
 Haga clic en esta opción para agregar una nueva cláusula de filtro a la lista.  
  
 **Eliminar**  
 Haga clic en esta opción para eliminar de la lista la cláusula de filtro seleccionada.  
  
 **Flecha arriba**  
 Haga clic en esta opción para mover el filtro seleccionado hacia arriba en la lista.  
  
 **Flecha abajo**  
 Haga clic en esta opción para mover el filtro seleccionado hacia abajo en la lista.  
  
 **Expresión**  
 Escriba o elija la expresión a la que desea aplicar un filtro. Haga clic en el botón Expresión (**fx**) para editar la expresión.  
  
 **Data type**  
 Elija el tipo de datos para **Valor**. Si es posible, elija un tipo de datos que coincida con el tipo de datos de **Expresión**.  
  
 Los valores de **Expresión** y de **Valor** deben devolver el mismo tipo de datos. Por ejemplo, si **Expresión** se establece en un campo que tiene el tipo de datos System.Int32 y **Valor** se establece en 7, en la lista desplegable, elija **Integer**.  
  
 Si la opción de tipos de datos que necesita no está en la lista desplegable, escriba una expresión que convierta el valor al tipo de datos correcto. Para más información, vea [Ejemplos de ecuaciones de filtro &#40;Generador de informes y SSRS&#41;](report-design/filter-equation-examples-report-builder-and-ssrs.md).  
  
 **Operador**  
 Elija el operador que se va a utilizar para comparar la expresión y el valor.  
  
 **Value**  
 Escriba la expresión o el valor respecto al cual se va a evaluar la expresión de **Expresión**.  
  
## <a name="see-also"></a>Vea también  
 [Agregar filtros de conjunto de datos, filtros de región de datos y filtros de grupo &#40;Generador de informes y SSRS&#41;](report-design/add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Ejemplos de expresiones &#40;Generador de informes y SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md)   
 [Expresiones &#40;Generador de informes y SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md)   
 [Filtrar, agrupar y ordenar datos &#40;el generador de informes SSRS&#41;](report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  