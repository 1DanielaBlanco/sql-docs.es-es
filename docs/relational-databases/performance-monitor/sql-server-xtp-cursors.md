---
title: Cursores XTP de SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 84bf4654-3ef7-4d7f-a269-c8bb4ed4acad
caps.latest.revision: 6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0aee7c81b5074e0212617b880df2159b0fec4f5d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="sql-server-xtp-cursors"></a>Cursores SQL Server XTP
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  El objeto de rendimiento Cursores XTP de SQL Server contiene contadores relacionados con los cursores internos del motor OLTP en memoria. Los cursores son los bloques de creación de bajo nivel que usa el motor OLTP en memoria para procesar consultas de [!INCLUDE[tsql](../../includes/tsql-md.md)] . Por tanto, el usuario no tiene normalmente control directo sobre ellos.  
  
 En esta tabla se describen los contadores de **Cursores XTP** .  
  
|Contador|Description|  
|-------------|-----------------|  
|**Eliminaciones de cursor/s**|Número de eliminaciones de cursor (en promedio), por segundo.|  
|**Inserciones de cursor/s**|Número de inserciones de cursor (en promedio), por segundo.|  
|**Recorridos de cursor iniciados/s**|Número de recorridos de cursor iniciados (en promedio), por segundo.|  
|**Infracciones de restricciones UNIQUE de cursor/s**|Número de infracciones de restricciones UNIQUE (en promedio), por segundo.|  
|**Actualizaciones de cursor/s**|Número de actualizaciones de cursor (en promedio), por segundo.|  
|**Conflictos de escritura de cursor/s**|Número de conflictos de escritura contra escritura en la misma versión de fila (en promedio), por segundo.|  
|**Reintentos de recorrido de esquinas sucias/s (emitidos por el usuario)**|Número de reintentos de recorrido debido a conflictos de escritura durante los rastreos de esquinas sucias emitidos por un recorrido de tabla completo del usuario (en promedio), por segundo. Es un contador de nivel muy bajo, no está pensado para uso de los clientes.|  
|**Filas expiradas quitadas/s**|Número de filas expiradas quitadas mediante cursores (en promedio), por segundo.|  
|**Filas expiradas tocadas/s**|Número de filas expiradas tocadas mediante cursores (en promedio), por segundo.|  
|**Filas devueltas/s**|Número de filas devueltas mediante cursores (en promedio), por segundo.|  
|**Filas tocadas/s**|Número de filas tocadas mediante cursores (en promedio), por segundo.|  
|**Filas tocadas eliminadas provisionalmente/s**|Número de filas que van a expirar tocadas mediante cursores (en promedio), por segundo. Una fila va a expirar si la transacción que la eliminó permanece activa (es decir, no se confirma o anula).|  
  
## <a name="see-also"></a>Ver también  
 [Contadores de rendimiento de XTP &#40;OLTP en memoria&#41;](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)  
  
  
