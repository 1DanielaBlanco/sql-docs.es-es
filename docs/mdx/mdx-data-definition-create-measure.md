---
title: Instrucción CREATE MEASURE (MDX) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: f264ba96-cbbe-488b-8ac9-b3056a6e997b
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: c87b1b725489de8b163ab5a2a7d73794eddce9e9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-data-definition---create-measure"></a>Definición de datos MDX - crear medida
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Crea una medida en un modelo tabular.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
CREATE MEASURE Table_Name[Measure_Name] = DAX_Expression  
[; CREATE MEASURE ...n]  
  
```  
  
## <a name="arguments"></a>Argumentos  
 *Table_name*  
 Literal de cadena válido que proporciona el nombre de la tabla donde se creará la medida.  
  
 *Measure_Name*  
 Literal de cadena válida que proporciona un nombre de medida.  
  
 *DAX_Expression*  
 Expresión DAX válida que devuelve un solo valor escalar.  
  
## <a name="remarks"></a>Comentarios  
 El *Measure_Name* debe ir entre corchetes.  
  
 La instrucción CREATE MEASURE solo puede usarse dentro de una definición de script MDX; vea [elemento MdxScript &#40;ASSL&#41;](../analysis-services/scripting/objects/mdxscript-element-assl.md).  
  
 También puede definir un miembro calculado para su uso en una sola consulta. Para definir un miembro calculado limitado a una sola consulta, use la cláusula WITH de la instrucción SELECT. Para obtener más información, consulte [generar medidas en MDX](../analysis-services/multidimensional-models/mdx/mdx-building-measures.md).  
  
## <a name="see-also"></a>Vea también  
 [Instrucciones de definición de datos MDX &#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
