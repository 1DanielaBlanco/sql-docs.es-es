---
title: Elemento de configuración (DTA) | Documentos de Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- Configuration element
ms.assetid: 1478e56f-57c4-4441-bac9-1ac91453839b
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 6cca142282c59539d54d5e1d42d5d2269ac41635
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36104837"
---
# <a name="configuration-element-dta"></a>Configuration (DTA, elemento)
  Establece una configuración especificada por el usuario compuesta por estructuras de diseño físico existentes e hipotéticas para que el Asistente para la optimización de motor de base de datos la analice al optimizar una carga de trabajo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
<DTAInput>  
    <Server>...</Server>  
    <Workload>...</Workload>  
    <TuningOptions>...</TuningOptions  
    <Configuration [SpecificationMode="Relative" | "Absolute"]>  
    ...code removed here...  
    </Configuration>  
</DTAInput>  
```  
  
## <a name="element-attributes"></a>Atributos del elemento  
  
|Atributo Configuration|Descripción|  
|-----------------------------|-----------------|  
|`SpecificationMode`|Opcional. Especifica si el Asistente para la optimización de motor de base de datos debe analizar la configuración especificada con respecto a la configuración actual existente o como una independiente totalmente nueva. Utilice un tipo de datos **string** para especificar este atributo mediante uno de los siguientes valores permitidos:<br /><br /> `Relative`: <br />                  Evalúa la configuración especificada con respecto a la configuración actual existente de las estructuras de diseño físico (índices, vistas indizadas, particiones) de la base de datos que se está optimizando. Por ejemplo: <br />`<Configuration SpecificationMode="Relative">`<br /><br /> `Absolute`: <br />                  Evalúa la configuración especificada como una configuración independiente. Cuando se especifica Absolute, el Asistente para la optimización de motor de base de datos no tiene en cuenta la configuración existente. Por ejemplo:<br />`<Configuration SpecificationMode="Absolute">`|  
  
## <a name="element-characteristics"></a>Características del elemento  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|**Tipo y longitud de los datos**|Ninguno.|  
|**Valor predeterminado**|Ninguno.|  
|**Repetición**|Opcional. Puede utilizar una vez por cada `DTAInput` elemento.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elementos|  
|------------------|--------------|  
|**Elemento primario**|[Elemento DTAInput &#40;DTA&#41;](dtainput-element-dta.md)|  
|**Elementos secundarios**|[Elemento de servidor para la configuración de &#40;DTA&#41;](server-element-for-configuration-dta.md)|  
  
## <a name="example"></a>Ejemplo  
 Para obtener un ejemplo de uso de este elemento, vea [Ejemplo de archivo de entrada XML con configuración especificada por el usuario &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia del archivo de entrada XML &#40;Asistente para la optimización de motor de base de datos&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  