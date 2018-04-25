---
title: Filter (tipo de datos geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- Filter
- Filter_TSQL
- Filter (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- Filter method
ms.assetid: 3d629a39-157e-4159-a3ca-a3c2e0ed4160
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7067fbff6824e4ddfec8cb7c7c111fc7a8f902d6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="filter-geometry-data-type"></a>Filter (tipo de datos Geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Método que proporciona una forma rápida de intersección solo para índices con la que se puede determinar si una instancia de **geometry** forma intersección con otra instancia de **geometry**, siempre y cuando haya un índice disponible.
  
Devuelve 1 si una instancia de **geometry** puede formar intersección con otra instancia de **geometry**. Este método puede generar un resultado falso positivo, y el resultado exacto puede depender del plan. Devuelve el valor 0 preciso (respuesta verdadera negativa) si no se encuentra ninguna intersección de las instancias de **geometry**.
  
En los casos en los que no haya ningún índice disponible o que no se use, el método devolverá los mismos valores que **STIntersects()** cuando se llama con los mismos parámetros.
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
.Filter ( other_geometry )  
```  
  
## <a name="arguments"></a>Argumentos  
 *other_geometry*  
 Es otra instancia de **geometry** con la que se compara la instancia en la que se invoca Filter().  
  
## <a name="return-types"></a>Tipos devueltos  
 Tipo de valor devuelto de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **bit**  
  
 Tipo de valor devuelto de CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Notas  
 Este método no es determinista y no es preciso.  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se usa `Filter()` para determinar si dos instancias de `geometry` forman intersección.  
  
```  
CREATE TABLE sample (id int primary key, g geometry);  
GO  
INSERT INTO sample VALUES  
   (0, geometry::Point(0, 0, 0)),  
   (1, geometry::Point(0, 1, 0)),  
   (2, geometry::Point(0, 2, 0)),  
   (3, geometry::Point(0, 3, 0)),  
   (4, geometry::Point(0, 4, 0));  
  
CREATE SPATIAL INDEX sample_idx ON sample(g)  
WITH (bounding_box = (-8000, -8000, 8000, 8000));  
GO  
SELECT id  
FROM sample   
WHERE g.Filter(geometry::Parse('POLYGON((-1 -1, 1 -1, 1 1, -1 1, -1 -1))')) = 1;  
```  
  
## <a name="see-also"></a>Ver también  
 [Métodos extendidos en instancias de geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)   
 [STIntersects &#40;tipo de datos geometry&#41;](../../t-sql/spatial-geometry/stintersects-geometry-data-type.md)  
  
  

