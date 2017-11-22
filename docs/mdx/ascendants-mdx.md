---
title: Ascendants (MDX) | Documentos de Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ASCENDANTS
dev_langs: kbMDX
helpviewer_keywords: Ascendants function
ms.assetid: a2baf4a2-7d66-4766-b708-739a3c21b09e
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 2b81f8dffc10d5fa62c264814d3f1215c7f44c5a
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="ascendants-mdx"></a>Ascendants (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve el conjunto de antecesores de un miembro especificado, incluyendo el propio miembro.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Ascendants(Member_Expression)  
```  
  
## <a name="arguments"></a>Argumentos  
 *Expresión_miembro*  
 Expresión MDX válida que devuelve un miembro.  
  
## <a name="remarks"></a>Comentarios  
 El **antecesores** función devuelve todos los antecesores de un miembro desde el propio miembro hasta la parte superior de la jerarquía del miembro; más específicamente, realiza un recorrido transversal posterior a la de la jerarquía para el miembro especificado y, a continuación, devuelve todos los miembros antecesores relacionados con el miembro, incluido él mismo, en un conjunto. Se trata de diferencia el [antecesor](../mdx/ancestor-mdx.md) función, que devuelve un miembro antecesor específico, o antecesor, en un nivel específico.  
  
## <a name="examples"></a>Ejemplos  
 El ejemplo siguiente devuelve el número de pedidos de distribuidores el `[Sales Territory].[Northwest]` miembro y todos los antecesores de ese miembro de la **Adventure Works** cubo. El **antecesores** función crea el conjunto que incluye el `[Sales Territory].[Northwest]` miembro y sus antecesores para el eje de filas.  
  
```  
SELECT  
   Measures.[Reseller Order Count] ON COLUMNS,  
   Order(  
      Ascendants(  
         [Sales Territory].[Northwest]  
      ),  
      DESC  
   ) ON ROWS  
FROM  
   [Adventure Works]  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de funciones MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
