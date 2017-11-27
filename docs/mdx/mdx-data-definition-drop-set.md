---
title: "Instrucción DROP SET (MDX) | Documentos de Microsoft"
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
- SET
- DROP
- DROP SET
- DROP_SET
dev_langs:
- kbMDX
helpviewer_keywords:
- DROP SET statement
- deleting named sets
- named sets [MDX]
- removing named sets
- dropping named sets
ms.assetid: bbc37afb-af8c-41df-ba81-12771beb1c41
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e4138e926a72af94389df15c924cf6bbcfb6e8e1
ms.contentlocale: es-es
ms.lasthandoff: 08/02/2017

---
# <a name="mdx-data-definition---drop-set"></a>Definición de datos MDX: conjunto de destino
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Quita un conjunto con nombre.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
DROP [SESSION] SET   
   <Cube_Reference>.Set_Name   
               [,<Cube_Reference>.Set_Name ...n]  
  
<Cube_Reference> ::= {CURRENTCUBE | Cube_Name}  
  
```  
  
## <a name="arguments"></a>Argumentos  
 *Restricciones obligatorias Cube_Name*  
 Expresión de cadena válida que proporciona el nombre del cubo.  
  
 *Set_Name*  
 Expresión de cadena válida que proporciona el nombre del conjunto con nombre que se va a quitar.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información sobre los conjuntos con nombre, vea [Crear conjuntos con nombre en MDX &#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-named-sets-building-named-sets.md).  
  
## <a name="see-also"></a>Vea también  
 [Instrucciones de definición de datos MDX &#40; MDX &#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  

