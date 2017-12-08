---
title: "Ver información y realizar tareas para un publicador (Monitor de replicación) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Publishers [SQL Server replication], Replication Monitor tasks
- viewing Publisher information
- Publishers [SQL Server replication], viewing information
ms.assetid: 1e777e95-377a-4de3-b965-867464aadaaf
caps.latest.revision: "37"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ad1d0890185e7e9e8066885057742870f48b1acc
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="view-information-and-perform-tasks-for-a-publisher-replication-monitor"></a>Ver información y realizar tareas para un publicador (Monitor de replicación)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] El Monitor de replicación proporciona las siguientes pestañas que muestran información sobre el publicador seleccionado:  
  
-   **Publicaciones**  
  
     En esta pestaña se muestra información sobre todas las publicaciones en el publicador seleccionado.  
  
-   **Lista de supervisión de suscripciones**  
  
     En esta pestaña se muestra información acerca de las suscripciones de todas las publicaciones disponibles en el publicador seleccionado que tienen errores, advertencias o un rendimiento insuficiente. Esta pestaña no se muestra en los distribuidores que se ejecutan en versiones anteriores de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
-   Pestaña**Agentes**   
  
     Esta pestaña muestra información detallada sobre los agentes y trabajos utilizados por todos los tipos de replicación. La pestaña también le permite iniciar y detener cada agente y trabajo.  
  
 Para obtener más información acerca de las opciones de esta pestaña, haga clic en el panel derecho y , a continuación, haga clic en **Ayuda** en la barra de menús. Para obtener información sobre cómo iniciar el Monitor de replicación, vea [Iniciar el Monitor de replicación](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
### <a name="to-view-information-and-perform-tasks-for-a-publisher"></a>Para ver información y realizar tareas en un publicador  
  
1.  Expanda un grupo de publicador en el panel izquierdo y, a continuación, haga clic en un publicador.  
  
2.  Para ver información sobre todas las publicaciones, haga clic en la pestaña **Publicaciones** .  
  
3.  Para ver información acerca de las suscripciones, haga clic en la pestaña **Lista de supervisión de suscripciones** . En esta pestaña, también puede realizar tareas y tener acceso a información más detallada:  
  
    -   Para ver información detallada sobre el agente asociado a una suscripción, haga clic con el botón secundario en la suscripción y, a continuación, haga clic en **Ver detalles**.  
  
    -   Para ver las propiedades de una suscripción, haga clic con el botón secundario en la suscripción y, a continuación, haga clic en **Propiedades**.  
  
    -   Para sincronizar una suscripción de inserción, haga clic con el botón secundario en la suscripción y, a continuación, haga clic en **Iniciar sincronización**.  
  
    -   Para reinicializar una suscripción, haga clic con el botón secundario en la suscripción y, a continuación, haga clic en **Reinicializar suscripción**.  
  
4.  Para ver información sobre los agentes, haga clic en la pestaña **Agentes** . En esta pestaña, también puede realizar tareas y tener acceso a información más detallada:  
  
    -   Para ver información detallada sobre un agente (por ejemplo, mensajes informativos y mensajes de error), haga clic con el botón secundario en el agente y, a continuación, haga clic en **Ver detalles**.  
  
    -   Para ver información detallada del trabajo que ejecuta el agente (como la programación, los detalles de los pasos del trabajo, etc.), haga clic con el botón secundario en el agente y, a continuación, haga clic en **Propiedades**.  
  
    -   Para administrar perfiles para el agente, haga clic con el botón secundario en el agente y, a continuación, haga clic en **Perfil del agente**. Para más información, vea [Trabajar con perfiles del Agente de replicación](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md).  
  
    -   Para iniciar un agente que no se está ejecutando, haga clic con el botón secundario en el agente y, a continuación, haga clic en **Iniciar agente**.  
  
    -   Para detener un agente que se está ejecutando, haga clic con el botón secundario en el agente y, a continuación, haga clic en **Detener agente**.  
  
## <a name="see-also"></a>Vea también  
 [Ver y modificar las propiedades del distribuidor y del publicador](../../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Supervisar la replicación](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
