---
title: Elemento DimensionID (ASSL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/06/2017
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
apiname: DimensionID Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: DimensionID
helpviewer_keywords: DimensionID element
ms.assetid: 00262781-4216-4a19-8bdc-d46647f42165
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3154856186051f14331361266e05e57619ffae61
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2017
---
# <a name="dimensionid-element-assl"></a>Elemento DimensionID (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Contiene el identificador (ID) de la dimensión.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<CubeDimension> <!-- or DimensionBinding, DimensionAttributeBinding -- >  
   ...  
   <DimensionID>...</DimensionID>  
      ...  
</CubeDimension>  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|Cadena|  
|Valor predeterminado|Ninguno|  
|Cardinalidad|1-1: Elemento necesario que se produce una vez y solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|[CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md), [DimensionBinding](../../../analysis-services/scripting/data-type/dimensionbinding-data-type-assl.md), [DimensionAttributeBinding](../../../analysis-services/scripting/data-type/dimensionattributebinding-data-type-out-of-line-assl.md)|  
|Elementos secundarios|Ninguno|  
  
## <a name="remarks"></a>Comentarios  
 Los elementos que corresponden a los elementos primarios de **DimensionID** en el modelo de objetos de Analysis Management Objects (AMO) son <xref:Microsoft.AnalysisServices.CubeDimension> y <xref:Microsoft.AnalysisServices.DimensionBinding>.  
  
## <a name="see-also"></a>Vea también  
 [Propiedades &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
