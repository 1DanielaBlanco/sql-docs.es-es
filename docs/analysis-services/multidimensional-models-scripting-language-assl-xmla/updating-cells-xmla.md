---
title: Actualizar celdas (XMLA) | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- modifying cells
- XMLA, cells
- updating cells
- cells [Analysis Services]
- XML for Analysis, cells
ms.assetid: a1c61496-36ee-4bce-98d9-d13440d349aa
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 57edea50d67fa52de99f92b85b40bcd5caf307fb
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="updating-cells-xmla"></a>Actualizar celdas (XMLA)
  Puede usar el [UpdateCells](../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md) comando para cambiar el valor de una o más celdas en un cubo habilitado para reescritura del cubo. [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] almacena la información actualizada en una tabla de reescritura independiente para cada partición que contiene celdas que se va a actualizar.  
  
> [!NOTE]  
>  El **UpdateCells** comando no es compatible con las asignaciones durante la reescritura del cubo. Para usar la reescritura asignada, debe utilizar el [instrucción](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md) comando que se envía una instrucción UPDATE de expresiones multidimensionales (MDX). Para obtener más información, vea [instrucción UPDATE CUBE &#40; MDX &#41; ](../../mdx/mdx-data-manipulation-update-cube.md).  
  
## <a name="specifying-cells"></a>Especificar celdas  
 El [celda](../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md) propiedad de la **UpdateCells** comando contiene las celdas que se va a actualizar. Identificar cada celda de la **celda** propiedad mediante el número ordinal de la celda. Conceptualmente, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] numera las celdas de un cubo como si el cubo fuera una *p*-matriz unidimensional, donde *p* es el número de ejes. Las celdas se ordenan por importancia de fila. En la ilustración siguiente se muestra la fórmula para calcular el número ordinal de una celda.  
  
 ![Fórmula para calcular la posición ordinal de celda](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/media/cellordinalformula.gif "fórmula para calcular la posición ordinal de celda")  
  
 Una vez que sepa el número ordinal de una celda, puede indicar el valor esperado de la celda en la [valor](../../analysis-services/xmla/xml-elements-properties/value-element-xmla.md) propiedad de la [celda](../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md) propiedad.  
  
## <a name="see-also"></a>Vea también  
 [Actualizar elemento &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Desarrollar con XMLA en Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
