---
title: "Tipo de datos DimensionAttributeBinding (fuera de línea) (ASSL) | Documentos de Microsoft"
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
apiname: DimensionAttributeBinding Data Type (out-of-line)
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DimensionAttributeBinding data type
ms.assetid: d8ec77a9-749f-4b08-8d56-8b6514a70248
caps.latest.revision: "9"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 48c20d78a2123d8881b6eecf05f925e4b7517cc2
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2017
---
# <a name="dimensionattributebinding-data-type-out-of-line-assl"></a>Tipo de datos DimensionAttributeBinding (fuera de línea) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Define un tipo de datos derivado que representa un enlace fuera de línea para un atributo de una dimensión.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<DimensionAttributeBinding>  
   <!-- The following elements extend Binding -->  
   <DatabaseID>...</DatabaseID>  
   <DimensionID>...</DimensionID>  
   <AttributeID>...</AttributeID>  
   <KeyColumns>...</KeyColumns>  
   <NameColumn>...</NameColumn>  
   <Translations>...</Translations>  
</DimensionAttributeBinding>  
```  
  
## <a name="data-type-characteristics"></a>Características del tipo de datos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipos de datos base|[Enlace](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
|Tipos de datos derivados|Ninguno|  
  
## <a name="data-type-relationships"></a>Relaciones entre tipos de datos  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|Ninguno|  
|Elementos secundarios|[AttributeID](../../../analysis-services/scripting/properties/attributeid-element-assl.md), [DatabaseID](../../../analysis-services/xmla/xml-elements-properties/databaseid-element-xmla.md), [DimensionID](../../../analysis-services/scripting/properties/dimensionid-element-assl.md), [KeyColumns](../../../analysis-services/scripting/collections/keycolumns-element-assl.md), [NameColumn](../../../analysis-services/scripting/objects/namecolumn-element-assl.md), [ Traducciones](../../../analysis-services/scripting/collections/translations-element-assl.md)|  
|Elementos derivados|[Enlace](../../../analysis-services/xmla/xml-elements-properties/binding-element-xmla.md) ([enlaces](../../../analysis-services/scripting/collections/attributes-element-assl.md) colección de XML for Analysis (XMLA) [lote](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md) y [proceso](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) comandos)|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de los enlaces fuera de línea, consulte [orígenes de datos y enlaces &#40; SSAS Multidimensional &#41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>Vea también  
 [Analysis Services Scripting Language tipos de datos XML &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
