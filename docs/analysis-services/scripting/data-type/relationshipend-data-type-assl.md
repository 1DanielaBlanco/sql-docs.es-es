---
title: Tipo de datos RelationshipEnd (ASSL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: 3a974dd4-e1d6-45b2-b8c8-1a914bc13a02
caps.latest.revision: "7"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d309feb925649d49016a614237b517e67bd21308
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2017
---
# <a name="relationshipend-data-type-assl"></a>Tipo de datos RelationshipEnd (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Define un tipo de datos primitivo que representa un extremo de la relación en una relación.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<RelationshipEnd>  
   <Role>...</Role>  
   <Multiplicity>...</Multiplicity>  
   <DimensionID>...</DimensionID>  
   <Attributes>...</Attributes>  
   <Translations>...</Translations>  
   <VisualizationProperties>...</VisualizationProperties>  
</Relationship>  
```  
  
## <a name="data-type-characteristics"></a>Características del tipo de datos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipos de datos base|Ninguno|  
|Tipos de datos derivados|Ninguno|  
  
## <a name="data-type-relationships"></a>Relaciones entre tipos de datos  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|[Relación](../../../analysis-services/scripting/data-type/relationship-data-type-assl.md)|  
|Elementos secundarios|[Role](../../../analysis-services/xmla/xml-elements-properties/role-element-xmla.md), [Multiplicity](../../../analysis-services/scripting/properties/multiplicity-element-assl.md), [DimensionID](../../../analysis-services/scripting/properties/dimensionid-element-assl.md), [Attributes](../../../analysis-services/scripting/collections/attributes-element-assl.md), [Translations](../../../analysis-services/scripting/collections/translations-element-assl.md), [VisualizationProperties](../../../analysis-services/scripting/data-type/relationshipendvisualizationproperties-data-type-assl.md)|  
|Elementos derivados||  
  
## <a name="remarks"></a>Comentarios  
 El elemento correspondiente en el modelo de objetos de Analysis Management Objects (AMO) es <xref:Microsoft.AnalysisServices.RelationshipEnd>.  
  
## <a name="see-also"></a>Vea también  
 [Analysis Services Scripting Language tipos de datos XML &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
