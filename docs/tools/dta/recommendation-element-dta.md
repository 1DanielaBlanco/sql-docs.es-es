---
title: Elemento Recommendation (DTA) | Documentos de Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: XML
helpviewer_keywords: Recommendation element
ms.assetid: 679ea535-865a-4633-a4d3-5b3090515158
caps.latest.revision: "13"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 88ee6ad381638147b1b19a515fb3c55cdf0a7447
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="recommendation-element-dta"></a>Recommendation (DTA, elemento)
  Contiene información sobre los índices hipotéticos que forman parte de una configuración especificada por el usuario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
<Configuration>  
    ...code removed here...  
    <Table>  
      <Name>...</Name>  
      <Recommendation>  
      ...code removed here...  
      </Recommendation>  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|**Tipo y longitud de los datos**|Ninguno.|  
|**Valor predeterminado**|Ninguno.|  
|**Repetición**|Opcional. Se puede utilizar una vez por cada elemento **Table** .|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elementos|  
|------------------|--------------|  
|**Elemento primario**|[Table &#40;DTA, elemento de Schema&#41;](../../tools/dta/table-element-for-schema-dta.md)|  
|**Elementos secundarios**|[Create &#40;DTA, elemento&#41;](../../tools/dta/create-element-dta.md)<br /><br /> Elemento**Drop** . Para obtener más información, vea el [esquema XML del Asistente para la optimización de motor de base de datos](http://go.microsoft.com/fwlink/?linkid=43100).|  
  
## <a name="remarks"></a>Comentarios  
 Este elemento tiene el nombre **RecommendationTypecomplexType** en el esquema XML del Asistente para la optimización de motor de base de datos. Se utiliza para especificar índices para una configuración hipotética. No confunda este elemento **Recommendation** con los otros tipos que se pueden usar para especificar la creación de particiones (**RecommendationPType**) o vistas (**RecommendationViewType**). Para obtener información sobre los demás tipos de elementos **Recommendation** , vea el [esquema XML del Asistente para la optimización de motor de base de datos](http://go.microsoft.com/fwlink/?linkid=43100).  
  
## <a name="example"></a>Ejemplo  
 Para obtener un ejemplo de uso de este elemento, vea [Ejemplo de archivo de entrada XML con configuración especificada por el usuario &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia del archivo de entrada XML &#40;Asistente para la optimización de motor de base de datos&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
