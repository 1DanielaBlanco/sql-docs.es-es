---
title: TupleToStr (MDX) | Documentos de Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b31c84cf028141943d4d726d96c48d926792814e
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743264"
---
# <a name="tupletostr-mdx"></a>TupleToStr (MDX)


  Devuelve una cadena con formato MDX (Expresiones multidimensionales) que corresponde a una tupla especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
TupleToStr(Tuple_Expression)   
```  
  
## <a name="arguments"></a>Argumentos  
 *Tuple_Expression*  
 Expresión MDX válida que devuelve una tupla.  
  
## <a name="remarks"></a>Notas  
 Esta función se utiliza para transferir una representación de cadena de una tupla a una función externa para su análisis. La cadena devuelta aparece encerrada entre llaves {} y cada miembro, si más de uno expresamente definido en la tupla, está separado por una coma.  
  
## <a name="examples"></a>Ejemplos  
 El ejemplo siguiente devuelve la cadena ([Date].[Calendar Year].&[2001],[Geography].[Geography].[Country].&[United States]) :  
  
```  
WITH MEMBER Measures.x AS TupleToStr   
   (   
      ([Date].[Calendar Year].&[2001]  
         , [Geography].[Geography].[Country].&[United States]  
      )  
   )     
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
 El ejemplo siguiente devuelve la misma cadena que el ejemplo anterior.  
  
```  
WITH SET s AS   
   {  
      ([Date].[Calendar Year].&[2001],  
         [Geography].[Geography].[Country].&[United States]  
      )   
   }  
MEMBER Measures.x AS TupleToStr ( s.Item(0) )  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de funciones MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
