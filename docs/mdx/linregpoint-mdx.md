---
title: LinRegPoint (MDX) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- LINREGPOINT
dev_langs:
- kbMDX
helpviewer_keywords:
- LinRegPoint function
ms.assetid: 28298d7c-2b8a-4423-ae52-9c2d6f0f0064
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 37c0f4b4ef73ff14d8c0f46208b94d1b96d995e7
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="linregpoint-mdx"></a>LinRegPoint (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Calcula la regresión lineal de un conjunto y devuelve el valor de la *intercepción* en la recta de regresión y = ax + b. para un determinado valor de x.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
LinRegPoint(Slice_Expression_x, Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>Argumentos  
 *Slice_Expression_x*  
 Expresión numérica válida que suele ser una expresión MDX (Expresiones multidimensionales) de las coordenadas de celdas que devuelven un número que representa los valores del eje segmentador.  
  
 *Set_Expression*  
 Expresión MDX (Expresiones multidimensionales) válida que devuelve un conjunto.  
  
 *Numeric_Expression_y*  
 Expresión numérica válida que suele ser una expresión MDX de las coordenadas de celdas que devuelven un número que representa los valores del eje Y.  
  
 *Numeric_Expression_x*  
 Expresión numérica válida que suele ser una expresión MDX de las coordenadas de celdas que devuelven un número que representa los valores del eje X.  
  
## <a name="remarks"></a>Comentarios  
 La regresión lineal, que utiliza el método de mínimos cuadrados, calcula la ecuación de la recta de regresión (es decir, la de mejor ajuste para un conjunto de puntos). La recta de regresión tiene la siguiente ecuación, donde una es la pendiente y b es la intersección:  
  
 y = ax+b  
  
 El **LinRegPoint** función evalúa el conjunto especificado con la segunda expresión numérica para obtener los valores del eje y. A continuación, la función evalúa el conjunto especificado con la tercera expresión numérica, si se especifica, para obtener los valores del eje X. Si no se especifica la tercera expresión numérica, la función utiliza el contexto actual de las celdas del conjunto especificado como valores para el eje X. No se especifica el argumento del eje x se suele usar con la dimensión de tiempo.  
  
 Una vez que se ha calculado la recta de regresión lineal, se calcula el valor de la ecuación para la primera expresión numérica y, a continuación, se devuelve.  
  
> [!NOTE]  
>  El **LinRegPoint** función omite las celdas vacías o celdas que contienen texto. No obstante, la función incluye celdas con valor de cero.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente devuelve el valor predicho de las ventas por unidad de los últimos diez períodos según la relación estadística entre Unit Sales y Store Sales.  
  
```  
LinRegPoint([Measures].[Unit Sales],LastPeriods(10),[Measures].[Unit Sales],[Measures].[Store Sales])  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de funciones MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
