---
title: Elemento EndOfData (ASSL) | Documentos de Microsoft
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
apiname: EndOfData Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: EndOfData
helpviewer_keywords: EndOfData element
ms.assetid: 4cee48bc-d486-4125-9d65-f323c6ec9d09
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 87426bbdd3e0f19deca928448c5d3874d9ea85f8
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2017
---
# <a name="endofdata-element-assl"></a>Elemento EndOfData (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Indica el final de los datos recibidos de un [PushedDataSource](../../../analysis-services/scripting/data-type/pusheddatasource-data-type-assl.md) elemento.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<PushedDataSource>  
   ...  
   <EndOfData>...</EndOfData>  
   ...  
</PushedDataSource  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|Booleano|  
|Valor predeterminado|Ninguno|  
|Cardinalidad|1-1: Elemento requerido que puede aparecer una y solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|[PushedDataSource](../../../analysis-services/scripting/data-type/pusheddatasource-data-type-assl.md)|  
|Elementos secundarios|Ninguno|  
  
## <a name="remarks"></a>Comentarios  
 El último paquete de datos de la **PushedDataSource** debe establecer el **EndOfData** elemento **True**.  
  
## <a name="see-also"></a>Vea también  
 [Propiedades &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
