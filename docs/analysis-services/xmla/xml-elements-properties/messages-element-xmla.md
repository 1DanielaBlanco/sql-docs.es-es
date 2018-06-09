---
title: Mensajes de elemento (XMLA) | Documentos de Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 21bb83be0940b806c071f305d75826ab65330c15
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34575597"
---
# <a name="messages-element-xmla"></a>Elemento Messages (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene una colección de [mensaje](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md) elementos devuelvan de una instancia de Analysis Services mediante un [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) o [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) llamada al método.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<Resultset>  
   <Messages>  
      <Message>  
   </Messages>  
</Resultset>  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|Ninguno|  
|Valor predeterminado|Ninguno|  
|Cardinalidad|0-1: Elemento opcional que puede aparecer una y solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|[Conjunto de resultados](../../../analysis-services/xmla/xml-data-types/resultset-data-type-xmla.md)|  
|Elementos secundarios|[de mensaje](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|  
  
## <a name="remarks"></a>Comentarios  
 Este elemento se utiliza en casos en los que una llamada al método **Discover** o un comando XMLA único dentro de una llamada al método **Execute** se completa correctamente, pero con errores o advertencias. En tales casos se agrega un elemento **Messages** al elemento [root](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) después de todos los otros elementos, que a su vez contiene uno o más elementos **Message** . Cada elemento **Message** representa un mensaje único, un error o una advertencia, devuelta por la instancia [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .  
  
## <a name="see-also"></a>Vea también
 [Propiedades &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
