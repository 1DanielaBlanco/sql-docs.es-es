---
title: Elemento UnaryOperatorColumn (ASSL) | Documentos de Microsoft
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
- UnaryOperatorColumn Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- UnaryOperatorColumn
helpviewer_keywords:
- UnaryOperatorColumn element
ms.assetid: 10889e51-69e5-4f50-9749-ecbc66c247d3
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7ccb0447a0e68e464ea3dd54f65bc88fa4cbacbc
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="unaryoperatorcolumn-element-assl"></a>Elemento UnaryOperatorColumn (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Define los detalles de una columna que proporciona un operador unario.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <UnaryOperatorColumn xsi:type="DataItem">...</UnaryOperatorColumn>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Características del elemento  
  
|Característica|Description|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|[Elemento de datos](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|Valor predeterminado|None|  
|Cardinalidad|0-1: Elemento opcional que puede aparecer una y solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Elementos secundarios|None|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información sobre la **DataItem** tipo, incluida una tabla de objetos de Analysis Services Scripting Language (ASSL) y las propiedades de la **DataItem** los tipos, vea [tipo de datos de elemento de datos &#40; ASSL &#41; ](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md).  
  
 El elemento que corresponde al elemento primario de **UnaryOperatorColumn** en el objeto de Analysis Management Objects (AMO) es el modelo <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Vea también  
 [Objetos de &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
