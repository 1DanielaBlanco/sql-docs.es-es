---
title: Elemento WritebackTableCreation (XMLA) | Documentos de Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e04f44d9caa3ae51ea141997e83de54524000fee
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/02/2018
ms.locfileid: "34576857"
---
# <a name="writebacktablecreation-element-xmla"></a>Elemento WritebackTableCreation (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Determina si una tabla de reescritura se crea durante la [proceso](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) operación.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<Process>  
...  
   <WritebackTableCreation>...</WritebackTableCreation>  
...  
</Process>  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|String (enumeración)|  
|Valor predeterminado|None|  
|Cardinalidad|0-1: Elemento opcional que puede aparecer una y solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|[Procesar](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)|  
|Elementos secundarios|None|  
  
## <a name="remarks"></a>Notas  
 Para obtener más información acerca de las opciones de procesamiento disponibles para los objetos en una instancia de Analysis Services, consulte [procesar un modelo multidimensional &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
 El valor del elemento **WritebackTableCreation** se limita a las cadenas listadas en la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|*Crear*|Crear crea una nueva tabla de reescritura si no existe una. Se produce un error si la tabla de reescritura ya existe.|  
|*CreateAlways*|Cree una nueva tabla de reescritura, sobrescribiendo cualquier tabla de reescritura existente.|  
|*UseExisting*|Utilice la tabla de reescritura existente, si ya existe una. Si no existe una, se produce un error.|  
  
## <a name="see-also"></a>Vea también
 [Propiedades &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
