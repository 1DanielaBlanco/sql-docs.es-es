---
title: STArea (tipo de datos geometry) | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- STArea (geometry Data Type)
- STArea_TSQL
dev_langs: TSQL
helpviewer_keywords: STArea (geometry Data Type)
ms.assetid: a7dd6083-c649-4ac3-885d-1234e0db62f1
caps.latest.revision: "25"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9b7a3a75aab4df98ddb4e9b4e4149749c22e723b
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/19/2018
---
# <a name="starea-geometry-data-type"></a>STArea (tipo de datos geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Devuelve el área expuesta total de un **geometry** instancia.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
.STArea ( )  
```  
  
## <a name="return-types"></a>Tipos devueltos  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo de valor devuelto: **float**  
  
 Tipo de valor devuelto de CLR: **SqlDouble**  
  
## <a name="remarks"></a>Comentarios  
 `STArea()`Devuelve 0 si una **geometry** instancia contiene únicamente figuras 0 y 1-dimensiones, o si está vacía. `STArea()`Devuelve **NULL** si la **geometry** no se ha inicializado la instancia.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-computing-the-area-of-a-polygon-instance"></a>A. Calcular el área de una instancia de Polygon  
 En el ejemplo siguiente se crea un `Polygon``geometry` de instancia y se calcula el área del polígono.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0),(2 2, 2 1, 1 1, 1 2, 2 2))', 0);  
SELECT @g.STArea();  
```  
  
### <a name="b-computing-the-area-of-a-curvepolygon-instance"></a>B. Calcular el área de una instancia de CurvePolygon  
 En el siguiente ejemplo se calcula el área de una instancia de `CurvePolygon`.  
  
```
 DECLARE @g geometry;  
 SET @g = geometry::Parse('CURVEPOLYGON(CIRCULARSTRING(0 2, 2 0, 4 2, 4 2, 0 2))');  
 SELECT @g.STArea() AS Area;
 ```  
  
## <a name="see-also"></a>Vea también  
 [Métodos de OGC en instancias de geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
