---
title: Filtrar eventos basándose en la hora de inicio del evento (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: sql-server-profiler
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- event start times [SQL Server]
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: e965579e-d006-41a3-89ec-cfd5398c67d2
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cfd8b7593b4e43613483a6ce91cf279ade6b91bc
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="filter-events-based-on-the-event-start-time-sql-server-profiler"></a>Filtrar eventos basándose en la hora de inicio del evento (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] En este tema se describe el modo de filtrar eventos de seguimiento basándose en la hora de inicio del evento mediante [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-filter-an-event-based-on-the-event-start-time"></a>Para filtrar un evento en función de la hora de inicio del evento  
  
1.  En el menú **Archivo** , haga clic en **Nuevo seguimiento**y conéctese a una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Aparecerá el cuadro de diálogo **Propiedades de seguimiento**.  
  
    > [!NOTE]  
    >  Si se selecciona **Iniciar el seguimiento inmediatamente tras realizar la conexión**, el cuadro de diálogo **Propiedades de seguimiento**no aparecerá y, en su lugar, se iniciará el seguimiento. Para desactivar esta configuración, en el menú **Herramientas**, haga clic en **Opciones**y desactive la casilla **Iniciar el seguimiento inmediatamente tras realizar la conexión** .  
  
2.  En el cuadro **Nombre de seguimiento** , escriba un nombre para el seguimiento.  
  
3.  En el cuadro **Use the template**(Usar la plantilla), seleccione una plantilla de seguimiento.  
  
4.  Opcionalmente, especifique un destino para los resultados del seguimiento.  
  
5.  En el menú **Selección de eventos**, haga clic en el encabezado de columna **StartTime** . También puede hacer clic con el botón derecho en el encabezado de la columna y hacer clic en **Editar filtro de columna** para abrir el cuadro de diálogo **Editar filtro** .  
  
6.  Expanda **Mayor que** o **Menor que**y, a continuación, especifique un valor **datetime** en el campo que aparece debajo del operador de comparación.  
  
## <a name="see-also"></a>Ver también  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
