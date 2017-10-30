---
title: Los miembros (Set) (MDX) | Documentos de Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Members
dev_langs:
- kbMDX
helpviewer_keywords:
- Members function
ms.assetid: 0c4d5bb9-500b-47ce-b7fc-f5a10e2400e0
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 4430d24665eb791b8567fa83e7793c64727fd88f
ms.contentlocale: es-es
ms.lasthandoff: 08/02/2017

---
# <a name="members-set-mdx"></a>Members (Set) (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve el conjunto de miembros en una dimensión, nivel o jerarquía.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Hierarchy expression syntax  
Hierarchy_Expression.Members  
  
Level expression Syntax  
Level_Expression.Members  
```  
  
## <a name="arguments"></a>Argumentos  
 *Hierarchy_Expression*  
 Expresión MDX válida que devuelve una jerarquía.  
  
 *Level_Expression*  
 Expresión MDX válida que devuelve un nivel.  
  
## <a name="remarks"></a>Comentarios  
 Si se especifica una expresión de jerarquía, el **Members (conjunto)** función devuelve el conjunto de todos los miembros de la jerarquía especificada, sin incluir los miembros calculados. Para obtener el conjunto de todos los miembros, calculado o en caso contrario, en una jerarquía, utilice la [AllMembers &#40; MDX &#41; ](../mdx/allmembers-mdx.md) (función)  
  
 Si se especifica una expresión de nivel, la **Members (conjunto)** función devuelve el conjunto de todos los miembros del nivel especificado.  
  
> [!IMPORTANT]  
>  Cuando una dimensión contiene solo una única jerarquía visible, se puede hacer referencia a la jerarquía por el nombre de la dimensión o por el nombre de la jerarquía, dado que el nombre de la dimensión en este escenario se resuelve en su única jerarquía visible. Por ejemplo, Measures.Members es una expresión MDX válida debido a que se resuelve en la única jerarquía de la dimensión Measures.  
  
## <a name="examples"></a>Ejemplos  
 El ejemplo siguiente devuelve el conjunto de todos los miembros de la jerarquía Calendar Year del cubo Adventure Works.  
  
```  
SELECT   
   [Date].[Calendar].[Calendar Year].Members ON 0  
FROM  
   [Adventure Works]  
  
```  
  
 El siguiente ejemplo devuelve las cantidades de pedido de 2003 para cada miembro del nivel `[Product].[Products].[Product Line]`. El **miembros** función devuelve un conjunto que representa todos los miembros del nivel.  
  
```  
SELECT   
   {Measures.[Order Quantity]} ON COLUMNS,  
   [Product].[Product Line].[Product Line].Members ON ROWS  
FROM  
   [Adventure Works]  
WHERE  
   {[Date].[Calendar Year].[Calendar Year].&[2003]}  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de funciones MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)   
 [Referencia de funciones MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

