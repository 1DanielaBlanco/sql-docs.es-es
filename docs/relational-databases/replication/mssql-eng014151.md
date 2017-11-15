---
title: MSSQL_ENG014151 | Microsoft Docs
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: MSSQL_ENG014151 error
ms.assetid: 54b45e70-46b3-4c7a-a5bf-06f6dd028ceb
caps.latest.revision: "17"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b6ff7b1cd07bfb91ab44ced875fc321c7b9ae34b
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="mssqleng014151"></a>MSSQL_ENG014151
    
## <a name="message-details"></a>Detalles del mensaje  
  
|||  
|-|-|  
|Nombre del producto|SQL Server|  
|Identificador del evento|14151|  
|Origen del evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nombre simbólico||  
|Texto del mensaje|Replicación-%s: error en el agente %s. %s|  
  
## <a name="explanation"></a>Explicación  
 Este error se produce en caso de fallo del agente de replicación. El texto al final del mensaje depende del contexto del error.  
  
## <a name="user-action"></a>Acción del usuario  
 Este error se puede producir en una serie de situaciones; aplique las siguientes soluciones según corresponda:  
  
-   Reinicie el agente en el que se ha producido el error para ver si se ejecuta correctamente. Para obtener más información, vea [Iniciar y detener un agente de replicación &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) y [Conceptos de los ejecutables del Agente de replicación](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
-   Compruebe el historial del agente y el historial de trabajos para ver otros errores que se hayan producido aproximadamente a la misma hora. Para obtener información sobre el modo de ver el estado del agente y los detalles del error en el Monitor de replicación, vea los siguientes temas:  
  
    -   Para el Agente de instantáneas, el Agente de registro del LOG y el Agente de lectura de cola, vea [Cómo ver información y realizar tareas para los agentes asociados a una publicación &#40;Monitor de replicación&#41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-publication-agents.md).  
  
    -   Para el Agente de distribución y el Agente de mezcla, vea [Ver información y realizar tareas para los agentes asociados a una suscripción &#40;Monitor de replicación&#41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-subscription-agents.md).  
  
-   Compruebe que la conectividad básica funciona entre los equipos a los que el agente tiene acceso y, a continuación, conecte a cada equipo con una herramienta como [sqlcmd Utility](../../tools/sqlcmd-utility.md). Para conectar, utilice la misma cuenta con la que el agente realiza las conexiones. Para obtener más información acerca de los permisos que necesita cada cuenta de agente, vea [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
-   Si se producen errores al crear o aplicar una instantánea, compruebe los archivos del directorio de la instantánea.  
  
-   Si el error persiste, aumente el registro del agente y especifique un archivo de salida para el registro. Dependiendo del contexto del error, esto puede proporcionar los pasos que conducen al error o a mensajes de error adicionales.  
  
## <a name="see-also"></a>Vea también  
 [Administración del Agente de replicación](../../relational-databases/replication/agents/replication-agent-administration.md)   
 [Referencia de errores y eventos &#40;replicación&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Agente de distribución de replicación](../../relational-databases/replication/agents/replication-distribution-agent.md)   
 [Agente de registro del LOG de replicación](../../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [Agente de mezcla de replicación](../../relational-databases/replication/agents/replication-merge-agent.md)   
 [Agente de lectura de cola de replicación](../../relational-databases/replication/agents/replication-queue-reader-agent.md)   
 [Replication Snapshot Agent](../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
  
