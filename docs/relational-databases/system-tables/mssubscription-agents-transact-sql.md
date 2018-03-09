---
title: MSsubscription_agents (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSsubscription_agents
- MSsubscription_agents_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscription_agents system table
ms.assetid: 86ad5891-0bef-4963-9381-7d5b45245a0c
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 11ad8bb029c1a083a4490cfe62e2bacf54b37d01
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="mssubscriptionagents-transact-sql"></a>MSsubscription_agents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  El **MSsubscription_agents** tabla se utiliza por el agente de distribución y los desencadenadores de suscripciones actualizables para realizar un seguimiento de propiedades de la suscripción. Esta tabla se almacena en la base de datos de suscripción.  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Id. de la fila.|  
|**publicador**|**sysname**|El nombre del publicador.|  
|**publisher_db**|**sysname**|El nombre de la base de datos de publicación.|  
|**publicación**|**sysname**|Nombre de la publicación.|  
|**subscription_type**|**int**|El tipo de suscripción:<br /><br /> 0 = Inserción.<br /><br /> 1 = Extracción<br /><br /> 2 = Extracción anónima|  
|**queue_id**|**sysname**|El identificador de la [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queue en el publicador. *queue_id* está establecido en **SQL** para basados en SQL de actualización en cola.|  
|**update_mode**|**tinyint**|El tipo de actualización:<br /><br /> **0** = solo lectura.<br /><br /> **1** = actualización inmediata.<br /><br /> **2** = actualización en cola mediante Message Queue Server.<br /><br /> **3** = inmediato actualizar con actualización en cola como conmutación por error mediante Message Queue Server.<br /><br /> **4** = actualización en cola mediante cola de SQL Server.<br /><br /> **5** = actualización inmediata con conmutación por error de actualización en cola, mediante cola de SQL Server.|  
|**failover_mode**|**bit**|Si se selecciona un tipo de actualización por conmutación por error, se elige este tipo de conmutación por error:<br /><br /> **0** = inmediato se utiliza la actualización. No se habilita la conmutación por error.<br /><br /> **1** = en cola se utiliza la actualización. Se habilita la conmutación por error. La cola que se utiliza para la conmutación por error se especifica en el *update_mode* valor.|  
|**SPID**|**int**|Id. del proceso de sistema para la conexión que utiliza el Agente de distribución actualmente en ejecución o recientemente ejecutado.|  
|**login_time**|**datetime**|La fecha y la hora de la conexión del Agente de distribución actualmente en ejecución o recientemente ejecutado.|  
|**allow_subscription_copy**|**bit**|Especifica si se permite o no la capacidad de copiar de la base de datos de suscripciones.|  
|**attach_state**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**attach_version**|**binary (16)**|Identificador único que representa la versión de una suscripción adjunta.|  
|**last_sync_status**|**int**|El último estado del Agente de distribución actualmente en ejecución o recientemente ejecutado. El estado puede ser:<br /><br /> **1** = iniciado.<br /><br /> **2** = se realizó correctamente.<br /><br /> **3** = en curso.<br /><br /> **4** = inactivo.<br /><br /> **5** = reintento.<br /><br /> **6** = error.|  
|**last_sync_summary**|**sysname**|El último mensaje del Agente de distribución actualmente en ejecución o recientemente ejecutado. El estado puede ser:<br /><br /> **Se inició.**<br /><br /> **Se realizó correctamente.**<br /><br /> **En curso.**<br /><br /> **Inactivo.**<br /><br /> **Intente de nuevo.**<br /><br /> **Producirá un error.**|  
|**last_sync_time**|**datetime**|La fecha y hora cuando el *last_sync_summary* y *last_sync_status* columnas se actualizaron. Los Agentes de distribución anónimos o de extracción que se ejecutan como trabajos del servicio del Agente SQL Server no actualizan estas columnas. En su lugar, la información del historial se registra en la tabla del historial de trabajos en ese caso.|  
|**queue_server**|**sysname**|Exclusivamente para uso interno.|  
  
## <a name="see-also"></a>Vea también  
 [Tablas de replicación &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vistas de replicación &#40; Transact-SQL &#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_helppullsubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)  
  
  
