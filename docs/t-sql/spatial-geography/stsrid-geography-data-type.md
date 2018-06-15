---
title: STSrid (tipo de datos geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STSrid (geography Data Type)
- STSrid_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STSrid method
ms.assetid: 6b04f5a7-2e69-4d34-901e-b61ba6ca9c14
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0b1a83b42a1812077f146cc4ea040934e2934daf
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "33061222"
---
# <a name="stsrid-geography-data-type"></a>STSrid (tipo de datos geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  **STSrid** es un entero que representa el identificador de referencia espacial (SRID) de la instancia.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
.STSrid  
```  
  
## <a name="return-types"></a>Tipos devueltos  
 Tipo de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **int**  
  
 Tipo de CLR: **SqlInt32**  
  
## <a name="remarks"></a>Notas  
 Esta propiedad se puede modificar.  
  
## <a name="examples"></a>Ejemplos  
 En el primer ejemplo se crea una instancia de `geography` con el valor SRID 4326 (WGS84) y se usa `STSrid` para confirmar dicho SRID.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STSrid;  
```  
  
 El segundo ejemplo usa `STSrid` para cambiar el valor SRID de la instancia a 4267 (NAD27) y, a continuación, confirma la modificación de dicho valor.  
  
```  
SET @g.STSrid = 4267;  
SELECT @g.STSrid;  
```  
  
## <a name="see-also"></a>Ver también  
 [Métodos de OGC en instancias de geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)   
 [Identificadores de referencia espacial &#40;SRID&#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md)  
  
  
