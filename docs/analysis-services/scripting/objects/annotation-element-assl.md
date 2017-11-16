---
title: Elemento Annotation (ASSL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Annotation Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Annotation
helpviewer_keywords:
- Annotation element
ms.assetid: 7d75291a-47b4-498a-8ba4-3d093b8513b2
caps.latest.revision: 43
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 109386991ba5d632e6c40523241f6d64c4dba05d
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="annotation-element-assl"></a>Elemento Annotation (ASSL)
  Contiene elementos que se utilizan para extender el esquema del lenguaje de scripting de Analysis Services (ASSL).  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<Annotations>  
   <Annotation>  
      <Name>...</Name>  
      <Visibility>...</Visibility>  
      <Value>...</Value>  
   </Annotation>  
</Annotations >  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|Ninguno|  
|Valor predeterminado|Ninguno|  
|Cardinalidad|0-n: elemento opcional que puede aparecer más de una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|[Anotaciones](../../../analysis-services/scripting/collections/annotations-element-assl.md)|  
|Elementos secundarios|[Nombre](../../../analysis-services/scripting/properties/name-element-assl.md), [valor](../../../analysis-services/scripting/properties/value-element-assl.md), [visibilidad](../../../analysis-services/scripting/properties/visibility-element-assl.md)|  
  
## <a name="remarks"></a>Comentarios  
 El **anotación** elemento proporciona extensibilidad del esquema ASSL para todos los objetos que no sean los que se usan únicamente para definir un tipo de datos complejos. El **valor** elemento de la **anotación** elemento puede contener XML válido de cualquier espacio de nombres XML distinto de ASSL, sujeto a las reglas siguientes:  
  
-   El XML solo puede contener elementos.  
  
-   Cada elemento debe tener un nombre único. Se recomienda que el valor de la **nombre** elemento de la **anotación** elemento hacer referencia el espacio de nombres de destino.  
  
 Estas reglas se imponen para permitir que el contenido de la **anotación** pares de elemento que se va a exponer como un conjunto de nombre/valor mediante otras interfaces, como Decision Support Objects (DSO).  
  
 Comentarios y espacios en blanco dentro del **anotación** no se puede conservar el elemento que no se incluyen dentro de un elemento secundario. Además, todos los elementos deben ser de lectura y escritura; se omitirán los elementos de solo lectura.  
  
 El elemento correspondiente en el modelo de objetos de Analysis Management Objects (AMO) es <xref:Microsoft.AnalysisServices.Annotation>.  
  
## <a name="see-also"></a>Vea también  
 [Objetos de &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  

