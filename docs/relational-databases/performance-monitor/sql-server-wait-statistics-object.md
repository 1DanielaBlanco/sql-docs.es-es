---
title: Wait Statistics (objeto de SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
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
helpviewer_keywords:
- Wait Statistics object
- SQLServer:Wait Statistics
ms.assetid: cb7f917d-4291-4115-9b78-ee7692ebbb2d
caps.latest.revision: 15
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 344b5a8a7ec6d1719986c8700c04fbf8f94a0a31
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="sql-server-wait-statistics-object"></a>Wait Statistics (objeto de SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  El objeto de rendimiento de **SQLServer:Wait Statistics** contiene contadores de rendimiento que ofrecen información sobre el estado de la espera.  
  
 La tabla incluida a continuación enumera los contadores que contiene el objeto de Wait Statistics.  
  
|Contadores de Wait Statistics de SQL Server|Description|  
|-----------------------------------------|-----------------|  
|**Esperas de bloqueo**|Estadísticas para procesos que esperan en un bloqueo.|  
|**Esperas de búfer de registro**|Estadísticas para procesos que esperan que el búfer de registro esté disponible.|  
|**Esperas de escritura en registro**|Estadísticas para procesos que esperan que se escriba el búfer de registro.|  
|**Esperas de cola de concesión de memoria**|Estadísticas para procesos que esperan que una concesión de memoria esté disponible.|  
|**Esperas de E/S de red**|Estadísticas relacionadas con la espera en E/S de red.|  
|**Esperas de bloqueos temporales distintos de páginas**|Estadísticas relacionadas con bloqueos temporales distintos de páginas.|  
|**Esperas de bloqueos temporales de E/S de páginas**|Estadísticas relacionadas con bloqueos temporales de E/S de páginas.|  
|**Esperas de bloqueos temporales de páginas**|Estadísticas relacionadas con bloqueos temporales de páginas, no incluidos los bloqueos temporales de E/S.|  
|**Esperas de objetos de memoria seguros para subprocesos**|Estadísticas para procesos que esperan en asignadores de memoria seguros para subprocesos.|  
|**Esperas de propiedad de transacción**|Estadísticas relacionadas con procesos que sincronizan el acceso a la transacción.|  
|**Espera del objeto de trabajo**|Estadísticas relacionadas con procesos que esperan que el objeto de trabajo esté disponible.|  
|**Esperas de sincronización de área de trabajo**|Estadísticas relacionadas con procesos que sincronizan el acceso al área de trabajo.|  
  
 Cada contador del objeto contiene las instancias siguientes:  
  
|Elemento|Description|  
|----------|-----------------|  
|**Tiempo promedio de espera (ms)**|Tiempo promedio del tipo de espera seleccionado.|  
|**Tiempo de espera acumulado (ms) por segundo**|Tiempo de espera agregado por segundo para el tipo de espera seleccionado.|  
|**Espera en curso**|Número de procesos actualmente en espera en el tipo siguiente.|  
|**Esperas iniciadas por segundo**|Número de esperas iniciadas por segundo del tipo de espera seleccionado.|  
  
## <a name="see-also"></a>Ver también  
 [Supervisar el uso de recursos&#40;Monitor de sistema&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
