---
title: Elemento HoldoutMaxPercent | Documentos de Microsoft
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
topic_type:
- apiref
f1_keywords:
- HoldoutMaxPercent
helpviewer_keywords:
- HoldoutMaxPercent element
ms.assetid: e375cc51-5f9d-4252-98a1-326ca0dbbf83
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 089ed35d7c900e48da2ba283f8bcf9ee4a29fa7a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36105945"
---
# <a name="holdoutmaxpercent-element"></a>Elemento HoldoutMaxPercent
  Especifica el porcentaje máximo de casos del origen de datos que se usará para la partición de exclusión que contiene el conjunto de pruebas de un [MiningStructure](../objects/miningstructure-element-assl.md) elemento. Los casos restantes se usan para aprendizaje. Un valor 0 indica que no hay ningún límite con respecto al número de casos que se pueden considerar como el conjunto de pruebas.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<MiningStructure>  
   ...  
   <ddl100_100:HoldoutMaxPercent>...</ddl100_100:HoldoutMaxPercent>  
   ...  
</MiningStructure>  
```  
  
## <a name="element-characteristics"></a>Características del elemento  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|Entero entre 0 y 99|  
|Valor predeterminado|30|  
|Cardinalidad|0-1: Elemento opcional que puede producirse una sola y única vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elemento primario|[MiningStructure](../objects/miningstructure-element-assl.md)|  
|Elementos secundarios|None|  
  
## <a name="remarks"></a>Notas  
 Si especifica los valores de `HoldoutMaxPercent` y `HoldoutMaxCases`, el algoritmo limita el conjunto de pruebas al menor de los dos valores.  
  
 Si `HoldoutMaxCases` está establecido en el valor predeterminado de 0 y no se ha establecido un valor para `HoldoutMaxPercent`, el algoritmo usa el conjunto de datos completo para aprendizaje.  
  
 Las nuevas propiedades `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed`, o `HoldoutActualSize` sólo están disponibles en [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] y versiones posteriores. Por lo tanto, es necesario establecer estas propiedades como prefijos usando el nuevo espacio de nombres, tal como se muestra en la descripción de la sintaxis, o [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] devolverá un error.  
  
> [!NOTE]  
>  En [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] no admitía el uso de particiones de exclusión en una estructura de minería de datos. Por consiguiente, las instrucciones ASSL (Lenguaje de scripting de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]) que contengan uno de los parámetros de exclusión `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed` o `HoldoutActualSize`, no se pueden utilizar en [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Si usa uno de estos parámetros de exclusión en una instrucción ASSL en [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] devolverá un error.  
  
 El elemento que corresponde al elemento primario de `HoldoutMaxPercent` en el objeto de Analysis Management Objects (AMO) es el modelo <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>Vea también  
 [Propiedades &#40;ASSL&#41;](properties-assl.md)   
 [Elemento HoldoutMaxCases](holdoutmaxcases-element.md)   
 [Holdoutseed, elemento](holdoutseed-element.md)   
 [Elemento HoldoutActualSize](holdoutactualsize-element.md)  
  
  