---
title: Usar expresiones de conjunto | Documentos de Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: kbMDX
helpviewer_keywords:
- expressions [MDX], set
- tuples
- set expressions [MDX]
ms.assetid: 88d65872-0cbe-4c95-b36f-e1aa4ac8ed07
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 441931651dbe54b9205a5e02da808f35a2b34844
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="using-set-expressions"></a>Usar expresiones de conjunto
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Un conjunto está formado por una lista ordenada de cero o más tuplas. Los conjuntos que no contienen tuplas se denominan conjuntos vacíos.  
  
 La expresión completa de un conjunto consta de cero o más tuplas especificadas explícitamente entre corchetes:  
  
 {[{ *Tuple_expression* | *expresión_miembro* } [, { *Tuple_expression* | *expresión_miembro* }]...]}  
  
 Las expresiones de miembro especificadas en expresiones de conjunto se convierten en expresiones de tupla de un miembro.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestran dos expresiones de conjunto que se utilizan en los ejes de columnas y de filas de una consulta:  
  
 `SELECT`  
  
 `{[Measures].[Internet Sales Amount], [Measures].[Internet Tax Amount]} ON COLUMNS,`  
  
 `{([Product].[Product Categories].[Category].&[4], [Date].[Calendar].[Calendar Year].&[2004]),`  
  
 `([Product].[Product Categories].[Category].&[1], [Date].[Calendar].[Calendar Year].&[2003]),`  
  
 `([Product].[Product Categories].[Category].&[3], [Date].[Calendar].[Calendar Year].&[2004])}`  
  
 `ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 En el eje de columnas, el conjunto  
  
 {[Measures].[Internet Sales Amount], [Measures].[Internet Tax Amount]}  
  
 está compuesto de dos miembros de dimensión Measures. En el eje de filas, el conjunto  
  
 {([Product].[Product Categories].[Category].&[4], [Date].[Calendar].[Calendar Year].&[2004]),  
  
 ([Product].[Product Categories].[Category].&[1], [Date].[Calendar].[Calendar Year].&[2003]),  
  
 ([Product].[Product Categories].[Category].&[3], [Date].[Calendar].[Calendar Year].&[2004])}  
  
 está compuesto de tres tuplas, cada una de las cuales contiene dos referencias explícitas a miembros de la jerarquía Product Categories de la dimensión Product y de la jerarquía Calendar de la dimensión Date.  
  
 Para obtener ejemplos de funciones que devuelven conjuntos, vea [trabajar con miembros, tuplas y conjuntos de &#40; MDX &#41; ](../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md).  
  
## <a name="see-also"></a>Vea también  
 [Expresiones &#40; MDX &#41;](../mdx/expressions-mdx.md)  
  
  
