---
title: Bloquear elemento (ASSL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Block Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Block
helpviewer_keywords: Block element
ms.assetid: f45c32ae-e4e0-465a-9564-9ccfb10a858f
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e53ea02e3841aaa6bafe91d1373df72f90e34701
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2017
---
# <a name="block-element-assl"></a>Elemento Block (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Contiene todo o parte del contenido binario de un [ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md) elemento.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<Blocks>  
   <Block>...</Block>  
</Blocks>  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|Base64Binary|  
|Valor predeterminado|Ninguno|  
|Cardinalidad|1-n: Elemento necesario que puede aparecer más de una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|[Bloques](../../../analysis-services/scripting/collections/blocks-element-assl.md)|  
|Elementos secundarios|Ninguno|  
  
## <a name="see-also"></a>Vea también  
 [Assembly (elemento) &#40; ASSL &#41;](../../../analysis-services/scripting/objects/assembly-element-assl.md)   
 [Tipo de datos ClrAssembly &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)   
 [Elemento de archivos &#40; ASSL &#41;](../../../analysis-services/scripting/collections/files-element-assl.md)   
 [Elemento File &#40; ASSL &#41;](../../../analysis-services/scripting/objects/file-element-assl.md)   
 [Tipo de datos ClrAssemblyFile &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)   
 [Elemento de datos &#40; ASSL &#41;](../../../analysis-services/scripting/objects/data-element-assl.md)   
 [Tipo de datos DataBlock &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/datablock-data-type-assl.md)   
 [Objetos de &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
