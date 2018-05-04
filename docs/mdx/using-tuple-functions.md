---
title: Usar funciones de tupla | Documentos de Microsoft
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
dev_langs:
- kbMDX
helpviewer_keywords:
- tuple functions
ms.assetid: fe41e3e5-a675-4169-a966-b42c18e8d741
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 796494ac0d73b6dfaf955da58ed79b8b51b54638
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="using-tuple-functions"></a>Usar funciones de tupla
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Una función de tupla recupera una tupla de un conjunto o mediante la resolución de una representación de cadena de una tupla.  
  
 Las funciones de tupla, al igual que las funciones de miembro y de conjunto, son esenciales para negociar las estructuras multidimensionales de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Hay tres funciones de tupla en MDX, [actual &#40;MDX&#41;](../mdx/current-mdx.md), [elemento &#40;tupla&#41; &#40;MDX&#41; ](../mdx/item-tuple-mdx.md) y [StrToTuple &#40;MDX&#41;](../mdx/strtotuple-mdx.md). En la consulta de ejemplo siguiente se muestra el modo de usar cada una de estas funciones:  
  
 `WITH`  
  
 `//Creates a set of tuples consisting of Years and Countries`  
  
 `SET MyTuples AS  [Date].[Calendar Year].[Calendar Year].MEMBERS * [Customer].[Country].[Country].MEMBERS`  
  
 `//Returns a string representation of that set using the Current and Generate functions`  
  
 `MEMBER MEASURES.CURRENTDEMO AS GENERATE(MyTuples, TUPLETOSTR(MyTuples.CURRENT), ", ")`  
  
 `//Retrieves the fourth tuple from that set and displays it as a string`  
  
 `MEMBER MEASURES.ITEMDEMO AS TUPLETOSTR(MyTuples.ITEM(3))`  
  
 `//Creates a tuple consisting of the measure Internet Sales Amount and the country Australia from a string`  
  
 `MEMBER MEASURES.STRTOTUPLEDEMO AS STRTOTUPLE("([Measures].[Internet Sales Amount]" + ", [Customer].[Country].&[Australia])")`  
  
 `SELECT{MEASURES.CURRENTDEMO,MEASURES.ITEMDEMO,MEASURES.STRTOTUPLEDEMO} ON COLUMNS`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Vea también  
 [Funciones &#40;sintaxis MDX&#41;](../mdx/functions-mdx-syntax.md)   
 [Usar funciones de miembro](../mdx/using-member-functions.md)   
 [Uso de funciones de conjuntos](../mdx/using-set-functions.md)  
  
  
