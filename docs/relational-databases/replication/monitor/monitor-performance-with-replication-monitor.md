---
title: "Supervisar el rendimiento con el Monitor de replicaci&#243;n | Microsoft Docs"
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
  - "Agente de registro del LOG, supervisar"
  - "Monitor de replicación, rendimiento"
  - "Agente de mezcla, supervisar"
  - "Agente de lectura de cola, supervisar"
  - "Agente de instantáneas, supervisar"
  - "Agente de distribución, supervisar"
  - "supervisar rendimiento [replicación de SQL Server]"
ms.assetid: f212397d-1bfd-496b-a246-668952891d09
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# Supervisar el rendimiento con el Monitor de replicaci&#243;n
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] le ofrece las siguientes posibilidades para supervisar el rendimiento de la replicación transaccional y de la replicación de mezcla:  
  
-   Establecer advertencias y umbrales  
  
-   Ver medidas de rendimiento  
  
-   Determinar la latencia con testigos de seguimiento (replicación transaccional)  
  
-   Ver estadísticas de sincronización detalladas (replicación de mezcla)  
  
-   Ver transacciones y tiempos de entrega (replicación transaccional)  
  
## Establecer advertencias y umbrales  
 El Monitor de replicación permite habilitar advertencias para una serie de condiciones de rendimiento. Al habilitar una advertencia, debe especificar un umbral. Cuando se alcance o supere dicho umbral, se muestra una advertencia en el **estado** columna para la suscripción y la publicación con los que sincronizará (a menos que se debe mostrar un problema con una prioridad más alta). Además de mostrar una advertencia en el Monitor de replicación, llegar a un umbral también puede desencadenar una alerta. Puede habilitar advertencias en las siguientes condiciones de rendimiento:  
  
-   Si se supera la latencia especificada (el intervalo de tiempo que transcurre entre la confirmación de una transacción en el publicador y confirmación de la transacción correspondiente en el suscriptor).  
  
     Esto se aplica a la replicación transaccional. Si se alcanza o sobrepasa el umbral especificado, el estado se mostrará como **Rendimiento crítico**.  
  
-   Si se supera el tiempo de sincronización especificado.  
  
     Esto se aplica a la replicación de mezcla. Si se alcance o supere el umbral especificado, el estado se muestra como **mezcla de ejecución prolongada**. Puede especificar diferentes umbrales para las conexiones de acceso telefónico o de red de área local (LAN).  
  
-   Si se produce un error en el procesamiento del número de filas especificado en un período de tiempo determinado.  
  
     Esto se aplica a la replicación de mezcla. Si se alcanza o sobrepasa el umbral especificado, el estado se mostrará como **Rendimiento crítico**. Puede especificar diferentes umbrales para las conexiones de acceso telefónico o de red de área local (LAN).  
  
 Para más información, consulte [Set Thresholds and Warnings in Replication Monitor](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
## Ver medidas de rendimiento  
 El Monitor de replicación muestra los valores de calidad del rendimiento de la replicación transaccional y de la replicación de mezcla en las columnas **Rendimiento medio actual** y **Peor rendimiento actual** para las publicaciones y en la columna **Rendimiento** para las suscripciones. Los valores son:  
  
-   Excelente  
  
-   Bueno  
  
-   Regular  
  
-   Insuficiente  
  
-   Crítico (solo replicación transaccional)  
  
 Los valores se determinan de las formas siguientes:  
  
-   En la replicación transaccional, la calidad del rendimiento se determina mediante el umbral de latencia. Si no se establece el umbral, no se muestra ningún valor. En la siguiente tabla se muestra la correlación entre el umbral y el valor de calidad del rendimiento. Por ejemplo, si el umbral se establece en 60 segundos y la latencia actual es de 30 segundos, la latencia supone un 50% del umbral, lo que da como resultado un valor de Bueno.  
  
    |Excelente|Bueno|Regular|Insuficiente|Crítico|  
    |---------------|----------|----------|----------|--------------|  
    |0 – 34%|35 – 59%|60 – 84%|85 – 99%|100% +|  
  
-   Replicación de mezcla, la calidad del rendimiento es independiente del umbral (el umbral de procesamiento de filas determinar si un valor de **rendimiento crítico** se muestra en el **estado** columna). La calidad del rendimiento se determina comparando el rendimiento de una suscripción individual con el rendimiento medio histórico de las suscripciones a la publicación que tienen el mismo tipo de conexión (de acceso telefónico o LAN). El Monitor de replicación muestra un valor una vez que se han producido cinco sincronizaciones con al menos 50 cambios en cada una a través del mismo tipo de conexión. Si ha habido menos de cinco sincronizaciones con al menos 50 cambios, o la sincronización más reciente tiene menos de 50 cambios, el Monitor de replicación no muestra ningún valor.  
  
     En la siguiente tabla se muestra la correlación entre el rendimiento medio y el valor de calidad del rendimiento. Por ejemplo, si diez suscriptores se han sincronizado mediante una conexión LAN con una velocidad media de 100 filas por segundo, y una de las suscripciones se sincroniza después a una velocidad de 125 filas por segundo, el rendimiento de la sincronización de ese suscriptor es 125% de la media, lo que da como resultado un valor de Bueno.  
  
    |Excelente|Bueno|Regular|Insuficiente|  
    |---------------|----------|----------|----------|  
    |151+%|76 – 150%|26 – 75%|0 – 25%|  
  
 Para obtener más información acerca de cómo ver información de suscripción, consulte [Ver información y realizar tareas para una suscripción & #40; Monitor de replicación & #41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md).  
  
## Determinar la latencia con testigos de seguimiento  
 La replicación transaccional le permite medir la latencia en un sistema insertando un token (una pequeña cantidad de datos) en el registro de transacciones de la base de datos de publicaciones y registrando cuánto tiempo tarda en llegar al distribuidor y a los suscriptores. El token también le permite identificar si los datos no están llegando al distribuidor o al suscriptor. Para más información, consulte [Measure Latency and Validate Connections for Transactional Replication](../../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md).  
  
## Ver detalles del rendimiento de la sincronización en la replicación de mezcla  
 En la replicación de mezcla, el Monitor de replicación muestra estadísticas detalladas de cada artículo que se procesa durante la sincronización, incluida la cantidad de tiempo  de cada fase del proceso (carga de cambios, descarga de cambios, etc.). Esto puede ayudar a identificar las tablas específicas que están causando una reducción de la velocidad y es el mejor lugar para solucionar problemas de rendimiento con las suscripciones de mezcla. Para obtener más información acerca de cómo ver estadísticas detalladas, consulte [Ver información y realizar tareas para los agentes asociados a una suscripción & #40; Monitor de replicación & #41;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
## Ver transacciones y tiempos de entrega en la replicación transaccional  
 En la replicación transaccional, el Monitor de replicación muestra información sobre el número de transacciones en la base de datos de distribución que no se han distribuido todavía a un suscriptor y el tiempo estimado para distribuir dichas transacciones. Para obtener más información, consulte [Ver información y realizar tareas para los agentes asociados a una suscripción & #40; Monitor de replicación & #41;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
## Vea también  
 [Supervisar la replicación](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)   
 [Establecer umbrales y advertencias en el Monitor de replicación](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md)  
  
  