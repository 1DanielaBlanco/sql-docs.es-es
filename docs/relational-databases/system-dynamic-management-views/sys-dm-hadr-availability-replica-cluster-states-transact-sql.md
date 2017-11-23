---
title: Sys.dm_hadr_availability_replica_cluster_states (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_hadr_availability_replica_cluster_states_TSQL
- dm_hadr_availability_replica_cluster_states
- sys.dm_hadr_availability_replica_cluster_states
- dm_hadr_availability_replica_cluster_states_TSQL
dev_langs: TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], WSFC clusters
- sys.dm_hadr_availability_replica_cluster_states dynamic management view
ms.assetid: 2e0dd780-6a71-4f4b-b7f7-6e063bec71d6
caps.latest.revision: "12"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d7c173b034bd54bd187a78508d3d29b65b194406
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmhadravailabilityreplicaclusterstates-transact-sql"></a>sys.dm_hadr_availability_replica_cluster_states (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Devuelve una fila por cada Always On réplica de disponibilidad (independientemente de su estado de unión) de todos los grupos de disponibilidad AlwaysOn (independientemente de la ubicación de réplica) en el clúster de clústeres de conmutación por error de servidor de Windows (WSFC).  
  
##  <a name="connected_state"></a>  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**replica_id**|**uniqueidentifier**|Identificador único de la réplica de disponibilidad.|  
|**replica_server_name**|**nvarchar(256)**|Nombre de la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que hospeda la réplica.|  
|**group_id**|**uniqueidentifier**|Identificador único del grupo de disponibilidad.|  
|**join_state**|**tinyint**|0 = Sin unir<br /><br /> 1 = Instancia independiente unida<br /><br /> 2 = Instancia de clúster de conmutación por error unida|  
|**join_state_desc**|**nvarchar (60)**|NOT_JOINED<br /><br /> JOINED_STANDALONE_INSTANCE<br /><br /> JOINED_FAILOVER_CLUSTER_INSTANCE|  
  
## <a name="security"></a>Seguridad  
  
### <a name="permissions"></a>Permissions  
 es necesario contar con el permiso VIEW SERVER STATE en el servidor.  
  
## <a name="see-also"></a>Vea también  
 [Supervisar grupos de disponibilidad &#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)  
  
  
