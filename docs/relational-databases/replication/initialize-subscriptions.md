---
title: Inicializar suscripciones | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.rep.newsubwizard.initializesubscriptions.f1
ms.assetid: 7b170e4e-470d-4828-a9ed-7435b0b03514
caps.latest.revision: 24
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c688ea2bd6345d6e57425e5d99d3068838d237bd
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="initialize-subscriptions"></a>Inicializar suscripciones
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Deberá inicializar los suscriptores antes de que puedan comenzar a recibir datos replicados. No se requiere un conjunto de datos inicial, pero el suscriptor deberá poseer al menos el esquema de cada objeto replicado y todas las tablas de metadatos y los procedimientos necesarios para la replicación.  
  
## <a name="options"></a>Opciones  
 **Propiedades de la suscripción**  
 Active la casilla de la columna **Inicializar** para cada suscriptor que necesite un conjunto de datos inicial. Si desactiva la casilla, solo se inicializarán los procedimientos y metadatos de replicación. Para más información, vea [Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md) (Inicializar una suscripción transaccional sin una instantánea).  
  
 Seleccione **Inmediatamente** en la columna **Inicializar cuando** del cuadro de lista desplegable para que el Agente de mezcla o el Agente de distribución transfieran los archivos de instantáneas al suscriptor una vez finalizado el asistente. Seleccione **En la primera sincronización** para que el agente transfiera los archivos la próxima vez que esté programado para ejecutarse. La opción **Inmediatamente** no está disponible para suscripciones de extracción a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]. El Agente de mezcla y el Agente de distribución no se ejecutarán con instancias de [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], por lo que deberá inicializar la suscripción de otra forma.  
  
> [!NOTE]  
>  El asistente podría solicitar una conexión al distribuidor para iniciar un trabajo adecuado del Agente de distribución o el Agente de mezcla.  
  
## <a name="see-also"></a>Ver también  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Inicializar una suscripción](../../relational-databases/replication/initialize-a-subscription.md)   
 [Suscribirse a publicaciones](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
