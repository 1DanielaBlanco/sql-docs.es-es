---
title: Elemento KPI (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Kpi Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Kpi
helpviewer_keywords:
- Kpi element
ms.assetid: 1979a58f-97a8-4c1a-aa65-dcfb6d2404cf
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 63b7947785976d41cda112b1c14b3829e3f98e3a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2018
ms.locfileid: "48124155"
---
# <a name="kpi-element-assl"></a>Elemento Kpi (ASSL)
  Define un indicador clave de rendimiento (KPI) dentro de un [cubo](cube-element-assl.md) elemento o un [perspectiva](perspective-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<Kpis>  
   <Kpi> <!-- ancestor: Cube -->  
            <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</Description>  
      <Translations>...</Translations>  
      <DisplayFolder>...</DisplayFolder>  
      <AssociatedMeasureGroupID>...</AssociatedMeasureGroupID>  
      <Value>...</Value>  
            <Goal>...</Goal>  
      <Status>...</Status>  
      <Trend>...</Trend>  
      <TrendGraphic>...</TrendGraphic>  
      <StatusGraphic>...</StatusGraphic>  
      <CurrentTimeMember>...</CurrentTimeMember>  
      <Annotations>...</Annotations>  
   </Kpi>  
   <!-- or -->  
   <Kpi xsi:type="PerspectiveKpi">...</Kpi> <!-- ancestor: Perspective -->  
   </Kpi>  
</Kpis>  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Valor predeterminado|None|  
|Cardinalidad|0-n: elemento opcional que puede aparecer más de una vez.|  
  
|Antecesor o elemento primario|Tipo de datos|  
|------------------------|---------------|  
|[Cubo](cube-element-assl.md)|None|  
|[Perspectiva](../data-type/perspectivekpi-data-type-assl.md)|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|[KPI](../collections/kpis-element-assl.md)|  
  
## <a name="child-elements"></a>Elementos secundarios  
  
|Antecesor o elemento primario|Elementos secundarios|  
|------------------------|--------------------|  
|[Cubo](../collections/annotations-element-assl.md), [AssociatedMeasureGroupID](../properties/id-element-assl.md), [CurrentTimeMember](member-element-assl.md), [descripción](../properties/description-element-assl.md), [DisplayFolder](../properties/displayfolder-element-assl.md), [Objetivo](../properties/goal-element-assl.md), [ID](../properties/id-element-assl.md), [nombre](../properties/name-element-assl.md), [estado](../properties/status-element-assl.md), [StatusGraphic](../properties/statusgraphic-element-assl.md), [traducciones ](../collections/translations-element-assl.md), [Tendencia](../properties/trend-element-assl.md), [TrendGraphic](../properties/trendgraphic-element-assl.md), [valor](../properties/value-element-assl.md)|  
|[Perspectiva](perspective-element-assl.md)|None|  
  
## <a name="remarks"></a>Comentarios  
 Los elementos correspondientes en el modelo de objetos Objetos de administración de análisis (AMO) son <xref:Microsoft.AnalysisServices.Kpi> y <xref:Microsoft.AnalysisServices.PerspectiveKpi>.  
  
## <a name="see-also"></a>Vea también  
 [Objetos &#40;ASSL&#41;](objects-assl.md)  
  
  
