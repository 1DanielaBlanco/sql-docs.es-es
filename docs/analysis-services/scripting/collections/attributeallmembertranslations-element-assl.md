---
title: Elemento AttributeAllMemberTranslations (ASSL) | Documentos de Microsoft
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
- AttributeAllMemberTranslations Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AttributeAllMemberTranslations
helpviewer_keywords:
- AttributeAllMemberTranslations element
ms.assetid: 1a0d86ea-d95d-4d93-b321-acd35ed4ac26
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a04a690805037616558f160539cb55e48f6bb8cf
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="attributeallmembertranslations-element-assl"></a>Elemento AttributeAllMemberTranslations (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Contiene la colección de traducciones para el título del miembro All de la dimensión.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<Dimension>  
   ...  
   <AttributeAllMemberTranslations>  
      <AttributeAllMemberTranslation xsi:type="Translation">...</AttributeAllMemberTranslation>  
   </AttributeAllMemberTranslations>  
      ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Características del elemento  
  
|Característica|Description|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|None|  
|Valor predeterminado|None|  
|Cardinalidad|0-1: Elemento opcional que puede aparecer una y solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|[Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
|Elementos secundarios|[AttributeAllMemberTranslation](../../../analysis-services/scripting/objects/attributeallmembertranslation-element-assl.md)|  
  
## <a name="remarks"></a>Comentarios  
 El elemento que corresponde al elemento primario de **AttributeAllMemberTranslations** en el objeto de Analysis Management Objects (AMO) es el modelo <xref:Microsoft.AnalysisServices.Dimension>.  
  
## <a name="see-also"></a>Vea también  
 [Translation, elemento &#40; ASSL &#41;](../../../analysis-services/scripting/objects/translation-element-assl.md)   
 [Colecciones de &#40; ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
