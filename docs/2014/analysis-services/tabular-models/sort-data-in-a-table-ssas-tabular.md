---
title: Ordenar datos en una tabla (SSAS Tabular) | Documentos de Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5fa6ad56-bf68-4aac-a226-52556173b7e2
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 156f75856c371914c41519a1ce577c02e4773679
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36107491"
---
# <a name="sort-data-in-a-table-ssas-tabular"></a>Ordenar datos en una tabla (SSAS tabular)
  Puede ordenar los datos por texto (de A a Z o de Z a A) y los números (de menor a mayor o viceversa) en una o varias columnas.  
  
### <a name="to-sort-the-data-in-a-table-based-on-a-text-column"></a>Para ordenar los datos de una tabla según una columna de texto  
  
1.  En el Diseñador de modelos, seleccione una columna de datos alfanuméricos o un rango de celdas de una columna, o asegúrese de que la celda activa está en una columna de la tabla que contenga datos alfanuméricos; a continuación, haga clic en la flecha del encabezado de la columna que desea usar para el filtrado.  
  
2.  En el menú Autofiltro, siga uno de estos procedimientos:  
  
    -   Para clasificar en orden alfanumérico ascendente, haga clic en **Ordenar de A a Z**.  
  
    -   Para clasificar en orden alfanumérico descendente, haga clic en **Ordenar de Z a A.**  
  
    > [!NOTE]  
    >  En algunos casos, los datos importados de otra aplicación podrían tener espacios iniciales incrustados antes de los datos. Debe quitar los espacios iniciales para ordenar los datos correctamente.  
  
### <a name="to-sort-the-data-in-a-table-based-on-a-numeric-column"></a>Para ordenar los datos en una tabla según una columna numérica  
  
1.  En el Diseñador de modelos, seleccione una columna de datos alfanuméricos o un rango de celdas de una columna, o asegúrese de que la celda activa está en una columna de la tabla que contenga datos alfanuméricos; a continuación, haga clic en la flecha del encabezado de la columna que desea usar para el filtrado.  
  
2.  En el menú Autofiltro, siga uno de estos procedimientos:  
  
    -   Para ordenar de los números bajos a los números altos, haga clic en **Ordenar de menor a mayor**.  
  
    -   Para ordenar de los números altos a los números bajos, haga clic en **Ordenar de mayor a menor**.  
  
    > [!NOTE]  
    >  Si los resultados no son los que esperaba, la columna podría contener números almacenados como texto y no como números. Por ejemplo, los números negativos importados de algunos sistemas contables o un número escrito con un símbolo ' inicial (apóstrofo) se almacenan en forma de texto.  
  
## <a name="see-also"></a>Vea también  
 [Filtrar y ordenar datos &#40;SSAS Tabular&#41;](../filter-and-sort-data-ssas-tabular.md)   
 [Las perspectivas &#40;SSAS Tabular&#41;](perspectives-ssas-tabular.md)   
 [Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md)  
  
  