---
title: Elemento LastProcessed (ASSL) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/14/2017
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
- LastProcessed Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- LastProcessed
helpviewer_keywords:
- LastProcessed element
ms.assetid: df3d1f6f-705c-4408-9eb3-c550a1dec450
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: dd61777044ac8746bfe44a881dd2ad3f70a6253a
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="lastprocessed-element-assl"></a>Elemento LastProcessed (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Contiene la marca de tiempo de solo lectura que indica cuándo se procesó por última vez la base de datos que contiene el elemento primario.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<Cube> <!-- or one of the elements listed in the Element Relationships table -->  
   ...  
      <LastProcessed>...</LastProcessed>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Características del elemento  
  
|Característica|Description|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|DateTime|  
|Valor predeterminado|None|  
|Cardinalidad|0-1: Elemento opcional que puede aparecer una y solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|[Cubo](../../../analysis-services/scripting/objects/cube-element-assl.md), [base de datos](../../../analysis-services/scripting/objects/database-element-assl.md), [dimensión](../../../analysis-services/scripting/objects/dimension-element-assl.md), [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md), [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md), [MiningStructure ](../../../analysis-services/scripting/objects/miningstructure-element-assl.md), [Partición](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|Elementos secundarios|None|  
  
## <a name="remarks"></a>Comentarios  
 La instancia de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] mantiene el valor de la **LastProcessed** elemento. El valor solo cambia si se procesa la base de datos que contiene el elemento primario. Al procesar individualmente el elemento primario, no se cambia el valor del elemento **LastProcessed** .  
  
 Los elementos que corresponden a los elementos primarios de **LastProcessed** en el modelo de objetos de Analysis Management Objects (AMO) son <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.MeasureGroup>, <xref:Microsoft.AnalysisServices.MiningModel>, <xref:Microsoft.AnalysisServices.MiningStructure>, y <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>Vea también  
 [Propiedades &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
