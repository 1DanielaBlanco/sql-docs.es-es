---
title: Elemento MemberUniqueNameStyle (ASSL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: MemberUniqueNameStyle Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
helpviewer_keywords: MemberUniqueNameStyle element
ms.assetid: f0771c81-0127-4203-9501-ae4f864730fa
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: dbe8b82f9f82327009875530e7750753705f48e8
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="memberuniquenamestyle-element-assl"></a>Elemento MemberUniqueNameStyle (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Determina cómo únicos nombres se generan para los miembros de las jerarquías contenidas en el [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md) elemento.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<CubeDimension>  
   ...  
   <MemberUniqueNameStyle>...</MemberUniqueNameStyle>  
   ...  
</CubeDimension>  
```  
  
## <a name="element-characteristics"></a>Características del elemento  
  
|Característica|Description|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|String (enumeración)|  
|Valor predeterminado|*Nativo*|  
|Cardinalidad|0-1: Elemento opcional que puede aparecer una y solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elemento primario|[CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md)|  
|Elementos secundarios|None|  
  
## <a name="remarks"></a>Comentarios  
 El valor de este elemento se limita a una de las cadenas enumeradas en la tabla siguiente.  
  
|Valor|Description|  
|-----------|-----------------|  
|*Nativo*|La instancia determina automáticamente los nombres únicos de los miembros.|  
|*NamePath*|La instancia genera un nombre compuesto formado por cada nivel y el título del miembro.|  
  
## <a name="remarks"></a>Comentarios  
 El elemento que corresponde al elemento primario de **MemberUniqueNameStyle** en el objeto de Analysis Management Objects (AMO) es el modelo <xref:Microsoft.AnalysisServices.CubeDimension>.  
  
## <a name="see-also"></a>Vea también  
 [CUBE, elemento &#40; ASSL &#41;](../../../analysis-services/scripting/objects/cube-element-assl.md)   
 [Dimension, elemento &#40; ASSL &#41;](../../../analysis-services/scripting/objects/dimension-element-assl.md)   
 [Tipo de datos CubeDimension &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md)  
  
  
