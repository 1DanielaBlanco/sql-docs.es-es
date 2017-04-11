---
title: "Almacenamiento en cach&#233;, actualizaci&#243;n y rendimiento del Monitor de replicaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "supervisar rendimiento [replicación de SQL Server], Monitor de replicación"
  - "caché [SQL Server], replicación"
  - "Monitor de replicación, almacenar en caché"
  - "actualizar datos"
  - "Monitor de replicación, actualizar"
ms.assetid: a2d8b666-ed41-4f86-b2b8-c8e118416ab7
caps.latest.revision: 12
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 12
---
# Almacenamiento en cach&#233;, actualizaci&#243;n y rendimiento del Monitor de replicaci&#243;n
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] está diseñado para supervisar de manera eficaz un gran número de equipos en un sistema de producción. Las consultas que utiliza el Monitor de replicación para realizar cálculos y recopilar datos se almacenan en caché y se actualizan periódicamente. El almacenamiento en caché reduce el número de consultas y cálculos necesarios para ver diferentes páginas en el Monitor de replicación, y permite escalar la supervisión para varios usuarios.  
  
 Un trabajo del Agente [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , el **Actualizador de supervisión de replicación para distribución**, controla la actualización de la caché. El trabajo se ejecuta continuamente, pero la programación de actualización de la caché se basa en esperar determinado tiempo después de la actualización anterior:  
  
-   Si hay cambios en el historial del agente desde que se creó la caché por última vez, el tiempo de espera es el menor de los siguientes: 4 segundos o el tiempo necesario para crear la caché anterior.  
  
-   Si no hay cambios en el historial del agente desde que se creó la caché por última vez (aunque haya habido otros cambios), el tiempo de espera es el mayor de los siguientes: 30 segundos o el tiempo necesario para crear la caché anterior.  
  
## Actualizar la interfaz de usuario del Monitor de replicación  
 La interfaz de usuario del Monitor de replicación se puede actualizar de varias formas:  
  
-   La ventana principal del Monitor de replicación (y todas sus pestañas) se actualiza automáticamente, de manera predeterminada, cada cinco segundos. Las actualizaciones automáticas no obligan a actualizar la caché; la interfaz de usuario muestra la versión más reciente de los datos de la caché. Puede personalizar la velocidad de actualización utilizada para todas las ventanas asociadas con un publicador si modifica la configuración de éste. También puede deshabilitar las actualizaciones automáticas para un publicador.  
  
-   Las ventanas de detalles que se abren desde el Monitor de replicación no se actualizan automáticamente de manera predeterminada, con excepción de las ventanas relacionadas con las suscripciones de mezcla que se están sincronizando. Si especifica que se actualicen automáticamente las ventanas de detalles, se actualizarán con la misma programación que la ventana principal del Monitor de replicación.  
  
-   Todas las ventanas se pueden actualizar manualmente presionando F5 o haciendo clic en un nodo en el árbol del Monitor de replicación y haga clic en **actualizar**. La actualización manual fuerza una actualización de la caché.  
  
 Para obtener más información, consulte [Actualizar datos en el Monitor de replicación](../../../relational-databases/replication/monitor/refresh-data-in-replication-monitor.md).  
  
## Consideraciones de rendimiento  
 A pesar de que el Monitor de replicación está diseñado para ejecutarse de forma eficaz, debe tener en cuenta los siguientes aspectos:  
  
-   Si tiene un gran número de publicaciones o suscripciones, configure una programación de actualización automática menos frecuente para la interfaz de usuario.  
  
-   Evite ejecutar simultáneamente varias instancias del Monitor de replicación.  
  
-   Evite registrar un gran número de distribuidores y configurar el Monitor de replicación para que se conecte automáticamente a todos ellos.  
  
## Vea también  
 [Ejecutar trabajos de mantenimiento de replicación & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/administration/run-replication-maintenance-jobs-sql-server-management-studio.md)   
 [Supervisar la replicación](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  