---
title: Elemento Filter (Binding) (ASSL) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Filter Element (Binding)
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- filter
helpviewer_keywords:
- Filter element
ms.assetid: 3d4cd169-2903-4266-8541-540ece424b7b
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 47b12ea503e917513bfe00001f01665b7712f30e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="filter-element-binding-assl"></a>Elemento Filter (Binding) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene una expresión MDX (Expresiones multidimensionales) que filtra el contenido del elemento primario.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<CubeDimensionBinding> <!-- or MeasureGroupBinding -->  
   ...  
   <Filter>...</Filter>  
   ...  
</CubeDimensionBinding>  
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
|Elementos primarios|[CubeDimensionBinding](../../../analysis-services/scripting/data-type/cubedimensionbinding-data-type-assl.md), [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)|  
|Elementos secundarios|Ninguno|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información sobre la **enlace** tipo, incluidas las tablas de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] objetos de Scripting Language (ASSL) de la **enlace** tipo y la jerarquía de herencia de **de enlace**  tipos, consulte [tipo de datos de enlace &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md).  
  
 Para obtener información general de enlaces de datos en ASSL, vea [orígenes de datos y enlaces & #40; SSAS Multidimensional & #41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 Los elementos que corresponden a los elementos primarios de **filtro** en el modelo de objetos de Analysis Management Objects (AMO) son <xref:Microsoft.AnalysisServices.CubeDimensionBinding> y <xref:Microsoft.AnalysisServices.MeasureGroupBinding>.  
  
## <a name="see-also"></a>Vea también  
 [Tipo de enlace de datos & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)   
 [Orígenes de datos y enlaces &#40;SSAS Multidimensional&#41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)   
 [Propiedades & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
