---
title: Elemento primario (MDX) | Documentos de Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: PARENT
dev_langs: kbMDX
helpviewer_keywords: Parent function
ms.assetid: 7be9b172-4241-4618-bdba-53cde8badd9b
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 95c6ee8d33dfe77ec53f07166a85c7ce7a4776ae
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="parent-mdx"></a>Parent (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve el elemento primario de un miembro.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Member_Expression.Parent   
```  
  
## <a name="arguments"></a>Argumentos  
 *Expresión_miembro*  
 Expresión MDX válida que devuelve un miembro.  
  
## <a name="remarks"></a>Comentarios  
 El **primario** función devuelve el miembro primario del miembro especificado.  
  
## <a name="examples"></a>Ejemplos  
 Los ejemplos siguientes devuelven el elemento primario del miembro 1 de julio de 2001. El primer ejemplo especifica este miembro en el contexto de la jerarquía de atributo Date y devuelve el miembro All Periods.  
  
```  
SELECT [Date].[Date].[July 1, 2001].Parent ON 0  
FROM [Adventure Works]  
```  
  
 El ejemplo siguiente especifica el miembro 1 de julio de 2001 en el contexto de la jerarquía Calendar.  
  
```  
SELECT [Date].[Calendar].[July 1, 2001].Parent ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de funciones MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
