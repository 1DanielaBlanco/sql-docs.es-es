---
title: Max (MDX) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- MAX
dev_langs:
- kbMDX
helpviewer_keywords:
- Max function [MDX]
ms.assetid: 745c2b3e-022b-471a-ac16-e39ecb3297ea
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 6b309cb1ec89fa7207ba1c12bfcaaa4a14d9f6b6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="max-mdx"></a>Max (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Devuelve el valor máximo de una expresión numérica evaluada sobre un conjunto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Max( Set_Expression [ , Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Argumentos  
 *Set_Expression*  
 Expresión MDX (Expresiones multidimensionales) válida que devuelve un conjunto.  
  
 *Numeric_expression*  
 Expresión numérica válida que suele ser una expresión MDX de las coordenadas de celdas que devuelven un número.  
  
## <a name="remarks"></a>Comentarios  
 Si se especifica una expresión numérica, dicha expresión numérica especificada se evalúa en todo el conjunto y devuelve el valor máximo de esa evaluación. Si no se especifica una expresión numérica, el conjunto especificado se evalúa en el contexto actual de los miembros del conjunto y devuelve el valor máximo de esa evaluación.  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] omite los valores NULL al calcular el valor máximo de un conjunto de números.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente devuelve las ventas mensuales máximas de cada trimestre, subcategoría y país del cubo de Adventure Works.  
  
```  
WITH MEMBER Measures.x AS Max   
   ([Date].[Calendar].CurrentMember.Children  
      , [Measures].[Reseller Order Quantity]  
   )  
SELECT Measures.x ON 0  
,NON EMPTY [Date].[Calendar].[Calendar Quarter]*   
   [Product].[Product Categories].[Subcategory].members *  
   [Geography].[Geography].[Country].Members  
ON 1  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de funciones MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
