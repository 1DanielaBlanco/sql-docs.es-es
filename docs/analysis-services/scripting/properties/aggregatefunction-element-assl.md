---
title: Elemento AggregateFunction (ASSL) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- AggregateFunction Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AggregateFunction
helpviewer_keywords:
- AggregateFunction element
ms.assetid: 880b6bd0-d62a-4221-831c-39f748ee84f2
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: e0ed42e0e1803fbd2dab49ca5098cb880459ea5d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="aggregatefunction-element-assl"></a>Elemento AggregateFunction (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Define el tipo de función de agregado usada por un [medida](../../../analysis-services/scripting/objects/measure-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<Measure>  
   ...  
   <AggregateFunction>...</AggregateFunction>  
   ...  
</Measure>  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|String (enumeración)|  
|Valor predeterminado|*Sum*|  
|Cardinalidad|0-1: Elemento opcional que puede aparecer solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|[Medida](../../../analysis-services/scripting/objects/measure-element-assl.md)|  
|Elementos secundarios|Ninguno|  
  
## <a name="remarks"></a>Comentarios  
 El valor de este elemento se limita a una de las cadenas enumeradas en la tabla siguiente.  
  
|Valor|Description|  
|-----------|-----------------|  
|*Sum*|La medida se agrega utilizando la función **Sum** .|  
|*Count*|La medida se agrega utilizando la función **Count** .|  
|*Min*|La medida se agrega utilizando la función **Min** .|  
|*Max*|La medida se agrega utilizando la función **Max** .|  
|*DistinctCount*|La medida se agrega utilizando la función **DistinctCount** .|  
|*Ninguno*|No se agrega la medida.|  
|*ByAccount*|La cuenta agrega la medida.|  
|*AverageOfChildren*|La medida se agrega devolviendo la media de sus elementos secundarios.|  
|*FirstChild*|Se agrega la medida devolviendo su primer miembro secundario.|  
|*LastChild*|Se agrega la medida devolviendo su último miembro secundario.|  
|*FirstNonEmpty*|Se agrega la medida devolviendo su primer miembro no vacío.|  
|*LastNonEmpty*|Se agrega la medida devolviendo su último miembro no vacío.|  
  
 La enumeración que corresponde a los valores permitidos para **AggregateFunction** en el objeto de Analysis Management Objects (AMO) es el modelo <xref:Microsoft.AnalysisServices.AggregationFunction>.  
  
## <a name="see-also"></a>Vea también  
 [Propiedades & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
