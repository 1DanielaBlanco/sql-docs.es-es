---
title: Tipo de elemento (XMLA) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Type Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.type
- http://schemas.microsoft.com/analysisservices/2003/engine#Type
- urn:schemas-microsoft-com:xml-analysis#Type
helpviewer_keywords:
- Type element
ms.assetid: 5d898123-a635-402a-be86-8249d7304fa4
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 363b89eddf7794174689c0d6df7805328c88eb70
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="type-element-xmla"></a>Elemento Type (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Determina el tipo de procesamiento que debe realizar la [proceso](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<Process>  
...  
   <Type>...</Type>  
...  
</Process>  
```  
  
## <a name="element-characteristics"></a>Características del elemento  
  
|Característica|Description|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|String (enumeración)|  
|Valor predeterminado|None|  
|Cardinalidad|1-1: Elemento necesario que se produce una vez y solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|[Procesar](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)|  
|Elementos secundarios|None|  
  
## <a name="remarks"></a>Notas  
 Para obtener más información acerca del procesamiento de las opciones disponibles en una instancia de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], consulte [procesar un modelo multidimensional &#40; Analysis Services &#41; ](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
 El valor de la **tipo** elemento se limita a una de las cadenas enumeradas en la tabla siguiente.  
  
|Valor|Description|  
|-----------|-----------------|  
|*ProcessFull*|Quita todos los datos del objeto afectado y después lo procesa.|  
|*ProcessAdd*|Agrega nuevos datos al objeto afectado.|  
|*ProcessUpdate*|Actualiza los datos el objeto afectado.|  
|*ProcessIndexes*|Crea o vuelve a generar índices y agregaciones en el objeto afectado.|  
|*ProcessScriptCache*|Si se procesa el cubo, el servidor volverá a generar la caché de script de MDX. Si no, se producirá un error.<br /><br /> **Tenga en cuenta** se aplica solo al cubo.|  
|*ProcessData*|Procesa los datos sólo en el objeto afectado.|  
|*ProcessDefault*|Detecta el estado del objeto afectado y después ejecuta la opción de procesamiento adecuada en el objeto afectado para optimizarlo y volver a dejarlo en un estado totalmente procesado.|  
|*ProcessClear*|Quita los datos del objeto afectado y todos los objetos relacionados.|  
|*ProcessStructure*|Únicamente procesa los datos del objeto afectado.|  
|*ProcessClearStructureOnly*|Borra los datos únicamente del objeto afectado.|  
  
## <a name="see-also"></a>Ver también  
 [Propiedades &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
