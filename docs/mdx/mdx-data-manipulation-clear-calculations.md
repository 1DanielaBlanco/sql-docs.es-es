---
title: "CLEAR CALCULATIONS (instrucción, MDX) | Documentos de Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CLEAR CALCULATIONS
- clalculations
- clear
dev_langs: kbMDX
helpviewer_keywords:
- clearing calculations
- CLEAR CALCULATIONS statement
- deleting calculations
- removing calculations
- calculations [Analysis Services], clearing
- cubes [Analysis Services], calculations
ms.assetid: aebec9a1-1d1d-4697-aa3f-cc2449625603
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: ad7569a1db3d080c85dc0c45347c2dc011ee312d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="mdx-data-manipulation---clear-calculations"></a>Manipulación de datos MDX - CLEAR CALCULATIONS
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Quita todos los cálculos del cubo y devuelve el cubo al paso de cálculo 0.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
CLEAR CALCULATIONS [FROMCube_Expression]  
```  
  
## <a name="arguments"></a>Argumentos  
 *Cube_Expression*  
 Una expresión de cubo de MDX (Expresiones multidimensionales) válida.  
  
## <a name="remarks"></a>Comentarios  
 El **FROM** cláusula puede omitirse cuando el contexto del cubo es conocido, como en un script MDX.  
  
> [!NOTE]  
>  Esta instrucción solo puede ser ejecutada por un administrador de base de datos o de servidor o un miembro de un rol con acceso a los datos de origen del cubo (es decir, ReadSourceData=true)  
  
## <a name="see-also"></a>Vea también  
 [Instrucciones de manipulación de datos MDX &#40; MDX &#41;](../mdx/mdx-data-manipulation-statements-mdx.md)  
  
  
