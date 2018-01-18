---
title: Elemento StorageBoundInMB (DTA) | Documentos de Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: dta
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: XML
helpviewer_keywords: StorageBoundInMB element
ms.assetid: a8374910-bf68-4edb-b464-53a3a705e7f4
caps.latest.revision: "12"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e0584999dc8e98243c00f4bbd174d1bfa8b14ba2
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="storageboundinmb-element-dta"></a>StorageBoundInMB (DTA, elemento)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Especifica el espacio máximo en megabytes que pueden consumir la recomendación de optimización del Asistente para la optimización de motor de base de datos (índices y particiones conjunto).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <StorageBoundInMB>...</ StorageBoundInMB >  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|**Tipo y longitud de los datos**|**unsignedInt**, longitud ilimitada.|  
|**Valor predeterminado**|Ninguno.|  
|**Repetición**|Opcional. Solo puede utilizarse una vez para el elemento **TuningOptions** .|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elementos|  
|------------------|--------------|  
|**Elemento primario**|[Tuningoptions, elemento &#40; DTA &#41;](../../tools/dta/tuningoptions-element-dta.md)|  
|**Elementos secundarios**|Ninguno|  
  
## <a name="remarks"></a>Comentarios  
 Cuando se optimizan varias bases de datos, se tienen en cuenta las recomendaciones para todas las bases de datos sobre el cálculo del espacio. De forma predeterminada, el Asistente para la optimización de motor de base de datos asume el menor de los siguientes tamaños de almacenamiento:  
  
-   Tres veces el tamaño actual de los datos sin procesar, lo que incluye el tamaño total de los montones y los clúster de las tablas.  
  
-   El espacio disponible en todas las unidades de disco adjuntas más el tamaño de los datos sin procesar.  
  
 El tamaño de almacenamiento predeterminado no incluye los índices no clúster ni las vistas indizadas.  
  
 Si el valor especificado para el elemento **StorageBoundInMB** supera el espacio en disco real, el Asistente para la optimización de motor de base de datos devuelve un error, aunque continúa optimizando. Una vez finalizada la optimización, puede agregar espacio en disco si decide seguir la recomendación.  
  
## <a name="example"></a>Ejemplo  
  
## <a name="description"></a>Descripción  
 El siguiente ejemplo de código muestra cómo establecer un límite de 1500 megabytes como el máximo espacio en disco que una recomendación de optimización puede utilizar:  
  
## <a name="code"></a>código  
  
```  
<DTAInput>  
  <Server>...</Server>  
  <Workload>...</Workload>  
  <TuningOptions>  
    <StorageBoundInMB>1500</StorageBoundInMB>  
...code removed here...  
</DTAInput>  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia del archivo de entrada XML &#40;Asistente para la optimización de motor de base de datos&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
