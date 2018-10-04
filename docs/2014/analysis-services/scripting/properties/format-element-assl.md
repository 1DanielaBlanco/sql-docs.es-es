---
title: Formato de elemento (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Format Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Format
helpviewer_keywords:
- Format element
ms.assetid: 881ea707-52a7-46f7-ba16-ac2ec44eca22
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2ed7cf229d4ef65e324a59d2d9292948ae530147
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2018
ms.locfileid: "48228015"
---
# <a name="format-element-assl"></a>Elemento Format (ASSL)
  Contiene el formato requerido de la [DataItem](../data-type/dataitem-data-type-assl.md) elemento.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<DataItem>  
   ...  
   <Format>...</Format>  
      ...  
</DataItem>  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|String|  
|Valor predeterminado|None|  
|Cardinalidad|0-1: Elemento opcional que puede aparecer una y solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elemento primario|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|Elementos secundarios|None|  
  
## <a name="remarks"></a>Comentarios  
 Los valores permitidos para el `Format` elemento son los formatos de Microsoft Office Excel así como las cadenas *TrimRight*, *TrimLeft*, *TrimAll*, y  *TrimNone*. *TrimRight* es el valor predeterminado para el proceso de recorte.  
  
 El valor de este elemento se limita a una de las cadenas enumeradas en la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|Cualquier cadena de formato de Excel|Se da formato a los datos de acuerdo con la cadena de formato con nombre o personalizada que se haya especificado. Es posible especificar cualquier cadena de formato que admita Excel.|  
|*TrimAll*|Los datos se recortan por la izquierda y por la derecha.|  
|*TrimLeft*|Los datos se recortan por la izquierda.|  
|*TrimNone*|No se recortan los datos.|  
|*TrimRight*|Los datos se recortan por la derecha.|  
  
 El elemento que se corresponde con el elemento primario de `Format` en el objeto de Analysis Management Objects (AMO) es el modelo <xref:Microsoft.AnalysisServices.DataItem>.  
  
## <a name="see-also"></a>Vea también  
 [Propiedades &#40;ASSL&#41;](properties-assl.md)  
  
  
