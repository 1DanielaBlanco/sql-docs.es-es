---
title: Punto (tipo de datos geometry) | Documentos de Microsoft
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
- Point
- Point_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Point (geometry Data Type)
ms.assetid: 7a2e593a-4d4c-4214-b0c5-02d1ac46bc66
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e153b3bbaf18e6c4b69171e56f2fdae6965396a7
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="point-geometry-data-type"></a>Point (tipo de datos geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Construye un **geometry** instancia que representa un **punto** instancia a partir de sus valores X e Y y un SRID.
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Point ( X, Y, SRID )  
```  
  
## <a name="arguments"></a>Argumentos  
 *X*  
 Es un **float** expresión que representa la coordenada X de la **punto** que se está generando.  
  
 *Y*  
 Es un **float** expresión que representa la coordenada Y de la **punto** que se está generando.  
  
 *SRID*  
 Es un **int** expresión que representa el espaciales identificador de referencia (SRID) de la **geometry** instancia que se va a devolver.  
  
## <a name="return-types"></a>Tipos devueltos  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo de valor devuelto: **geometry**  
  
 Tipo de valor devuelto de CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se usa `Point()` para crear una instancia de `geometry`.  
  
```  
DECLARE @g geometry;   
SET @g = geometry::Point(1, 10, 0);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Vea también  
 [Métodos de geometría estáticos ampliados](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  


