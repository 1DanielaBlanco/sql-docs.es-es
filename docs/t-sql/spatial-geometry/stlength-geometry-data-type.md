---
title: STLength (tipo de datos geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STLength_TSQL
- STLength (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STLength (geometry Data Type)
ms.assetid: e34dc620-2a65-4248-b099-fff91830ab98
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c7b146d353ee18f9e1156a08c0ae6cee0aac7ab3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "33063212"
---
# <a name="stlength-geometry-data-type"></a>STLength (tipo de datos geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Devuelve la longitud total de los elementos de una instancia de **geometry**.
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
.STLength ( )  
```  
  
## <a name="return-types"></a>Tipos devueltos  
 Tipo de valor devuelto de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **float**  
  
 Tipo de valor devuelto de CLR: **SqlDouble**  
  
## <a name="remarks"></a>Notas  
 Si se trata de una instancia de **geometry** cerrada, su longitud se calcula como la longitud total alrededor de la instancia; la longitud de cualquier polígono es su perímetro y la longitud de un punto es 0. La longitud de cualquier tipo **geometrycollection** es la suma de las longitudes de las instancias de **geometry** que contiene.  
  
 STLength() funciona con LineString válidos y no válidos. Si un LineString no es válido normalmente se debe a la superposición de segmentos, lo cual se puede deber a anomalías como seguimientos de GPS inexactos. STLength() no quita segmentos superpuestos o no válidos. Incluye los segmentos superpuestos y no válidos en el valor de longitud que devuelve. El método MakeValid() puede quitar segmentos superpuestos de un LineString.  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se crea una instancia de `LineString` y se usa `STLength()` para averiguar la longitud de dicha instancia.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STLength();  
```  
  
## <a name="see-also"></a>Ver también  
 [Métodos de OGC en instancias de geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

