---
title: STNumCurves (tipo de datos geometry) | Documentos de Microsoft
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- STNumCurves method (geometry)
ms.assetid: 20c2fa0b-656b-4519-b34c-cc8f094290d4
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 718289c6785bec8f9bba15ccec76507ac2501f47
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="stnumcurves-geometry-data-type"></a>STNumCurves (tipo de datos geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Este método devuelve el número de curvas de una **geometry** instancia cuando la instancia es un tipo de datos espacial unidimensional. Los tipos de datos espaciales unidimensionales incluyen **LineString**, **CircularString**, y **CompoundCurve**. `STNumCurves`() funciona solo en tipos simples; no funciona con **geometry** colecciones como **MultiLineString**.
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
.STNumCurves()  
```  
  
## <a name="return-types"></a>Tipos devueltos  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo de valor devuelto: **geometry**  
  
 Tipo de valor devuelto de CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Comentarios  
 Unidimensional vacía **geometry** instancia devuelve 0. **NULL** se devuelve cuando la **geometry** instancia no es una instancia unidimensional o es una instancia no inicializada.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-using-stnumcurves-on-a-circularstring-instance"></a>A. Usar STNumCurves() en una instancia de CircularString  
 En el siguiente ejemplo se muestra cómo obtener el número de curvas de una instancia de `CircularString`:  
  
 `DECLARE @g geometry;`  
  
 `SET @g = geometry::Parse('CIRCULARSTRING(10 0, 0 10, -10 0, 0 -10, 10 0)');`  
  
 `SELECT @g.STNumCurves();`  
  
### <a name="b-using-stnumcurves-on-a-compoundcurve-instance"></a>B. Usar STNumCurves() en una instancia de CompoundCurve  
 En el siguiente ejemplo se utiliza `STNumCurves()` para devolver el número de curvas de una instancia de `CompoundCurve`.  
  
 `DECLARE @g geometry;`  
  
 `SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(10 0, 0 10, -10 0, 0 -10, 10 0))');`  
  
 `SELECT @g.STNumCurves();`  
  
## <a name="see-also"></a>Vea también  
 [Información general de los tipos de datos espaciales](../../relational-databases/spatial/spatial-data-types-overview.md)   
 [Métodos de OGC en instancias de Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  


