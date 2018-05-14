---
title: Elemento Translations (XMLA) | Documentos de Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5ee8f87ff70b95e6a4918ada08cbcdddd7a02f1d
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
---
# <a name="translations-element-xmla"></a>Elemento Translations (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene una colección de los elementos [Translation](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md) que se utilizan para identificar las claves de miembro del miembro de atributo representado por el elemento primario [Attribute](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md) .  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<Attribute>  
   ...  
   <Translations>  
      <Translation>...</Translation>  
   </Translations>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|Ninguno|  
|Valor predeterminado|Ninguno|  
|Cardinalidad|0-1: Elemento opcional que puede aparecer solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|[Atributo](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)|  
|Elementos secundarios|[Traducción](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md)|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Insertar elemento & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Actualizar elemento & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Propiedades & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
