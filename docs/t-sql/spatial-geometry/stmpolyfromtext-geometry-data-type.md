---
title: STMPolyFromText (tipo de datos geometry) | Microsoft Docs
ms.custom: 
ms.date: 08/03/2017
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
- STMPolyFromText (geometry Data Type)
- STMPolyFromText_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STMPolyFromText (geometry Data Type)
ms.assetid: f087a61c-f063-4fb8-8f1c-251a2fed76a1
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9b4610481d315122b2d811ef30e65b1d30a1f4d5
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="stmpolyfromtext-geometry-data-type"></a>STMPolyFromText (tipo de datos geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Devuelve una instancia de **geometry** a partir de una representación Well-Known Text (WKT) de Open Geospatial Consortium (OGC), con los valores Z (elevación) y M (medida) pertenecientes a la instancia.
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
STMPolyFromText ( 'multipolygon_tagged_text' , SRID )  
```  
  
## <a name="arguments"></a>Argumentos  
 *multipolygon_tagged_text*  
 Es la representación WKT de la instancia de **geometryMultiPolygon** que se quiere devolver. *multipolygon_tagged_text* es una expresión **nvarchar(max)**.  
  
 *SRID*  
 Es una expresión de tipo **int** que representa el identificador de referencia espacial (SRID) de la instancia de **geometryMultiPolygon** que se quiere devolver.  
  
## <a name="return-types"></a>Tipos devueltos  
 Tipo de valor devuelto de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geometry**  
  
 Tipo de valor devuelto de CLR: **Sql Geometry**  
  
 Tipo OGC: **MultiPolygon**  
  
## <a name="remarks"></a>Notas  
 Este método produce una excepción **FormatException** si la entrada no tiene el formato correcto.  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se usa `STMPolyFromText()` para crear una instancia de `geometry`.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STMPolyFromText('MULTIPOLYGON (((5 5, 10 5, 10 10, 5 5)), ((10 10, 100 10, 200 200, 30 30, 10 10)))', 0);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Ver también  
 [Métodos de geometría estáticos de OGC](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  

