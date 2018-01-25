---
title: AsGml (tipo de datos geography) | Documentos de Microsoft
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
- AsGml_(geography_Data_Type)_TSQL
- AsGml
- AsGml_TSQL
- AsGml (geography Data Type)
dev_langs: TSQL
helpviewer_keywords: AsGml method
ms.assetid: 67795c64-d8d3-48dc-93ef-3c8a9274deb6
caps.latest.revision: "14"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f4fe914c8f6f9d6a7547e36910be78878a66f19b
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
#  <a name="asgml---geography-data-type"></a>AsGml - tipo de datos geography
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Devuelve la representación de lenguaje de marcado de geografía (GML) de un **geography** instancia.  
  
 Para obtener más información sobre el lenguaje de marcado de geografía, vea la especificación de Open Geospatial Consortium: [OGC Specifications, Geography Markup Language.](http://go.microsoft.com/fwlink/?LinkId=93629)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
.AsGml ( )  
```  
  
## <a name="return-types"></a>Tipos devueltos  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo de valor devuelto: **xml**  
  
 Tipo de valor devuelto de CLR: **SqlXml**  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se crea una instancia de `LineString` y se usa `AsGML()` para devolver la descripción de GML de dicha instancia.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.AsGml();  
```  
  
 Este método devuelve la descripción como instancia de `LineString`.  
  
```  
<LineString xmlns="http://www.opengis.net/gml"><posList>47.656 -122.36 47.656 -122.343</posList></LineString>  
```  
  
## <a name="see-also"></a>Vea también  
 [Métodos extendidos en instancias de geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
