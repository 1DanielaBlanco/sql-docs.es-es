---
title: Elemento ServerProperties (ASSL) | Documentos de Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0c122c73c9830af99037c8ea96da44e37ddc519e
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="serverproperties-element-assl"></a>Elemento ServerProperties (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene la colección de [ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md) elementos asociados a un [Server](../../../analysis-services/scripting/objects/server-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<Server>  
      ...  
   <ServerProperties>  
      <ServerProperty>...</ServerProperty>  
   </ServerProperties>  
   ...  
</Server>  
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
|Elementos primarios|[Server](../../../analysis-services/scripting/objects/server-element-assl.md)|  
|Elementos secundarios|[ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md)|  
  
## <a name="remarks"></a>Comentarios  
 El elemento correspondiente en el modelo de objetos de Analysis Management Objects (AMO) es <xref:Microsoft.AnalysisServices.ServerPropertyCollection>.  
  
## <a name="see-also"></a>Vea también  
 [Colecciones de & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
