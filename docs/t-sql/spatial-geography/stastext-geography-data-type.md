---
title: STAsText (tipo de datos geography) | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STAsText (geography Data Type)
- STAsText_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STAsText method
ms.assetid: d3d2635d-ca6c-4205-9d6c-eb939ee314fd
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4f29024f7ac82979771fc897a9efc6860af08a9a
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="stastext-geography-data-type"></a>STAsText (tipo de datos geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Devuelve la representación de Open Geospatial Consortium (OGC) Well-Known Text (WKT) de un **geography** instancia. Este texto no contendrá ningún valor Z (elevación) ni M (medida) perteneciente a la instancia.  
  
 Esto **geography** admite el método de tipo de datos **FullGlobe** instancias o instancias espaciales mayores que un hemisferio.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
.STAsText ( )  
```  
  
## <a name="return-types"></a>Tipos devueltos  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo de valor devuelto: **nvarchar (max)**  
  
 Tipo de valor devuelto de CLR: **SqlChars**  
  
## <a name="remarks"></a>Comentarios  
 El tipo OGC de una **geography** instancia se puede determinar invocando [STGeometryType()](../../t-sql/spatial-geography/stgeometrytype-geography-data-type.md).  
  
 En [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], el conjunto de resultados posibles devuelto en el servidor se ha ampliado a **FullGlobe** instancias.  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se utiliza `STAsText()` para crear un `LineString``geography` de la instancia de (-122.360, 47.656) a (-122.343, 47.656) del texto. A continuación, devuelve el resultado en forma de texto.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STAsText();  
```  
  
## <a name="see-also"></a>Vea también  
 [Métodos de OGC en instancias de Geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  

