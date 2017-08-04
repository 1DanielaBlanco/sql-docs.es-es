---
title: StrToValue (MDX) | Documentos de Microsoft
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
- STRTOVALUE
dev_langs:
- kbMDX
helpviewer_keywords:
- StrToValue function
ms.assetid: 118a9c4f-74a3-48d5-a4f4-318664bc51bc
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 9db77d7e3d4721337ccbeb397d6cb7382209f027
ms.contentlocale: es-es
ms.lasthandoff: 08/02/2017

---
# <a name="strtovalue-mdx"></a>StrToValue (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve el valor numérico especificado por una cadena con formato MDX (Expresiones multidimensionales).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
StrToValue(MDX_Expression [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>Argumentos  
 *MDX_Expression*  
 Expresión de cadena válida que se resuelve, directa o indirectamente, en una sola celda.  
  
## <a name="remarks"></a>Comentarios  
 El **StrToValue** función devuelve el valor numérico especificado por la expresión MDX. El **StrToValue** función normalmente se utiliza con funciones definidas por el usuario para devolver una expresión MDX desde una función externa a una instrucción MDX que se puede resolver en una sola celda.  
  
-   Cuando se utiliza la marca CONSTRAINED, la expresión MDX debe contener solo un valor escalar. La marca CONSTRAINED se utiliza para reducir el riesgo de ataques por inyección de código mediante la cadena especificada. Si se proporciona una expresión MDX que no se resuelve directamente en un valor escalar, aparece el siguiente error: "Se infringieron las restricciones impuestas por la marca CONSTRAINED en la función STRTOVALUE."  
  
-   Cuando no se utiliza la marca CONSTRAINED, la expresión MDX especificada puede ser tan compleja como se desee, siempre que se resuelva en una expresión MDX (Expresiones multidimensionales) válida que devuelva una única celda.  
  
> [!NOTE]  
>  La devolución del resultado de una expresión MDX como un valor numérico puede ser útil si el valor se almacena como texto y se desean realizar operaciones aritméticas con los valores devueltos.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se usa el **StrToValue** función para devolver el peso de cada bicicleta como un valor.  
  
```  
WITH MEMBER Measures.x AS   
StrToValue   
   ([Product].[Product].CurrentMember.Properties ('Weight')  
   ,CONSTRAINED  
   )  
SELECT Measures.x ON 0  
,[Product].[Product].[Product].Members ON 1  
FROM [Adventure Works]  
WHERE [Product].[Product Categories].[Bikes]  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de funciones MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

