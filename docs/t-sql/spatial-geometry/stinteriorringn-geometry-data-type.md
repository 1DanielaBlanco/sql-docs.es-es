---
title: STInteriorRingN (tipo de datos geometry) | Documentos de Microsoft
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STInteriorRingN_TSQL
- STInteriorRingN (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STInteriorRingN (geometry Data Type)
ms.assetid: 47310f9f-2cdb-41e0-a6da-7c3cfbf139ac
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a973ba1a1f3092c6a973ce4db0b5188615075922
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="stinteriorringn-geometry-data-type"></a>STInteriorRingN (tipo de datos geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Devuelve el anillo interior especificado de un **Polygongeometry** instancia.
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
.STInteriorRingN ( expression )  
```  
  
## <a name="arguments"></a>Argumentos  
 *expression*  
 Es un **int** expresión entre 1 y el número de anillos interiores de la **geometry** instancia.  
  
## <a name="return-types"></a>Tipos devueltos  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo de valor devuelto: **geometry**  
  
 Tipo de valor devuelto de CLR: **SqlGeometry**  
  
 Abrir tipo Geospatial Consortium (OGC): **LineString**  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve **null** si la **geometry** instancia no es un polígono. Este método también producirá un **ArgumentOutOfRangeException** si la expresión es mayor que el número de anillos. Se puede devolver el número de anillos usando `STNumInteriorRing``()`.  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se crea un `Polygon` instancia y se utiliza `STInteriorRingN()` para devolver el anillo interior del polígono como un **LineString**.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0),(2 2, 2 1, 1 1, 1 2, 2 2))', 0);  
SELECT @g.STInteriorRingN(1).ToString();  
```  
  
## <a name="see-also"></a>Vea también  
 [Métodos de OGC en instancias de Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  


