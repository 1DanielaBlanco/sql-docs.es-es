---
title: Valor de elemento (XMLA) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Value Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.value
- urn:schemas-microsoft-com:xml-analysis#Value
- http://schemas.microsoft.com/analysisservices/2003/engine#Value
helpviewer_keywords:
- Value element
ms.assetid: f87ca7f8-d9fe-4730-a706-5d50fcfe21df
caps.latest.revision: 14
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 7a422298e8d1b77f3d036b4cea5761dc6dc6dde4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36104322"
---
# <a name="value-element-xmla"></a>Elemento Value (XMLA)
  Contiene el valor deseado de un [atributo](attribute-element-xmla.md) elemento que va a agregar un [insertar](../xml-elements-commands/insert-element-xmla.md) comando, o un [celda](cell-element-xmla.md) elemento que se va a actualizar una [UpdateCells](../xml-elements-commands/updatecells-element-xmla.md)comando.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<Attribute> <!-- or Cell --!>  
   ...  
   <Value>...</Value>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>Características del elemento  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|Cualquiera|  
|Valor predeterminado|None|  
|Cardinalidad|1-1: Elemento necesario que se produce una vez y solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|[Atributo](attribute-element-xmla.md), [celda](cell-element-xmla.md)|  
|Elementos secundarios|None|  
  
## <a name="remarks"></a>Notas  
 Para los elementos `Attribute`, el elemento `Value` contiene el valor deseado que el miembro debería contener una vez confirmado el comando `Insert`. Para obtener más información acerca de cómo insertar los miembros, vea [Insertar, actualizar y quitar miembros &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
 Para los elementos `Cell`, el elemento `Value` contiene el valor deseado que la celda debería contener una vez confirmado el comando `UpdateCells`. El valor real almacenado en la tabla de reescritura para esa celda es la diferencia entre el valor original de la celda y el valor deseado de la misma.  
  
 El tipo de datos utilizado por este elemento debería coincidir con el tipo de datos de la celda que se va a estar actualizada.  
  
 Para más información sobre la actualización de celdas, vea [Actualizar celdas &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/updating-cells-xmla.md).  
  
## <a name="see-also"></a>Vea también  
 [Elemento CellOrdinal &#40;XMLA&#41;](cellordinal-element-xmla.md)   
 [Insertar elemento &#40;XMLA&#41;](../xml-elements-commands/insert-element-xmla.md)   
 [Elemento UpdateCells &#40;XMLA&#41;](../xml-elements-commands/updatecells-element-xmla.md)   
 [Propiedades &#40;XMLA&#41;](xml-elements-properties.md)  
  
  