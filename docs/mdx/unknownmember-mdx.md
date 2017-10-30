---
title: UnknownMember (MDX) | Documentos de Microsoft
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
- UnknownMember
dev_langs:
- kbMDX
helpviewer_keywords:
- UnknownMember function
ms.assetid: 5ae39cbe-65c8-4a59-9548-71b28ecf6eb5
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 131993b1038229138df3e7d084b5d842693b7f0f
ms.contentlocale: es-es
ms.lasthandoff: 08/02/2017

---
# <a name="unknownmember-mdx"></a>UnknownMember (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve el miembro desconocido asociado con un nivel o miembro.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Member expression syntax  
Member_Expression.UnknownMember  
  
Hierarchy_expression syntax  
Hierarchy_Expression.UnknownMember  
```  
  
## <a name="arguments"></a>Argumentos  
 *Expresión_miembro*  
 Expresión MDX válida que devuelve un miembro.  
  
 *Hierarchy_Expression*  
 Expresión MDX válida que devuelve una jerarquía.  
  
## <a name="remarks"></a>Comentarios  
 [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] crea un miembro desconocido para asociar los datos de la tabla de hechos con una jerarquía cuando no se conoce la jerarquía. El miembro desconocido puede hallarse en cualquiera de los niveles siguientes:  
  
-   En el nivel superior de las jerarquías de atributo que no se agregan.  
  
-   En el primer nivel por debajo del **todos los** nivel para jerarquías naturales.  
  
-   En cualquier nivel en el caso de las jerarquías no naturales.  
  
 Si se especifica una expresión de miembro, el **UnknownMember** función devuelve el miembro desconocido miembro secundario del miembro especificado. Si el miembro especificado no existe, la función devuelve un valor NULL.  
  
 Si se especifica una expresión de jerarquía, el **UnknownMember** función devuelve el miembro desconocido en el nivel superior, si existe alguno.  
  
 Si el miembro desconocido no existe en el nivel o miembro, el **UnknownMember** función crea un miembro con valor null.  
  
> [!NOTE]  
>  Si el miembro desconocido no existe en la jerarquía o el miembro, se genera un error.  
  
## <a name="examples"></a>Ejemplos  
 El ejemplo siguiente devuelve el miembro desconocido del miembro All Products de la jerarquía de atributo Product de todos los miembros de la dimensión Measures.  
  
```  
SELECT [Product].[Product].[All Products].UnknownMember  
    ON Columns,  
[Measures].Members  
    ON Rows  
FROM [Adventure Works]  
  
```  
  
 El ejemplo siguiente devuelve el miembro desconocido de la jerarquía Product Categories de todos los miembros de la dimensión Measures.  
  
```  
SELECT [Product].[Product Categories].UnknownMember  
    ON Columns,  
[Measures].Members  
    ON Rows  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de funciones MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

