---
title: ExecStatistics (objeto de SQL Server) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLServer:ExecStatistics
- ExecStatistics object
ms.assetid: 4f8557a8-345f-4622-a8a5-763a0388ad94
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 709d44983ef7010b36de6238ce99b2d20397017a
ms.contentlocale: es-es
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-execstatistics-object"></a>ExecStatistics (objeto de SQL Server)
  El objeto **SQLServer:ExecStatistics** de Microsoft SQL Server proporciona contadores para supervisar diversas ejecuciones.  
  
 En esta tabla se describen los contadores de **Exec Statistics** de SQL Server.  
  
|Contadores de Exec Statistics de SQL Server|Descripción|  
|-----------------------------------------|-----------------|  
|**Consulta distribuida**|Estadísticas relacionadas con la ejecución de consultas distribuidas.|  
|**Llamadas DTC**|Estadísticas relacionadas con la ejecución de llamadas DTC.|  
|**Procedimientos extendidos**|Estadísticas relacionadas con la ejecución de procedimientos extendidos.|  
|**Llamadas OLEDB**|Estadísticas relacionadas con la ejecución de llamadas OLEDB.|  
  
 Cada contador del objeto contiene las instancias siguientes:  
  
|Elemento|Descripción|  
|----------|-----------------|  
|**Tiempo medio de ejecución (ms)**|Tiempo medio de ejecución del tipo de ejecución seleccionado.|  
|**Tiempo de ejecución acumulado (ms) por segundo**|Tiempo de ejecución acumulado por segundo del tipo de ejecución seleccionado.|  
|**Ejecuciones en curso**|Número de ejecuciones en curso del tipo de ejecución seleccionado.|  
|**Ejecuciones iniciadas por segundo**|Número de ejecuciones iniciadas por segundo del tipo de ejecución seleccionado.|  
  
## <a name="see-also"></a>Vea también  
 [Supervisar el uso de recursos &#40;Monitor de sistema&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
