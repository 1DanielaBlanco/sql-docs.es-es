---
title: Elemento Usage (MiningModelColumn) (ASSL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Usage Element (MiningModelColumn)
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Usage
helpviewer_keywords:
- Usage element
ms.assetid: 435a857e-37a9-434e-9de1-354f1ff2993f
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: eb454a49ae0035cedca3a8ef322f5f9d13c7625e
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="usage-element-miningmodelcolumn-assl"></a>Elemento Usage (MiningModelColumn) (ASSL)
  Describe cómo la columna asociada en el elemento primario [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md) se utiliza.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<MiningModelColumn>  
   ...  
   <Usage>...</Usage>  
   ...  
</MiningModelColumn>  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|String (enumeración)|  
|Valor predeterminado|Ninguno|  
|Cardinalidad|0-1: Elemento opcional que puede aparecer solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elemento primario|[MiningModelColumn](../../../analysis-services/scripting/data-type/miningmodelcolumn-data-type-assl.md)|  
|Elementos secundarios|Ninguno|  
  
## <a name="remarks"></a>Comentarios  
 El valor de este elemento se limita a una de las cadenas enumeradas en la tabla siguiente.  
  
|Valor|Description|  
|-----------|-----------------|  
|*Key*|La columna es una columna de clave.|  
|*Entrada*|La columna es una columna de entrada.|  
|*Predict*|La columna es una columna de predicción.|  
|*PredictOnly*|La columna es solo una columna de predicción.|  
|*Ninguno*|El modelo no utiliza la columna.<br /><br /> **\*\*Advertencia \* \***  cuando el valor de uso es "None", Analysis Services no envía ningún valor para el servidor de forma predeterminada; por lo tanto, el atributo de uso no está incluido en la solicitud/respuesta.|  
  
 La enumeración que corresponde a los valores permitidos para **uso** en el objeto de Analysis Management Objects (AMO) es el modelo <xref:Microsoft.AnalysisServices.MiningModelColumnUsages>.  
  
## <a name="see-also"></a>Vea también  
 [Propiedades &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  