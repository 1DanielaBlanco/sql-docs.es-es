---
title: Elemento primario (MDX) | Documentos de Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 16de50e05bf139d590f90630e338fdb7cbb428e5
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34742764"
---
# <a name="parent-mdx"></a>Parent (MDX)


  Devuelve el elemento primario de un miembro.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Member_Expression.Parent   
```  
  
## <a name="arguments"></a>Argumentos  
 *Expresión_miembro*  
 Expresión MDX válida que devuelve un miembro.  
  
## <a name="remarks"></a>Notas  
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
 [Referencia de funciones MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
