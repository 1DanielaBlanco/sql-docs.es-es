---
title: EnvelopeAngle (tipo de datos geography) | Documentos de Microsoft
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
- EnvelopeAngle
- EnvelopeAngle_TSQL
dev_langs: TSQL
helpviewer_keywords: EnvelopeAngle method
ms.assetid: 14a7ba15-168c-4b08-ba3d-951d73092ac7
caps.latest.revision: "19"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 41e560a4fa5ad869d126a1e594b57b96dc0f1558
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="envelopeangle-geography-data-type"></a>EnvelopeAngle (tipo de datos Geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Devuelve el ángulo máximo entre el punto devuelto por `EnvelopeCenter()` y un punto de la **geography** instancia en grados.  
  
 Esto **geography** admite el método de tipo de datos **FullGlobe** instancias o instancias espaciales mayores que un hemisferio.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
EnvelopeAngle( )  
```  
  
## <a name="return-types"></a>Tipos devueltos  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo de valor devuelto: **float**  
  
 Tipo de valor devuelto de CLR: **SqlDouble**  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve un punto en el **geography** instancia en grados. Cuando se usa con EnvelopeCenter(), `EnvelopeAngle()` devuelve un círculo de límite de un **geography** instancia.  
  
 En [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], este método se ha ampliado a **FullGlobe** instancias.  
  
 La limitación de hemisferio aplicada a `EnvelopeAngle()` en [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] se ha quitado. Sin embargo, en instancias con ángulos mayores que 90 grados, se devolverán 180 grados. `EnvelopeAngle()`no es preciso para **geography** instancias que abarcan más de un hemisferio.  
  
## <a name="examples"></a>Ejemplos  
  
```  
DECLARE @g geography = 'LINESTRING(-120 45, -120 0, -90 0)';   
SELECT @g.EnvelopeAngle();  
```  
  
## <a name="see-also"></a>Vea también  
 [Métodos extendidos en instancias de Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [EnvelopeCenter &#40; tipo de datos geography &#41;](../../t-sql/spatial-geography/envelopecenter-geography-data-type.md)  
  
  
