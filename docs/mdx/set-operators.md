---
title: Operadores de conjuntos | Documentos de Microsoft
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
dev_langs:
- kbMDX
helpviewer_keywords:
- set operators [MDX]
ms.assetid: 83500d2e-44b3-49eb-a221-3ce5a58277a5
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 161234bf6f72beb7548cfb5dc7ad3602f4903110
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="set-operators"></a>Operadores de conjuntos
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  En las expresiones multidimensionales (MDX), los operadores de conjuntos ejecutan operaciones en miembros o conjuntos y devuelven un conjunto. Por lo general, los operadores de conjuntos se utilizan como alternativa a las distintas funciones de conjuntos en expresiones MDX.  
  
 MDX es compatible con los operadores de conjuntos que se indican en la siguiente tabla.  
  
|Operador|Description|  
|--------------|-----------------|  
|[- (Excepto)](../mdx/except-mdx-operator.md)|Devuelve la diferencia entre dos conjuntos y elimina los miembros duplicados.<br /><br /> Este operador es funcionalmente equivalente a la [excepto](../mdx/except-mdx-function.md) (función).|  
|[* (Combinaciones cruzadas)](../mdx/crossjoin-mdx-operator-reference.md)|Devuelve el producto cruzado de dos conjuntos.<br /><br /> Este operador es funcionalmente equivalente a la [Crossjoin](../mdx/crossjoin-mdx.md) función.|  
|[: (Intervalo)](../mdx/range-mdx.md)|Devuelve un conjunto en su orden natural, con dos miembros especificados como extremos y todos los miembros entre ellos incluidos como miembros del conjunto.|  
|[+ (Unión)](../mdx/union-mdx-operator-reference.md)|Devuelve la unión de dos conjuntos y excluye los miembros duplicados.<br /><br /> Este operador es funcionalmente equivalente a la [unión &#40;MDX&#41; ](../mdx/union-mdx.md) (función).|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de funciones MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)   
 [Referencia de operadores MDX &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [Operadores &#40;sintaxis MDX&#41;](../mdx/operators-mdx-syntax.md)  
  
  
