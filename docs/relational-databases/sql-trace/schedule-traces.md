---
title: Programar seguimientos | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-trace
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- filters [SQL Server], events
- traces [SQL Server]
- traces [SQL Server], stopping
- events [SQL Server], filters
- scheduling traces [SQL Server]
- traces [SQL Server], scheduling
- stopping traces
ms.assetid: 620b79db-924b-4502-8af3-39efcfca245d
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6693df4ddf0afbca69ad46f50bbaa49877be4450
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/18/2018
---
# <a name="schedule-traces"></a>Programar seguimientos
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] En Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hay dos formas de programar seguimientos. Puede hacer lo siguiente:  
  
-   Habilitar una hora de detención de seguimiento.  
  
-   Utilizar el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para programar una seguimiento.  
  
## <a name="specifying-a-stop-time"></a>Especificar una hora de detención  
 Puede especificar una hora de detención de seguimiento si utiliza procedimientos almacenados de [!INCLUDE[tsql](../../includes/tsql-md.md)] o si utiliza el [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. La hora de detención debe establecerse al configurar originalmente la seguimiento.  
  
## <a name="scheduling-traces-by-using-sql-server-agent"></a>Programar seguimientos mediante el Agente SQL Server  
 La mejor forma de programar seguimientos consiste en usar el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para iniciar el seguimiento y, después, especificar una hora de detención de seguimiento mediante el procedimiento almacenado de [!INCLUDE[tsql](../../includes/tsql-md.md)] **sp_trace_setstatus**o el [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
 **Para establecer un filtro de hora de finalización para una seguimiento**  
  
 [Filtrar eventos basándose en la hora de finalización del evento &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-based-on-the-event-end-time-sql-server-profiler.md)  
  
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)  
  
## <a name="see-also"></a>Ver también  
 [Tareas administrativas automatizadas &#40;Agente SQL Server&#41;](http://msdn.microsoft.com/library/541ee5ac-2c9f-4b74-b4f0-13b7bd5920b0)  
  
  
