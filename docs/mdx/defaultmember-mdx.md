---
title: DefaultMember (MDX) | Documentos de Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: DefaultMember
dev_langs: kbMDX
helpviewer_keywords: DefaultMember function
ms.assetid: c1b53b3a-6e73-4c41-a4fe-9f5c96da5463
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 756f099281a884c168a304cf4d27dfbf8f1f03e0
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="defaultmember-mdx"></a>DefaultMember (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Devuelve el miembro predeterminado de una jerarquía.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Hierarchy_Expression.DefaultMember  
```  
  
## <a name="arguments"></a>Argumentos  
 *Hierarchy_Expression*  
 Expresión MDX válida que devuelve una jerarquía.  
  
## <a name="remarks"></a>Notas  
 El miembro predeterminado de un atributo se utiliza para evaluar expresiones cuando un atributo no está incluido en una consulta.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se usa el **DefaultMember** función, junto con el **nombre** función para devolver el miembro predeterminado para la dimensión de moneda de destino en el cubo de Adventure Works. El ejemplo devuelve **dólar estadounidense**. El **nombre** función se utiliza para devolver el nombre de la medida en lugar de la propiedad predeterminada de la medida, que es **valor**.  
  
```  
WITH MEMBER Measures.x AS   
   [Destination Currency].[Destination Currency].DefaultMember.Name  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Ver también  
 [Referencia de funciones MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)   
 [Definir a un miembro predeterminado](../analysis-services/multidimensional-models/attribute-properties-define-a-default-member.md)  
  
  
