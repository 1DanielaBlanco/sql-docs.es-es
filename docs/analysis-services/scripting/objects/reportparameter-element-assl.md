---
title: Elemento ReportParameter (ASSL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
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
apiname: ReportParameter Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: ReportParameter
helpviewer_keywords: ReportParameter element
ms.assetid: 653a5c64-f1af-4796-bb7b-b44a40e52901
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b270fa9fb739c6afdb7edb14aaa8b7dab998a815
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2017
---
# <a name="reportparameter-element---assl"></a>Elemento ReportParameter - ASSL
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Contiene el nombre y el valor de un parámetro que se pasa a un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] informes en tiempo de ejecución.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<ReportParameters>  
      <ReportParameter>  
      <Name>...</Name>  
      <Value>...</Value>  
   </ReportParameter>  
</ReportParameters>  
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
|Elementos primarios|[ReportParameters](../../../analysis-services/scripting/collections/reportparameters-element-assl.md)|  
|Elementos secundarios|[Name](../../../analysis-services/scripting/properties/name-element-assl.md), [Value](../../../analysis-services/scripting/properties/value-element-assl.md)|  
  
## <a name="remarks"></a>Comentarios  
 El elemento **Value** debe contener una expresión MDX (Expresiones multidimensionales).  
  
 El elemento correspondiente en el modelo de objetos de Analysis Management Objects (AMO) es <xref:Microsoft.AnalysisServices.ReportParameter>.  
  
## <a name="see-also"></a>Vea también  
 [Tipo de datos ReportAction &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md)   
 [Action, elemento &#40; ASSL &#41;](../../../analysis-services/scripting/objects/action-element-assl.md)   
 [Objetos de &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
