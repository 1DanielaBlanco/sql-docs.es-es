---
title: NonEmptyCrossjoin (MDX) | Documentos de Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- NONEMPTYCROSSJOIN
dev_langs:
- kbMDX
helpviewer_keywords:
- NonEmptyCrossjoin function
ms.assetid: 3dc9522d-9126-4f7a-b587-216fa7a06c62
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 54ea9a17d94b73d5423384023d49e4c86771f072
ms.contentlocale: es-es
ms.lasthandoff: 08/02/2017

---
# <a name="nonemptycrossjoin-mdx"></a>NonEmptyCrossjoin (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Devuelve un conjunto que contiene el producto cruzado de uno o más conjuntos, excluidas las tuplas vacías y las que no tienen datos de la tabla de hechos asociada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
NonEmptyCrossjoin(Set_Expression1 [ ,Set_Expression2,...] [,Count ] )  
```  
  
## <a name="arguments"></a>Argumentos  
 *Set_Expression1*  
 Expresión MDX (Expresiones multidimensionales) válida que devuelve un conjunto.  
  
 *Set_Expression2*  
 Expresión MDX (Expresiones multidimensionales) válida que devuelve un conjunto.  
  
 *Count*  
 Expresión numérica válida que especifica el número de conjuntos que serán devueltos.  
  
## <a name="remarks"></a>Comentarios  
 El **NonEmptyCrossjoin** función devuelve el producto cruzado de dos o más conjuntos como un conjunto, excluidas las tuplas vacías o sin datos proporcionados por las tablas de hechos subyacente. Debido a cómo el **NonEmptyCrossjoin** función, todas las calculadas miembros se excluyen automáticamente.  
  
 Si *recuento* no se especifica, la función cross combina todos los conjuntos especificados y excluye los miembros vacíos del conjunto resultante. Si se especifica un número de conjuntos, la función realiza combinaciones cruzadas de los números de los conjuntos especificados, comenzando con el primer conjunto especificado. El **NonEmptyCrossjoin** función utiliza los conjuntos restantes que se especifican en los conjuntos especificados subsiguientes, pero que no han sido cruzado para determinar qué miembros se consideran no vacíos en el conjunto combinado de forma cruzada resultante. El **NonEmptyCrossjoin** función respeta el **NON_EMPTY_BEHAVIOR** configuración de las medidas calculadas.  
  
> [!IMPORTANT]  
>  Esta función está desusada y no debería utilizarla; solo se conserva para mantener la compatibilidad con las versiones anteriores. En su lugar, debe utilizar el [Exists (MDX)](../mdx/exists-mdx.md) función con el argumento de nombre de grupo de medida o la [NonEmpty (MDX)](../mdx/nonempty-mdx.md) (función).  
  
## <a name="see-also"></a>Vea también  
 [Referencia de funciones MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

