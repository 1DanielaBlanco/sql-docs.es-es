---
title: Elemento FontFlags (ASSL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- FontFlags Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- FontFlags
helpviewer_keywords:
- FontFlags element
ms.assetid: ea608da9-ab05-42ab-8872-c52cd9f3f546
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8dd5fc52330966160d9674d7bb89e6794cffad46
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="fontflags-element-assl"></a>Elemento FontFlags (ASSL)
  Describe las características de presentación relacionadas con la fuente de la [CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md) o [medida](../../../analysis-services/scripting/objects/measure-element-assl.md) elemento primario.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<CalculationProperty> <!-- or Measure -->  
   ...  
      <FontFlags>...</FontFlags>  
      ...  
</CalculationProperty>  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|Cadena|  
|Valor predeterminado|Ninguno|  
|Cardinalidad|0-1: Elemento opcional que puede aparecer solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|[CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md), [medida](../../../analysis-services/scripting/objects/measure-element-assl.md)|  
|Elementos secundarios|Ninguno|  
  
## <a name="remarks"></a>Comentarios  
 El **FontFlags** propiedad contiene una expresión de expresiones multidimensionales (MDX) y se aplica a **CalculationProperty** elementos que tienen un [CalculationType](../../../analysis-services/scripting/properties/calculationtype-element-assl.md) de *Miembro* o *celdas*.  
  
 Los elementos que corresponden a los elementos primarios de **FontFlags** en el modelo de objetos de Analysis Management Objects (AMO) son <xref:Microsoft.AnalysisServices.CalculationProperty> y <xref:Microsoft.AnalysisServices.Measure>.  
  
## <a name="see-also"></a>Vea también  
 [Calculationproperties, elemento &#40; ASSL &#41;](../../../analysis-services/scripting/collections/calculationproperties-element-assl.md)   
 [MdxScript, elemento &#40; ASSL &#41;](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)   
 [MdxScripts, elemento &#40; ASSL &#41;](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md)   
 [Propiedades &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
