---
title: Elemento KeyUniquenessGuarantee (ASSL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: KeyUniquenessGuarantee Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: KeyUniquenessGuarantee
helpviewer_keywords: KeyUniquenessGuarantee element
ms.assetid: 6e0cf107-dd02-4bbd-94f5-c26d96438d4b
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ebeb77c0b03dadc5ab08e69eefed438d3467b910
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="keyuniquenessguarantee-element-assl"></a>Elemento KeyUniquenessGuarantee (ASSL)
  Indica si se garantiza la validez de la relación entre la clave de atributo y su nombre y la relación con los atributos relacionados.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <KeyUniquenessGuarantee>...</KeyUniquenessGuarantee>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|Booleano|  
|Valor predeterminado|False|  
|Cardinalidad|0-1: Elemento opcional que puede aparecer solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elemento primario|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Elementos secundarios|Ninguno|  
  
## <a name="remarks"></a>Comentarios  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] utiliza la **KeyUniquenessGuarantee** elemento para optimizar la construcción de consulta para recuperar los miembros del origen de datos subyacente para este atributo.  
  
 El elemento que corresponde al elemento primario de **KeyUniquenessGuarantee** en el objeto de Analysis Management Objects (AMO) es el modelo <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Vea también  
 [Propiedades &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
