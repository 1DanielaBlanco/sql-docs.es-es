---
title: IsAncestor (MDX) | Documentos de Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ISANCESTOR
dev_langs: kbMDX
helpviewer_keywords: IsAncestor function
ms.assetid: 49d2fcdf-8d9a-4c79-bd00-4910ea149141
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 1674a5edccc74db8561a62e550e0e4102e26d7af
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/27/2017
---
# <a name="isancestor-mdx"></a>IsAncestor (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Informa de si un miembro especificado es un antecesor de otro miembro especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
IsAncestor(Member_Expression1, Member_Expression2)   
```  
  
## <a name="arguments"></a>Argumentos  
 *Member_Expression1*  
 Expresión MDX válida que devuelve un miembro.  
  
 *Member_Expression2*  
 Expresión MDX válida que devuelve un miembro.  
  
## <a name="remarks"></a>Comentarios  
 El **IsAncestor** función devuelve **true** si el primer miembro especificado es un antecesor del segundo miembro especificado. En caso contrario, la función devuelve **false**.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente devuelve **true** si [Date]. [ Fiscal]. CurrentMember es un antecesor de January de 2003:  
  
 `WITH MEMBER MEASURES.ISANCESTORDEMO AS`  
  
 `IsAncestor([Date].[Fiscal].CurrentMember, [Date].[Fiscal].[Month].&[2003]&[1])`  
  
 `SELECT MEASURES.ISANCESTORDEMO ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Vea también  
 [Antecesor &#40; MDX &#41;](../mdx/ancestor-mdx.md)   
 [Referencia de funciones MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
