---
title: "Suscripción, Comandos sin distribuir (Suscripción transaccional) | Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.monitor.subscription.performance.f1
ms.assetid: 5451561e-0ce3-4bb5-844a-88cd15b0b371
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0343859b26086b22f3d50d6469fbcdd57af04647
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="subscription-undistributed-commands-transactional-subscription"></a>Suscripción, Comandos sin distribuir (Suscripción transaccional)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  En la pestaña **Comandos sin distribuir** se muestra información sobre le número de comandos de la base de datos de distribución que no se han entregado al suscriptor seleccionado y el tiempo estimado para entregar esos comandos. Para información sobre cómo ver los comandos en la base de datos de distribución, vea [sp_replshowcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql.md).  
  
## <a name="options"></a>.  
 **Número de comandos en la base de datos de distribución en espera de ser aplicados al suscriptor**  
 Número de comandos de la base de datos de distribución que no se han entregado al suscriptor seleccionado. Un comando se compone de una instrucción de lenguaje de manipulación de datos (DML) de Transact-SQL o una instrucción de lenguaje de definición de datos (DDL).  
  
 **Tiempo estimado para aplicar estos comandos según las últimas operaciones**  
 Cantidad estimada de tiempo para entregar comandos al suscriptor. Si este valor es superior al tiempo necesario para generar y aplicar una instantánea en el suscriptor, considere la posibilidad de volver a reinicializar el suscriptor. Para obtener más información, vea [Reinicializar suscripciones](../../relational-databases/replication/reinitialize-subscriptions.md).  
  
## <a name="see-also"></a>Ver también  
 [Iniciar el Monitor de replicación](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Supervisar el rendimiento con el Monitor de replicación](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md)   
 [Supervisar la replicación](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
