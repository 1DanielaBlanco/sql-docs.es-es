---
title: STIntersection (tipo de datos geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STIntersection_TSQL
- STIntersection (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STIntersection (geometry Data Type)
ms.assetid: 354843f5-cc14-478c-974a-04f363f9530f
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f556697457ba8baa649458f7a7c46b02e4682d4c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47759673"
---
# <a name="stintersection-geometry-data-type"></a>STIntersection (tipo de datos geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Devuelve un objeto que representa los puntos donde una instancia de **geometry** forma intersección con otra instancia de **geometry**.
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
.STIntersection ( other_geometry )  
```  
  
## <a name="arguments"></a>Argumentos  
 *other_geometry*  
 Es otra instancia de **geometry** usada para compararla con la instancia en la que se invoca `STIntersection()`, con objeto de determinar sus puntos de intersección.  
  
## <a name="return-types"></a>Tipos devueltos  
 Tipo de valor devuelto de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geometry**  
  
 Tipo de valor devuelto de CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Notas  
 `STIntersection()` siempre devuelve NULL si no coinciden los identificadores de referencia espacial (SRID) de las instancias de **geometry**. El resultado puede contener segmentos de arco circulares solo si las instancias de entrada los contienen.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-using-stintersection-on-polygon-instances"></a>A. Usar STIntersection () en instancias de Polygon  
 En el ejemplo siguiente se utiliza `STIntersection()` para calcular la intersección de dos polígonos.  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 0 2, 2 2, 2 0, 0 0))', 0);  
SET @h = geometry::STGeomFromText('POLYGON((1 1, 3 1, 3 3, 1 3, 1 1))', 0);  
SELECT @g.STIntersection(@h).ToString();  
```  
  
### <a name="b-using-stintersection-with-curvepolygon-instance"></a>B. Usar STIntersection() con una instancia de CurvePolygon  
 En el siguiente ejemplo se devuelve una instancia que contiene un segmento de arco circular.  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON (CIRCULARSTRING (0 -4, 4 0, 0 4, -4 0, 0 -4))';  
 DECLARE @h geometry = 'POLYGON ((1 -1, 5 -1, 5 3, 1 3, 1 -1))';  
 SELECT @h.STIntersection(@g).ToString();
 ```  
  
## <a name="see-also"></a>Ver también  
 [Métodos de OGC en instancias de geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

