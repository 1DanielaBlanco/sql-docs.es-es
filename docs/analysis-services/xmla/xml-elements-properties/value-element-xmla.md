---
title: Valor de elemento (XMLA) | Documentos de Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Value Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.value
- urn:schemas-microsoft-com:xml-analysis#Value
- http://schemas.microsoft.com/analysisservices/2003/engine#Value
helpviewer_keywords:
- Value element
ms.assetid: f87ca7f8-d9fe-4730-a706-5d50fcfe21df
caps.latest.revision: 14
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 61a5fa276918a176eb60340fce44e5dfdae0d4da
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="value-element-xmla"></a>Elemento Value (XMLA)
  Contiene el valor deseado de un [atributo](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md) elemento que va a agregar un [insertar](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md) comando, o un [celda](../../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md) elemento que se va a actualizar una [UpdateCells](../../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)comando.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<Attribute> <!-- or Cell --!>  
   ...  
   <Value>...</Value>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|Cualquiera|  
|Valor predeterminado|Ninguno|  
|Cardinalidad|1-1: Elemento necesario que se produce una vez y solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|[Atributo](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md), [celda](../../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md)|  
|Elementos secundarios|Ninguno|  
  
## <a name="remarks"></a>Comentarios  
 Para **atributo** elementos, el **valor** elemento contiene el valor deseado que el miembro debería contener una vez el **insertar** comando se confirma. Para obtener más información acerca de cómo insertar los miembros, vea [Insertar, actualizar y quitar miembros &#40; XMLA &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
 Para **celda** elementos, el **valor** elemento contiene el valor deseado que la celda debe contener una vez el **UpdateCells** comando se confirma. El valor real almacenado en la tabla de reescritura para esa celda es la diferencia entre el valor original de la celda y el valor deseado de la misma.  
  
 El tipo de datos utilizado por este elemento debería coincidir con el tipo de datos de la celda que se va a estar actualizada.  
  
 Para más información sobre la actualización de celdas, vea [Actualizar celdas &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/updating-cells-xmla.md).  
  
## <a name="see-also"></a>Vea también  
 [Elemento CellOrdinal &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/cellordinal-element-xmla.md)   
 [Insertar elemento &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Elemento UpdateCells &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)   
 [Propiedades &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
