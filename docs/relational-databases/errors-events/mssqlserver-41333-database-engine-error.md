---
title: MSSQLSERVER_41333 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 41333 (Database Engine error)
ms.assetid: c3c3ae9a-1e4c-4de6-ba72-2f393375b053
caps.latest.revision: 7
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 72f5461f4e60b7e4c5cb53df75906d1aae0a07a5
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver41333"></a>MSSQLSERVER_41333
  
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Identificador del evento|41333|  
|Origen del evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|CROSS_CONTAINER_ISOLATION_FAILURE|  
|Texto del mensaje|Las transacciones siguientes deben tener acceso a las tablas optimizadas en memoria y a los procedimientos almacenados compilados de forma nativa con aislamiento de instantánea: las transacciones RepeatableRead, Serializable y las que tienen acceso a las tablas que no están optimizadas en memoria en el aislamiento RepeatableRead o Serializable.|  
  
## <a name="explanation"></a>Explicación  
Hay restricciones respecto al usuario de los niveles de aislamiento mayores entre las transacciones basadas en disco y las transacciones XTP.  
  
## <a name="user-action"></a>Acción del usuario  
No intente operaciones de aislamiento alto nivel de las tablas optimizadas en memoria (y procedimientos compilados de forma nativa) y las tablas basadas en disco.  
  
Para obtener más información, vea [OLTP en memoria &#40;optimización en memoria&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Vea también  
[OLTP en memoria &#40;optimización en memoria&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  

