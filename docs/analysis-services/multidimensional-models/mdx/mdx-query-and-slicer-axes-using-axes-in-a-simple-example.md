---
title: Con ejes de consulta y segmentador en un ejemplo Simple (MDX) | Documentos de Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- slicer axis
- query axis [MDX]
ms.assetid: 85bcb26f-5971-4153-b334-61f8d8b475b5
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 810e4ef20ff718f6f560768f7c14cf19d1a81230
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="mdx-query-and-slicer-axes---using-axes-in-a-simple-example"></a>Consulta MDX y ejes de segmentación de datos - mediante ejes en un ejemplo Simple
  En este sencillo ejemplo se ilustran los conceptos en los que se basa la especificación y el uso de los ejes de consulta y segmentador.  
  
## <a name="the-cube"></a>Cubo  
 Un cubo, denominado TestCube, tiene dos dimensiones simples: Route y Time. Cada dimensión solo tiene una jerarquía de usuario, denominadas Route y Time respectivamente. Puesto que las medidas del cubo son parte de la dimensión Measures, este cubo tiene tres dimensiones en total.  
  
## <a name="the-query"></a>Consulta  
 La consulta va a proporcionar una matriz en la que la medida Packages se puede comparar con rutas (routes) y tiempos (times).  
  
 En la siguiente consulta MDX de ejemplo, las jerarquías Route y Time se utilizan como ejes de la consulta y la dimensión Measures como eje segmentador. La función [Members](../../../mdx/members-set-mdx.md) indica que MDX usará los miembros de la jerarquía o el nivel para generar un conjunto. El uso de la función **Members** implica que no es necesario especificar explícitamente cada miembro de una jerarquía o un nivel específicos de una consulta MDX.  
  
```  
SELECT  
   { Route.nonground.Members } ON COLUMNS,  
   { Time.[1st half].Members } ON ROWS  
FROM TestCube  
WHERE ( [Measures].[Packages] )  
```  
  
## <a name="the-results"></a>Resultado  
 El resultado es una cuadrícula que identifica el valor de la medida Packages en cada intersección de las dimensiones de eje COLUMNS y ROWS. En la tabla siguiente se muestra el aspecto que tendría la cuadrícula.  
  
||air|sea|  
|-|---------|---------|  
|1st quarter|60|50|  
|2nd quarter|45|45|  
  
## <a name="see-also"></a>Vea también  
 [Especificar el contenido de un eje de consulta &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)   
 [Especificar el contenido de un eje de división en sectores &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)  
  
  

