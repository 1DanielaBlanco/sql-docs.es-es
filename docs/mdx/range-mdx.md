---
title: ': (Intervalo) (MDX) | Documentos de Microsoft'
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ':'
dev_langs: kbMDX
helpviewer_keywords:
- ': (range operator)'
- range operator (:)
ms.assetid: f9b36aca-4efd-49b4-9e4f-12914c1b24a6
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: f272f132f85d1ed9ed83c61975a111f2eec6ebf6
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="-range-mdx"></a>: (Intervalo) (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Realiza una operación de conjunto que devuelve un conjunto en su orden natural, con los dos miembros especificados como extremos y todos los miembros entre ellos incluidos como miembros del conjunto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Member_Expression : Member_Expression      
```  
  
#### <a name="parameters"></a>Parámetros  
 *Expresión_miembro*  
 Expresión MDX válida que devuelve un miembro.  
  
## <a name="return-value"></a>Valor devuelto  
 Un conjunto que contiene los miembros especificados y todos los miembros que se encuentran entre los miembro especificados.  
  
## <a name="remarks"></a>Comentarios  
 Ambos parámetros deben especificar miembros del mismo nivel y jerarquía de una dimensión determinada. Si ambos parámetros especifican el mismo miembro, el **: (intervalo)** operador devuelve un conjunto que contiene solamente el miembro especificado. Si el primer parámetro es NULL, el conjunto contiene todos los miembros desde el principio del nivel del miembro especificado en el segundo parámetro hasta dicho miembro inclusive. Si el segundo parámetro es NULL, el conjunto contiene todos los miembros desde el miembro especificado en el primer parámetro hasta el último miembro del mismo nivel inclusive.  
  
 Este operador de conjunto no tiene equivalente funcional en MDX.  
  
## <a name="examples"></a>Ejemplos  
 En el siguiente ejemplo se muestra el uso de este operador.  
  
```  
-- This query returns the freight cost per user  
-- for products, averaged by month, for the first quarter.  
With Member [Measures].[Freight Per Customer] as  
 (  
     [Measures].[Internet Freight Cost]  
     /   
     [Measures].[Customer Count]  
)  
  
SELECT   
    {[Ship Date].[Calendar].[Month].&[2004]&[1] : [Ship Date].[Calendar].[Month].&[2004]&[3]} ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[Freight Per Customer])  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de operadores MDX &#40; MDX &#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
