---
title: EnvelopeAggregate (tipo de datos geography) | Microsoft Docs
ms.custom: 
ms.date: 07/30/2017
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
- EnvelopeAggregate_TSQL
- EnvelopeAggregate
dev_langs:
- TSQL
helpviewer_keywords:
- EnvelopeAggregate method (geography)
ms.assetid: 4947797f-edb8-490f-beca-37df9ec06954
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 62e288175b4c8f6f33e3996046fa24ffccaa8b2c
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="envelopeaggregate-geography-data-type"></a>EnvelopeAggregate (tipo de datos Geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Devuelve un objeto de enlace para un conjunto determinado de objetos **geography**. El objeto **geography** resultante contiene varios segmentos de arco circular.
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
EnvelopeAggregate ( geography_operand )  
```  
  
## <a name="arguments"></a>Argumentos  
 *geography_operand*  
 Es una columna de tabla de tipo **geography** que contiene el conjunto de objetos **geography** en el que se realiza una operación EnvelopeAggregate.  
  
## <a name="return-types"></a>Tipos devueltos  
 Tipo de valor devuelto de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geography**  
  
## <a name="remarks"></a>Notas  
 Se devuelve un objeto **FullGlobe** cuando el objeto de límite resultante es mayor que un hemisferio. Este método no es preciso.  
  
 El método devuelve **null** si la entrada tiene SRID diferentes. Vea [Identificadores de referencia espacial &#40;SRID&#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).  
  
 El método omite las entradas **null**.  
  
> [!NOTE]  
>  El método devuelve **null** si todos los valores introducidos son **null**.  
  
## <a name="examples"></a>Ejemplos  
 En el siguiente ejemplo se realiza una operación `EnvelopeAggregate` en un conjunto de puntos de ubicación de tipo **geography** de una ciudad.  
  
 ```
 USE AdventureWorks2012  
 GO  
 SELECT City,  
 geography::EnvelopeAggregate(SpatialLocation) AS SpatialLocation  
 FROM Person.Address  
 WHERE PostalCode LIKE('981%')  
 GROUP BY City;
 ```  
  
## <a name="see-also"></a>Ver también  
 [Métodos de geografía estáticos extendidos](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  
