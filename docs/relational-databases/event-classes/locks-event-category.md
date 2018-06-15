---
title: Categoría de eventos Bloqueos | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Locks event category [SQL Server]
- SQL Server event classes, Locks event category
- event classes [SQL Server], Locks event category
- lock escalation [SQL Server], locks event category
ms.assetid: 27d6afa2-7dab-4fe7-a1ad-064b879dc654
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 6d0616573c2215005994a45ac2d45d156dd065fc
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2018
ms.locfileid: "34327546"
---
# <a name="locks-event-category"></a>Bloqueos (categoría de eventos)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Utilice las clase de evento de la categoría de eventos **Bloqueos** para supervisar la actividad de bloqueo en una instancia del [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Estas clases de evento pueden ayudarle a investigar los problemas de bloqueo provocados por varios usuarios que leen y modifican datos simultáneamente.  
  
 Puesto que el [!INCLUDE[ssDE](../../includes/ssde-md.md)] a menudo procesa varios bloqueos, la captura de las clases de eventos en **Bloqueos** durante un seguimiento puede incurrir en un aumento significativo de la carga y dar como resultado archivos o tablas de seguimiento muy grandes.  
  
## <a name="in-this-section"></a>En esta sección  
  
|Tema|Descripción|  
|-----------|-----------------|  
|[Deadlock Graph (clase de eventos)](../../relational-databases/event-classes/deadlock-graph-event-class.md)|Proporciona una descripción en XML de un interbloqueo.|  
|[Lock:Acquired (clase de eventos)](../../relational-databases/event-classes/lock-acquired-event-class.md)|Indica que se ha adquirido un bloqueo en un recurso, por ejemplo una fila de una tabla.|  
|[Lock:Cancel (clase de eventos)](../../relational-databases/event-classes/lock-cancel-event-class.md)|Realiza un seguimiento de las solicitudes de bloqueos que se cancelaron antes de adquirirse el bloqueo (por ejemplo, para impedir un interbloqueo).|  
|[Lock:Deadlock Chain (clase de eventos)](../../relational-databases/event-classes/lock-deadlock-chain-event-class.md)|Supervisa cuándo se producen condiciones de interbloqueo y a qué objetos afectan.|  
|[Lock:Deadlock (clase de eventos)](../../relational-databases/event-classes/lock-deadlock-event-class.md)|Realiza un seguimiento de cuándo una transacción ha solicitado un bloqueo en un recurso ya bloqueado por otra transacción, con el resultado de un interbloqueo.|  
|[Lock:Escalation (clase de eventos)](../../relational-databases/event-classes/lock-escalation-event-class.md)|Indica que un bloqueo específico se ha convertido en un bloqueo general.|  
|[Lock:Released (clase de eventos)](../../relational-databases/event-classes/lock-released-event-class.md)|Realiza un seguimiento de cuándo se libera un bloqueo.|  
|[Clase de eventos Lock:Timeout &#40;timeout &#62; 0&#41;](../../relational-databases/event-classes/lock-timeout-timeout-0-event-class.md)|Realiza un seguimiento de cuándo no se pueden completar solicitudes de bloqueo porque otra transacción tiene bloqueado el recurso solicitado. Este evento solo se produce en situaciones en las que el valor de tiempo de espera del bloqueo es superior a cero.|  
|[Lock:Timeout (clase de eventos)](../../relational-databases/event-classes/lock-timeout-event-class.md)|Realiza un seguimiento de cuándo no se pueden completar solicitudes de bloqueo porque otra transacción tiene bloqueado el recurso solicitado.|  
  
  
