---
title: Conjunto de filas DMSCHEMA_MINING_MODEL_XML | Documentos de Microsoft
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
- DMSCHEMA_MINING_MODEL_XML
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_MODEL_XML rowset
ms.assetid: f58b00e9-3f72-4cff-b448-21a9fb529772
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 37bfb0f304e8204f28f83589a6c16625c178444c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36197041"
---
# <a name="dmschemaminingmodelxml-rowset"></a>Conjunto de filas DMSCHEMA_MINING_MODEL_XML
  Devuelve la estructura XML del modelo de minería de datos. El formato de las cadenas XML sigue el estándar PMML 2.1 (Lenguaje de marcado de modelos de predicción).  
  
## <a name="rowset-columns"></a>Columnas del conjunto de filas  
 El `DMSCHEMA_MINING_MODEL_XML` filas contiene las columnas siguientes.  
  
|Nombre de columna|Indicador de tipo|Longitud|Descripción|  
|-----------------|--------------------|------------|-----------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`||Nombre del catálogo. Se rellena con el nombre de la base de datos de la que es miembro el modelo.|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`||Nombre del esquema sin certificar. Esta columna no es compatible con [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; siempre contiene `NULL`.|  
|`MODEL_NAME`|`DBTYPE_WSTR`||Nombre del modelo. Esta columna no puede contener valores `NULL`.|  
|`MODEL_TYPE`|`DBTYPE_WSTR`||Tipo del modelo. Es una cadena específica del proveedor. Puede ser `NULL`:|  
|`MODEL_GUID`|`DBTYPE_GUID`||GUID que identifica el modelo. Los proveedores que no utilizan GUID para identificar las tablas devuelven `NULL`.|  
|`MODEL_PMML`|`DBTYPE_WSTR`||Representación XML del contenido del modelo en formato PMML.|  
|`SIZE`|`DBTYPE_UI4`||Número de bytes de la secuencia de XML.|  
|`LOCATION`|`DBTYPE_WSTR`||Ubicación del archivo XML. Es `NULL` si no se utiliza un archivo físico para el almacenamiento.|  
  
 Este conjunto de filas de esquema no está ordenado.  
  
## <a name="restriction-columns"></a>Columnas de restricción  
 El conjunto de filas DMSCHEMA_MINING_MODEL_XML se puede restringir en las columnas enumeradas en la tabla siguiente.  
  
|Nombre de columna|Indicador de tipo|Estado de restricción|  
|-----------------|--------------------|-----------------------|  
|`MODEL_CATALOG`|`DBTYPE_W`STR|Opcional.|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`|Opcional.|  
|`MODEL_NAME`|`DBTYPE_WSTR`|Opcional.|  
|`MODEL_TYPE`|`DBTYPE_WSTR`|Opcional.|  
  
## <a name="see-also"></a>Vea también  
 [Conjuntos de filas de esquema de minería de datos](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  