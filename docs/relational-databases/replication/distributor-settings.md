---
title: "Configuración del distribuidor | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.monitor.DistributorSettings.f1
helpviewer_keywords: Distributor Settings dialog box
ms.assetid: 8276a521-bdd1-4783-bdb6-7ab43499c0ca
caps.latest.revision: "10"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3dfd2c4bad135aaf87e9a9ce34c07dd1facb0f7d
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="distributor-settings"></a>Configuración del distribuidor
  El cuadro de diálogo **Configuración del distribuidor** le permite cambiar la configuración de los distribuidores que se han agregado al panel izquierdo del Monitor de replicación.  
  
## <a name="options"></a>Opciones  
 **Conectar automáticamente cuando se inicia el Monitor de replicación**  
 Seleccione esta opción para permitir que el Monitor de replicación se conecte al distribuidor y recupere información de estado.  
  
 **Conexión**  
 Haga clic aquí para mostrar el cuadro de diálogo **Conectar con el servidor** . Esto le permite ver y cambiar las propiedades de conexión y las credenciales que el Monitor de replicación utiliza para conectarse al distribuidor.  
  
 **Actualizar automáticamente el estado de este distribuidor y sus publicaciones**  
 Seleccione esta opción para permitir que el Monitor de replicación actualice automáticamente el estado del distribuidor. Si esta opción está seleccionada, el Monitor de replicación sondea al distribuidor para obtener información de estado basada en el intervalo de sondeo establecido por la opción **Frecuencia de actualización** . Para obtener más información sobre la actualización en el Monitor de replicación, vea [Caching, Refresh, and Replication Monitor Performance](../../relational-databases/replication/monitor/caching-refresh-and-replication-monitor-performance.md).  
  
 **Frecuencia de actualización**  
 Escriba un valor (en segundos) para especificar la frecuencia con la que el Monitor de replicación debe sondear el distribuidor en búsqueda de información de estado. Los valores menores producen sondeos más frecuentes. Esto puede afectar al rendimiento del distribuidor si está supervisando muchos publicadores. Se recomienda probar el sistema para determinar un valor adecuado. El valor **Frecuencia de actualización** también se utiliza si se selecciona **Actualizar automáticamente** en cualquiera de las ventanas de detalle del Monitor de replicación.  
  
 **Mostrar todos los publicadores de este distribuidor en el siguiente grupo**  
 Seleccione un grupo de publicadores de la lista. El publicador se muestra en este grupo en el panel izquierdo. Los grupos proporcionan una forma de organizar los publicadores y no afectan al funcionamiento de la replicación.  
  
 **Nuevo grupo**  
 Haga clic aquí para crear un nuevo grupo de publicadores. Un grupo de publicadores proporciona una forma cómoda de organizar publicadores dentro del Monitor de replicación. Los grupos no afectan a la replicación de datos ni a la relación entre los servidores de una topología de replicación.  
  
## <a name="see-also"></a>Vea también  
 [Iniciar el Monitor de replicación](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Supervisar la replicación](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
