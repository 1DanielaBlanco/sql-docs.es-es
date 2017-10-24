---
title: STCurveToLine (tipo de datos geography) | Documentos de Microsoft
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
- STCurveToLine_TSQL
- STCurveToLine
dev_langs:
- TSQL
helpviewer_keywords:
- STCurveToLine method (geography)
ms.assetid: 2f863a85-6168-465a-b32f-bb5e3de58dee
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9d2ad93d8bc292ebb86233917dc3f934fbe57dca
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="stcurvetoline-geography-data-type"></a>STCurveToLine (tipo de datos geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Devuelve una aproximación poligonal de un **geography** instancia que contiene los segmentos de arco circular.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
.STCurveToLine()  
```  
  
## <a name="return-types"></a>Tipos devueltos  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo de valor devuelto: **geography**  
  
 Tipo de valor devuelto de CLR: **SqlGeography**  
  
## <a name="remarks"></a>Comentarios  
 Devuelve un **LineString** de instancia para una **CircularString** o **CompoundCurve** instancia.  
  
 Devuelve un **polígono** de instancia para una **CurvePolygon** instancia.  
  
 Devolver una copia de **geography** instancias que no contienen **CircularString**, **CompoundCurve**, o **CurvePolygon** instancias.  
  
 A diferencia de la especificación MM de SQL, este método no utiliza los valores de coordenada z para calcular la aproximación poligonal. Los valores de coordenada z presentes en la llamada a **geography** instancia se omiten.  
  
## <a name="examples"></a>Ejemplos  
 En el siguiente ejemplo se devuelve una instancia `LineString` que es una aproximación poligonal de una instancia `CircularString`:  
  
```
 DECLARE @g1 geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 DECLARE @g2 geography;  
 SET @g2 = @g1.STCurveToLine();  
 SELECT @g1.STNumPoints() AS G1, @g2.STNumPoints() AS G2;
 ```  
  
## <a name="see-also"></a>Vea también  
 [STLength &#40; tipo de datos geography &#41;](../../t-sql/spatial-geography/stlength-geography-data-type.md)   
 [STNumPoints &#40; tipo de datos geography &#41;](../../t-sql/spatial-geography/stnumpoints-geography-data-type.md)   
 [Información general de los tipos de datos espaciales](../../relational-databases/spatial/spatial-data-types-overview.md)  
  
  

