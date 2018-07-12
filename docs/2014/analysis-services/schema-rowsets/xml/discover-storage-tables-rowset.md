---
title: Conjunto de filas DISCOVER_STORAGE_TABLES | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 13df6f10-8efe-4fe9-83a6-96d108809ed1
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 97f5e645098da53c720d37814b4dc4dbfe6f1c76
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37169556"
---
# <a name="discoverstoragetables-rowset"></a>DISCOVER_STORAGE_TABLES, conjunto de filas
  Permite al cliente determinar las tablas incluidas en una base de datos de Analysis Services que se ejecuta en modo Tabular o SharePoint.  
  
## <a name="rowset-columns"></a>Columnas del conjunto de filas  
 El `DISCOVER_STORAGE_TABLES` conjunto de filas contiene las siguientes columnas.  
  
|**Nombre de columna**|**Indicador de tipo**|**Longitud**|**Descripción**|  
|---------------------|------------------------|----------------|---------------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`||Especifica el nombre de la base de datos que contiene las tablas.<br /><br /> El `DISCOVER_STORAGE_TABLES` conjunto de filas puede restringirse mediante esta columna. Si esta columna no se utiliza para restringir el conjunto de filas, se utiliza la base de datos actual.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Especifica el cubo o el modelo que contiene las tablas.<br /><br /> El `DISCOVER_STORAGE_TABLES` conjunto de filas puede restringirse mediante esta columna.|  
|`MEASURE_GROUP_NAME`|`DBTYPE_WSTR`||Nombre del grupo de medida.|  
|`PARTITION_NAME`|`DBTYPE_WSTR`||Nombre de la partición.|  
|`DIMENSION_NAME`|`DBTYPE_WSTR`||Nombre de la dimensión.|  
|`TABLE_ID`|`DBTYPE_WSTR`||Identificador de la tabla que se utiliza para almacenar la tabla de atributos.|  
|`TABLE_PARTITIONS_COUNT`|`DBTYPE_ WSTR`||Recuento de particiones de la tabla.|  
|`HINT_TABLE_TYPE`|`DBTYPE_ WSTR`||Sugerencia del tipo de tabla.|  
|`ROWS_COUNT`|`DBTYPE_UI4`||Número de filas de la partición.|  
|`RIVIOLATION_COUNT`|`DBTYPE_UI4`||Número de filas con infracciones de integridad referencial.|  
  
## <a name="restriction-columns"></a>Columnas de restricción  
 El `DISCOVER_STORAGE_TABLES` conjunto de filas puede tener restricciones en las columnas enumeradas en la tabla siguiente.  
  
|**Nombre de columna**|**Indicador de tipo**|**Estado de restricción**|  
|---------------------|------------------------|---------------------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`|Opcional.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Opcional.|  
|`MEASURE_GROUP_NAME`|`DBTYPE_WSTR`|Opcional|  
|`PARTITION_NAME`|`DBTYPE_WSTR`|Opcional|  
  
## <a name="example"></a>Ejemplo  
 El ejemplo de código siguiente devuelve una lista de las tablas de almacenamiento y el número de filas de cada una, de la base de datos predeterminada en la conexión actual.  
  
```  
SELECT TABLE_ID, ROWS_COUNT  
FROM $system.DISCOVER_STORAGE_TABLES  
ORDER BY TABLE_ID DESC  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Conjuntos de filas de esquema de Analysis Services](../../schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
