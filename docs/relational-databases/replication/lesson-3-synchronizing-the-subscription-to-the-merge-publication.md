---
title: "Lección 3: Sincronización de la suscripción con la publicación de combinación | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
helpviewer_keywords: replication [SQL Server], tutorials
ms.assetid: 49008384-2c55-4080-a890-9bceb40e4d6d
caps.latest.revision: "14"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0c0e328499c4ed59f55ee29fa57261da898750a8
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="lesson-3-synchronizing-the-subscription-to-the-merge-publication"></a>Lección 3: Sincronizar la suscripción con la publicación de combinación
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] En esta lección iniciará el Agente de mezcla para inicializar la suscripción con [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. También utilizará este procedimiento para sincronizar con el publicador. Esta lección requiere que haya completado la lección anterior, [Lección 2: Crear una suscripción a la publicación de mezcla](../../relational-databases/replication/lesson-2-creating-a-subscription-to-the-merge-publication.md).  
  
### <a name="to-start-synchronization-and-initialize-the-subscription"></a>Para iniciar la sincronización e inicializar la suscripción  
  
1.  Conéctese al suscriptor en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expanda el nodo del servidor y luego la carpeta **Replicación** .  
  
2.  En la carpeta **Suscripciones locales** , haga clic con el botón derecho en la suscripción de la base de datos **SalesOrdersReplica** y, después, haga clic en **Ver estado de sincronización**.  
  
3.  Haga clic en **Inicio** para inicializar la suscripción.  
  
## <a name="next-steps"></a>Pasos siguientes  
Ha ejecutado correctamente el Agente de mezcla para iniciar la sincronización e inicializar la suscripción. También puede insertar, actualizar o eliminar datos en las tablas **SalesOrderHeader** o **SalesOrderDetail** en el publicador o en el suscriptor, repetir este procedimiento cuando exista conectividad de red para sincronizar datos entre el publicador y el suscriptor y, después, consultar las tablas **SalesOrderHeader** o **SalesOrderDetail** en el otro servidor para ver los cambios replicados.  
  
Con esto finaliza el tutorial Replicar datos con clientes móviles. Para obtener un tutorial similar que usa la replicación transaccional, consulte [Tutorial: Replicar datos entre servidores conectados de forma continua](../../relational-databases/replication/tutorial-replicating-data-between-continuously-connected-servers.md).  
  
## <a name="see-also"></a>Vea también  
[Inicializar una suscripción con una instantánea](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
[Sincronizar datos](../../relational-databases/replication/synchronize-data.md)  
[Sincronizar una suscripción de extracción](../../relational-databases/replication/synchronize-a-pull-subscription.md)  
  
  
  
