---
title: Tipo de datos MeasureGroupBinding (ASSL) | Documentos de Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- MeasureGroupBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MeasureGroupBinding
helpviewer_keywords:
- MeasureGroupBinding data type
ms.assetid: 47e83eec-e0bc-4118-9a0f-5bfdd6218297
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 12c54f8a61d75afd7689f19b2936bb6aefa3b4c1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36203507"
---
# <a name="measuregroupbinding-data-type-assl"></a>Tipo de datos MeasureGroupBinding (ASSL)
  Define un tipo de datos derivado que representa un enlace a un [MeasureGroup](../objects/group-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<MeasureGroupBinding>  
   <!-- The following elements extend Binding -->  
   <DataSourceID>...</DataSourceID>  
   <CubeID>...</CubeID>  
   <MeasureGroupID>...</MeasureGroupID>  
   <Persistence>...</Persistence>  
   <RefreshPolicy>...</RefreshPolicy>  
   <RefreshInterval>...</RefreshInterval>  
   <Filter>...</Filter>  
</MeasureGroupBinding>  
```  
  
## <a name="data-type-characteristics"></a>Características del tipo de datos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipos de datos base|[Enlace](binding-data-type-assl.md)|  
|Tipos de datos derivados|None|  
  
## <a name="data-type-relationships"></a>Relaciones entre tipos de datos  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|None|  
|Elementos secundarios|[CubeID](../properties/id-element-assl.md), [DataSourceID](../properties/datasourceid-element-assl.md), [filtro](../properties/filter-element-binding-assl.md), [MeasureGroupID](../properties/measuregroupid-element-assl.md), [persistencia](../properties/persistence-element-assl.md), [RefreshInterval ](../properties/refreshinterval-element-assl.md), [RefreshPolicy](../properties/refreshpolicy-element-assl.md)|  
|Elementos derivados|Vea [enlace](binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Notas  
 Para obtener información adicional sobre la `Binding` tipo, incluidas las tablas de objetos de Analysis Services Scripting Language (ASSL) del tipo de enlace y la jerarquía de herencia de `Binding` tipos, consulte [tipo de datos de enlace &#40;ASSL &#41;](binding-data-type-assl.md).  
  
 Para obtener información general de enlaces de datos en ASSL, vea [orígenes de datos y enlaces &#40;SSAS multidimensionales&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 El elemento correspondiente en el modelo de objetos de Analysis Management Objects (AMO) es <xref:Microsoft.AnalysisServices.MeasureGroupBinding>.  
  
## <a name="see-also"></a>Vea también  
 [Tipos de datos XML de lenguaje Scripting de Analysis Services &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  