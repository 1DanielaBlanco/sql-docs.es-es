---
title: Elemento AlgorithmParameter (ASSL) | Documentos de Microsoft
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
apiname: AlgorithmParameter Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: AlgorithmParameter
helpviewer_keywords: AlgorithmParameter element
ms.assetid: 73211495-065c-43c6-a486-be6044617263
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 4c5609d78c2b1fdb20944ca56f01044db7e113ed
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2017
---
# <a name="algorithmparameter-element-assl"></a>Elemento AlgorithmParameter (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Define un parámetro para el algoritmo usado por un [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<AlgorithmParameters>  
   <AlgorithmParameter>  
      <Name>...</Name>  
      <Value>...</Value>  
   </AlgorithmParameter>  
</AlgorithmParameters>  
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
|Elementos primarios|[AlgorithmParameters](../../../analysis-services/scripting/collections/algorithmparameters-element-assl.md)|  
|Elementos secundarios|[Name](../../../analysis-services/scripting/properties/name-element-assl.md), [Value](../../../analysis-services/scripting/properties/value-element-assl.md)|  
  
## <a name="remarks"></a>Comentarios  
 **AlgorithmParameter** es un parámetro para un algoritmo del modelo de minería de datos. **AlgorithmParameter** representa este parámetro como un par de nombre/valor. El conjunto de parámetros aplicables que **AlgorithmParameter** puede representar es depende del algoritmo. Para obtener más información acerca de los parámetros de algoritmo para un algoritmo dado, vea la documentación adecuada para ese algoritmo.  
  
 Parámetros de algoritmos disponibles, incluida la información de validación y presentación, se pueden recuperar desde el [DMSCHEMA_MINING_SERVICE_PARAMETERS](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset.md) de filas de esquema.  
  
 El elemento correspondiente en el modelo de objetos de Analysis Management Objects (AMO) es <xref:Microsoft.AnalysisServices.AlgorithmParameter>.  
  
## <a name="see-also"></a>Vea también  
 [MiningModel, elemento &#40; ASSL &#41;](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)   
 [Elemento Algorithm &#40; ASSL &#41;](../../../analysis-services/scripting/properties/algorithm-element-assl.md)   
 [Objetos de &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
