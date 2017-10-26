---
title: Elemento MiningStructure (ASSL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- MiningStructure Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- MiningStructure
helpviewer_keywords:
- MiningStructure element
ms.assetid: b943cd92-0ed8-4bd8-8fbc-7dab0534aede
caps.latest.revision: 48
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0f0ce9ca930e54c1cf8ac989330e00f298a06a28
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="miningstructure-element-assl"></a>Elemento MiningStructure (ASSL)
  Define la estructura de un conjunto de modelos de minería de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<MiningStructures>  
   <MiningStructure>  
      <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</<Description>  
      <Source>...</Source>  
      <CreatedTimestamp>...</<CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <LastProcessed>...</LastProcessed>  
      <Translations>...</Translations>  
      <Language>...</Language>  
            <Collation>...</Collation>  
      <ErrorConfiguration>...</ErrorConfiguration>  
      <CacheMode>...</CacheMode>  
            <Columns>...</Columns>  
      <State>...</State>  
      <HoldoutActualSize>...</HoldoutActualSize>  
      <HoldoutMaxCases>...</HoldoutMaxCases>  
      <HoldoutMaxPercent>...</HoldoutMaxPercent>  
      <HoldoutSeed>...</HoldoutSeed>        
            <MiningStructurePermissions>...</<MiningStructurePermissions>  
            <MiningModels>...</MiningModels>  
            <Annotations>...</Annotations>  
   </MiningStructure>  
</MiningStructures>  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|Ninguno|  
|Valor predeterminado|Ninguno|  
|Cardinalidad|0-n: elemento opcional que puede aparecer más de una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|[MiningStructures](../../../analysis-services/scripting/collections/miningstructures-element-assl.md)|  
|Elementos secundarios|[Anotaciones](../../../analysis-services/scripting/collections/annotations-element-assl.md), [CacheMode](../../../analysis-services/scripting/properties/cachemode-element-assl.md), [intercalación](../../../analysis-services/scripting/properties/collation-element-assl.md), [columnas](../../../analysis-services/scripting/collections/columns-element-assl.md), [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md), [ Descripción](../../../analysis-services/scripting/properties/description-element-assl.md), [ErrorConfiguration](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md),<br /><br /> [HoldoutActualSize](../../../analysis-services/scripting/properties/holdoutactualsize-element.md),<br /><br /> [HoldoutMaxCases](../../../analysis-services/scripting/properties/holdoutmaxcases-element.md),<br /><br /> [HoldoutMaxPercent](../../../analysis-services/scripting/properties/holdoutmaxpercent-element.md),<br /><br /> [HoldoutSeed](../../../analysis-services/scripting/properties/holdoutseed-element.md),<br /><br /> [Id. de](../../../analysis-services/scripting/properties/id-element-assl.md), [lenguaje](../../../analysis-services/scripting/properties/language-element-assl.md), [LastProcessed](../../../analysis-services/scripting/properties/lastprocessed-element-assl.md), [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md), [MiningModels](../../../analysis-services/scripting/collections/miningmodels-element-assl.md), [ MiningStructurePermissions](../../../analysis-services/scripting/collections/miningstructurepermissions-element-assl.md), [nombre](../../../analysis-services/scripting/properties/name-element-assl.md), [origen](../../../analysis-services/scripting/properties/source-element-binding-assl.md), [estado](../../../analysis-services/scripting/properties/state-element-assl.md), [traducciones](../../../analysis-services/scripting/collections/translations-element-assl.md)|  
  
## <a name="remarks"></a>Comentarios  
 La estructura de minería de datos define las columnas y los enlaces. Después de definir una estructura de minería, puede utilizarla para definir muchos modelos de minería. La estructura de minería y cada modelo de minería que contiene se pueden procesar independientemente.  
  
> [!NOTE]  
>  Las propiedades de exclusión, **HoldoutMaxCases**, **HoldoutMaxPercent**, **HoldoutSeed**, y **HoldoutActualSize**, se introdujeron en [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Le permiten definir una partición en una estructura de minería que actúa como el conjunto de pruebas para todos los modelos de minería que están asociados a la estructura. [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] no admite estas propiedades. Por consiguiente, si intenta utilizar estas propiedades en una instancia de [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] devolverá un error.  
  
## <a name="drillthrough-to-structure-columns"></a>Obtener detalles para las columnas de una estructura  
 En [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], se ha agregado un nuevo elemento de permiso para el [miningstructurepermissions, elemento &#40; ASSL &#41; ](../../../analysis-services/scripting/collections/miningstructurepermissions-element-assl.md) colección. Si agrega **AllowDrillthrough** permiso tanto la [MiningStructurePermissions](../../../analysis-services/scripting/collections/miningstructurepermissions-element-assl.md) y [MiningModelPermission](../../../analysis-services/scripting/objects/miningmodelpermission-element-assl.md) colecciones, obtención de detalles está habilitada desde el modelo de minería de datos a la estructura, de forma que los miembros de un rol que tenga **AllowDrillthrough** permisos en el modelo pueden consultar el modelo de minería de datos y devolver columnas de estructura que no se incluyeron en el modelo.  
  
 Por consiguiente, para proteger información confidencial o datos personales, debería crear la vista del origen de datos de forma que enmascare los datos confidenciales y conceder permiso **AllowDrillthrough** en la estructura de minería solo cuando sea necesario. Para obtener más información, vea [AllowDrillThrough, elemento &#40; ASSL &#41; ](../../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md).  
  
 El elemento correspondiente en el modelo de objetos de Analysis Management Objects (AMO) es <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>Vea también  
 [MiningModel, elemento &#40; ASSL &#41;](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)   
 [Objetos de &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)   
 [SELECT &#40; DMX &#41;](../../../dmx/select-dmx.md)  
  
  

