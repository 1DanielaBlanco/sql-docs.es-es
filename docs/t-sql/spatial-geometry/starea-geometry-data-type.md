---
title: STArea (tipo de datos geometry) | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STArea (geometry Data Type)
- STArea_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STArea (geometry Data Type)
ms.assetid: a7dd6083-c649-4ac3-885d-1234e0db62f1
caps.latest.revision: 25
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5ec0a874d0dc2dd8bb37ce7e04fe71cbea85f860
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="starea-geometry-data-type"></a>STArea (tipo de datos geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

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
 [Métodos de OGC en instancias de Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

