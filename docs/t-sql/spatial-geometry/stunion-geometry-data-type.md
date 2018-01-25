---
title: STUnion (tipo de datos geometry) | Documentos de Microsoft
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STUnion (geometry Data Type)
- STUnion_TSQL
dev_langs: TSQL
helpviewer_keywords: STUnion (geometry Data Type)
ms.assetid: 5b168118-137d-402f-9173-fee3f365a89c
caps.latest.revision: "23"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 45156b37fbc46ed92cb342eb1b1e82baa93131f7
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="stunion-geometry-data-type"></a>STUnion (tipo de datos geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Devuelve un objeto que representa la unión de un **geometry** instancia con otro **geometry** instancia.
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
.STUnion ( other_geometry )  
```  
  
## <a name="arguments"></a>Argumentos  
 *other_geometry*  
 Es otra **geometry** instancia para formar la unión con la instancia en la que `STUnion()` que se está llamando.  
  
## <a name="return-types"></a>Tipos devueltos  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo de valor devuelto: **geometry**  
  
 Tipo de valor devuelto de CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Comentarios  
 Este método siempre devuelve null si los identificadores de referencia espacial (SRID) de la **geometry** instancias no coinciden. El resultado puede contener segmentos de arco circulares solo si las instancias de entrada contienen segmentos de arco circulares.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-computing-the-union-of-two-polygon-instances"></a>A. Calcular la unión de dos instancias de Polygon  
 En el ejemplo siguiente se usa `STUnion()` para calcular la unión de dos instancias de `Polygon`.  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 0 2, 2 2, 2 0, 0 0))', 0);  
SET @h = geometry::STGeomFromText('POLYGON((1 1, 3 1, 3 3, 1 3, 1 1))', 0);  
SELECT @g.STUnion(@h).ToString();  
```  
  
### <a name="b-computing-the-union-of-a-polygon-instance-with-a-curvepolygon-instance"></a>B. Calcular la unión de una instancia de Polygon con una instancia de CurvePolygon  
 En el siguiente ejemplo se devuelve una instancia de `GeometryCollection` que contiene un segmento de arco circular.  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON(CIRCULARSTRING(0 -4, 4 0, 0 4, -4 0, 0 -4))';  
 DECLARE @h geometry = 'POLYGON((5 -1, 5 -3, 7 -3, 7 -1, 5 -1))';  
 SELECT @g.STUnion(@h).ToString();
 ```  
  
 `STUnion()` devuelve un resultado que contiene un segmento de arco circular porque la instancia que invocó `STUnion()` contiene un segmento de arco circular.  
  
## <a name="see-also"></a>Vea también  
 [Métodos de OGC en instancias de geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

