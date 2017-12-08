---
title: Nuevo perfil de agente | Microsoft Docs
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
f1_keywords: sql13.rep.profiles.newperfprofile.f1
helpviewer_keywords: New Agent Profile dialog box
ms.assetid: ebf59330-a421-45a5-9020-0484a96852bc
caps.latest.revision: "21"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e7f73501091ce352164db71ebf4ebf8758d0c40e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="new-agent-profile"></a>Nuevo perfil de agente
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Utilice el cuadro de diálogo **Nuevo perfil de agente** para crear un perfil nuevo. Los perfiles nuevos siempre se basan en perfiles existentes, pero pueden modificarse para satisfacer los requisitos de la aplicación. Después de crear el perfil, éste puede aplicarse a trabajos de agente existentes y futuros en el cuadro de diálogo **Perfiles de agente** . Los valores de los parámetros de agente pueden modificarse en el cuadro de diálogo \<**Propiedades de <NombrePerfilAgente>**.  
  
## <a name="options"></a>Opciones  
 **Nombre**  
 Escriba un nombre para el perfil.  
  
 **Descripción**  
 Escriba una descripción para el perfil.  
  
 **Parámetro**  
 Parámetros de agente incluidos en el perfil. El perfil en el que se basa el nuevo perfil no especifica necesariamente un valor para cada parámetro. Para ver todos los parámetros válidos para un agente determinado, desactive la casilla **Mostrar solo los parámetros utilizados en este perfil** . Para obtener una descripción de cada parámetro, vea:  
  
-   [Agente de instantáneas de replicación](../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
-   [Agente de registro del LOG de replicación](../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
-   [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md)  
  
-   [Agente de mezcla de replicación](../../relational-databases/replication/agents/replication-merge-agent.md)  
  
-   [Agente de lectura de cola de replicación](../../relational-databases/replication/agents/replication-queue-reader-agent.md)  
  
 **Valor predeterminado**  
 Valor predeterminado para cada parámetro de agente.  
  
 **Valor**  
 Valor especificado para el parámetro en el perfil en el que se basa el perfil nuevo. Modifique este campo para todos los parámetros que desee cambiar.  
  
 **Mostrar solo los parámetros utilizados en este perfil**  
 Desactive esta opción si desea mostrar todos los parámetros válidos para un agente determinado.  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con perfiles del Agente de replicación](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)   
 [Replication Agents Overview](../../relational-databases/replication/agents/replication-agents-overview.md)  (Información general sobre los agentes de replicación)  
 [Perfiles del Agente de replicación](../../relational-databases/replication/agents/replication-agent-profiles.md)  
  
  
