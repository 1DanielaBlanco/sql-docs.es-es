---
title: Bloquea el elemento (ASSL) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Blocks Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Blocks
helpviewer_keywords:
- Blocks element
ms.assetid: d6fd4e6b-b5bd-43cd-9c28-48af57cf977c
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ae3ab1e76831f59dccc5c89c30553596977fe067
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="blocks-element-assl"></a>Elemento Blocks (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene la colección de bloques de datos binarios que representan el contenido binario de un [ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md) elemento.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<Data xsi:type="DataBlock">  
   ...  
   <Blocks>  
      <Block>...</Block>  
   </Blocks>  
   ...  
</File>  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|Ninguno|  
|Valor predeterminado|Ninguno|  
|Cardinalidad|1-1: Elemento necesario que se produce una vez y solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|[Datos](../../../analysis-services/scripting/objects/data-element-assl.md) de tipo [DataBlock](../../../analysis-services/scripting/data-type/datablock-data-type-assl.md)|  
|Elementos secundarios|[Bloque](../../../analysis-services/scripting/objects/block-element-assl.md)|  
  
## <a name="remarks"></a>Comentarios  
 El elemento que corresponde al elemento primario de **bloques** en el objeto de Analysis Management Objects (AMO) es el modelo <xref:Microsoft.AnalysisServices.ClrAssemblyFile>.  
  
## <a name="see-also"></a>Vea también  
 [Assembly (elemento) & #40; ASSL & #41;](../../../analysis-services/scripting/objects/assembly-element-assl.md)   
 [Tipo de datos ClrAssembly &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)   
 [Archivos elemento &#40;ASSL&#41;](../../../analysis-services/scripting/collections/files-element-assl.md)   
 [Elemento File & #40; ASSL & #41;](../../../analysis-services/scripting/objects/file-element-assl.md)   
 [Tipo de datos ClrAssemblyFile & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)   
 [Elemento de datos & #40; ASSL & #41;](../../../analysis-services/scripting/objects/data-element-assl.md)   
 [Tipo de datos DataBlock & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/datablock-data-type-assl.md)   
 [Elemento Blocks](../../../analysis-services/scripting/collections/blocks-element-assl.md)   
 [Bloquear elemento & #40; ASSL & #41;](../../../analysis-services/scripting/objects/block-element-assl.md)   
 [Colecciones de & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
