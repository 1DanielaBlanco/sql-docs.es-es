---
title: Recuento (Set) (MDX) | Documentos de Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COUNT
dev_langs:
- kbMDX
helpviewer_keywords:
- Count function [MDX]
ms.assetid: 22f530e9-f8e1-4608-affa-9a2bc0821591
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 97a997760b2796bc0fb7708503caf1a278e0d59d
ms.contentlocale: es-es
ms.lasthandoff: 08/02/2017

---
# <a name="count-set-mdx"></a>Count (Set) (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Devuelve el número de celdas de un conjunto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Standard syntax  
Count(Set_Expression [ , ( EXCLUDEEMPTY | INCLUDEEMPTY ) ] )  
  
Alternate syntax  
Set_Expression.Count  
```  
  
## <a name="arguments"></a>Argumentos  
 *Set_Expression*  
 Expresión MDX (Expresiones multidimensionales) válida que devuelve un conjunto.  
  
## <a name="remarks"></a>Comentarios  
 El **recuento (Set)** función incluye o excluye celdas vacías, dependiendo de la sintaxis utilizada. Si se utiliza la sintaxis estándar, las celdas vacías pueden excluirse o incluirse utilizando la **EXCLUDEEMPTY** o **INCLUDEEMPTY** marcas, respectivamente. Si se utiliza la sintaxis alternativa, la función incluye siempre celdas vacías.  
  
 Para excluir las celdas vacías en el recuento de un conjunto, utilice la sintaxis estándar y opcional **EXCLUDEEMPTY** marca.  
  
> [!NOTE]  
>  El **recuento (Set)** función cuenta las celdas vacías de forma predeterminada. En cambio, el **recuento** función en OLE DB que cuenta un conjunto excluye las celdas vacías de forma predeterminada.  
  
## <a name="examples"></a>Ejemplos  
 El ejemplo siguiente cuenta el número de celdas del conjunto de miembros que consta del elemento secundario de la jerarquía de atributo Model Name de la dimensión Product.  
  
```  
WITH MEMBER measures.X AS  
   [Product].[Model Name].children.count   
SELECT Measures.X ON 0  
FROM [Adventure Works]  
```  
  
 En el ejemplo siguiente se cuenta el número de productos de la dimensión Product mediante la **DrilldownLevel** función junto con el **recuento** función.  
  
```  
Count(DrilldownLevel (   
   [Product].[Product].[Product]))  
```  
  
 El ejemplo siguiente devuelve los distribuidores cuyas ventas en comparación con el trimestre anterior, mediante el uso de han disminuido el **recuento** función junto con el **filtro** función y un número de otras funciones. Esta consulta utiliza la **agregado** función para permitir la selección de diferentes miembros geográficos, por ejemplo, para la selección desde dentro de una lista desplegable en una aplicación cliente.  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS  
   Count  
   (Filter  
      (Existing(Reseller.Reseller.Reseller),  
         [Measures].[Reseller Sales Amount]   
         < ([Measures].[Reseller Sales Amount],  
            [Date].Calendar.PrevMember)  
      )  
   )  
MEMBER [Geography].[State-Province].x AS   
   Aggregate  
   ( {[Geography].[State-Province].&[WA]&[US],   
      [Geography].[State-Province].&[OR]&[US] }   
   )  
SELECT NON EMPTY HIERARCHIZE   
   (AddCalculatedMembers   
      ({DrillDownLevel  
         ({[Product].[All Products]})  
      })  
   ) DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE ([Geography].[State-Province].x,  
   [Date].[Calendar].[Calendar Quarter].&[2003]&[4]  
   ,[Measures].[Declining Reseller Sales])  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Número de &#40; dimensión &#41; &#40; MDX &#41;](../mdx/count-dimension-mdx.md)   
 [Número de &#40; Niveles de jerarquía &#41; &#40; MDX &#41;](../mdx/count-hierarchy-levels-mdx.md)   
 [Número de &#40; Tupla &#41; &#40; MDX &#41;](../mdx/count-tuple-mdx.md)   
 [DrilldownLevel &#40; MDX &#41;](../mdx/drilldownlevel-mdx.md)   
 [AddCalculatedMembers &#40; MDX &#41;](../mdx/addcalculatedmembers-mdx.md)   
 [Hierarchize &#40; MDX &#41;](../mdx/hierarchize-mdx.md)   
 [Propiedades &#40; MDX &#41;](../mdx/properties-mdx.md)   
 [Agregado &#40; MDX &#41;](../mdx/aggregate-mdx.md)   
 [Filtro &#40; MDX &#41;](../mdx/filter-mdx.md)   
 [PrevMember &#40; MDX &#41;](../mdx/prevmember-mdx.md)   
 [Referencia de funciones MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

