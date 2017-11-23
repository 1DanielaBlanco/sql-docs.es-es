---
title: Elemento DeleteWithDescendants (XMLA) | Documentos de Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DeleteWithDescendants Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#DeleteWithDescendants
- microsoft.xml.analysis.deletewithdescendants
- urn:schemas-microsoft-com:xml-analysis#DeleteWithDescendants
helpviewer_keywords: DeleteWithDescendants element
ms.assetid: adfc9437-aaa7-4364-bcdb-128fcc9a410d
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7420b12875dd521186741726b084fc99131fa5cd
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="deletewithdescendants-element-xmla"></a>Elemento DeleteWithDescendants (XMLA)
  Indica si el comando [Drop](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md) del elemento primario elimina también los descendientes de los miembros de atributo.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<Drop>  
   ...  
   <DeleteWithDescendants>...</DeleteWithDescendants>  
   ...  
</Drop>  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|Booleano|  
|Valor predeterminado|False|  
|Cardinalidad|0-1: Elemento opcional que puede aparecer solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|[Quitar](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)|  
|Elementos secundarios|Ninguno|  
  
## <a name="remarks"></a>Comentarios  
 El elemento **DeleteWithDescendants** determina si el comando **Drop** debe eliminar no solo los miembros de atributo identificados por el elemento [Where](../../../analysis-services/xmla/xml-elements-properties/where-element-xmla.md) , si no también los descendientes de dichos miembros de atributo.  
  
> [!NOTE]  
>  Este elemento solamente se aplica a los miembros de atributo de jerarquías de elementos primarios y secundarios.  
  
 Para más información sobre cómo eliminar y actualizar miembros de atributos, vea [Insertar, actualizar y quitar miembros &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
## <a name="see-also"></a>Vea también  
 [Propiedades &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
