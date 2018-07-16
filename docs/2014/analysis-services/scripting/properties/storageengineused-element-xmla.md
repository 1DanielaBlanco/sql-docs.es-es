---
title: Elemento StorageEngineUsed (XMLA) | Microsoft Docs
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
api_name:
- StorageEngineUsed Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
ms.assetid: 98895c10-f3c2-4d8a-be94-6128c828561d
caps.latest.revision: 9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c6c8f7cdca7fb8134a27c8d1319385861294893a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37203966"
---
# <a name="storageengineused-element-xmla"></a>Elemento StorageEngineUsed (XMLA)
  Contiene un valor de solo lectura que describe el tipo de base de datos actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<Databases>  
      <Database>  
      <Name>...</Name>  
      <ID>...</ID>  
      <CreatedTimestamp>...</CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <LastUpdate>...</LastUpdate>  
      <Description>...</Description>  
      <State>   </State>  
      <AggregationPrefix>...</AggregationPrefix>  
      <EstimatedSize>...</EstimatedSize>  
      <LastProcessed>...</LastProcessed>  
      <Language>...</Language>  
            <Collation>...</Collation>  
            <Visible>...</Visible>  
      <MasterDatasourceID>...</MasterDataSourceID>  
      <Accounts>...</Accounts>  
      <DataSources>...</DataSources>  
      <DataSourceViews>...</DataSourceViews>  
            <Dimensions>...</Dimensions>  
      <Cubes>...</Cubes>  
            <MiningStructures>...</MiningStructures>  
      <Roles>...</Roles>  
      <Assemblies>...</Assemblies>  
      <DatabasePermissions>...</DatabasePermissions>  
      <Translations>...</Translations>  
      <Annotations>...</Annotations>  
            <StorageEngineUsed >...</StorageEngineUsed>  
   </Database>  
</Databases>  
```  
  
## <a name="element-characteristics"></a>Características del elemento  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|String (enumeración)|  
|Valor predeterminado|None|  
|Cardinalidad|1-1: Elemento necesario que se produce una vez y solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|[database](../objects/database-element-assl.md)|  
|Elementos secundarios|None|  
  
## <a name="remarks"></a>Notas  
 El valor de este elemento se limita a una de las cadenas enumeradas en la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|*Tradicional*|El modelo de la base de datos corresponde a un modo de almacenamiento MOLAP, HOLAP o ROLAP.|  
|*InMemory*|El modelo de base de datos corresponde a un modo de almacenamiento de IMBI.|  
|*Mixto*|El modelo de base de datos mezcla los modos de almacenamiento IMBI, MOLAP, HOLAP o ROLAP.|  
  
 La enumeración que corresponde a los valores permitidos para `StorageEngineUsed` en el objeto de Analysis Management Objects (AMO) es el modelo <xref:Microsoft.AnalysisServices.StorageEngineUsed>.  
  
 Los elementos que corresponden a los elementos primarios de `StorageEngineUsed` en el modelo de objetos Objetos de administración de análisis (AMO) son <xref:Microsoft.AnalysisServices.Database>.  
  
  
