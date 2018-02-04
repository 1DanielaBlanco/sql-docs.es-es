---
title: sys.dm_hadr_availability_group_states (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_hadr_availability_group_states
- sys.dm_hadr_availability_group_states_TSQL
- dm_hadr_availability_group_states_TSQL
- dm_hadr_availability_group_states
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.dm_hadr_availability_group_states dynamic management view
ms.assetid: d18019dd-f8dc-4492-b035-b1a639369b65
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b4d6dbddbf0fb211335789eefeff5f2a392f2d59
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmhadravailabilitygroupstates-transact-sql"></a>sys.dm_hadr_availability_group_states (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Devuelve una fila para cada grupo de disponibilidad AlwaysOn que posee una réplica de disponibilidad en la instancia local de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cada fila muestra los estados que definen el estado de un grupo de disponibilidad determinado.  
  
> [!NOTE]  
>  Para obtener una lista completa de, consulte el [sys.availability_groups](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md) vista de catálogo.  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**group_id**|**uniqueidentifier**|Identificador único del grupo de disponibilidad.|  
|**primary_replica**|**varchar(128)**|Nombre de la instancia de servidor que hospeda la réplica principal actual.<br /><br /> NULL = No es la réplica principal no se puede comunicar con el clúster de conmutación por error de WSFC.|  
|**primary_recovery_health**|**tinyint**|Indica el estado de recuperación de la réplica principal; puede ser uno de los siguientes:<br /><br /> 0 = en curso<br /><br /> 1 = En línea<br /><br /> NULL<br /><br /> En las réplicas secundarias del **primary_recovery_health** columna es NULL.|  
|**primary_recovery_health_desc**|**nvarchar(60)**|Descripción de **primary_replica_health**, uno de:<br /><br /> ONLINE_IN_PROGRESS<br /><br /> ONLINE<br /><br /> NULL|  
|**secondary_recovery_health**|**tinyint**|Indica el estado de recuperación de una réplica secundaria, uno de:<br /><br /> 0 = en curso<br /><br /> 1 = En línea<br /><br /> NULL<br /><br /> En la réplica principal, el **secondary_recovery_health** columna es NULL.|  
|**secondary_recovery_health_desc**|**nvarchar(60)**|Descripción de **secondary_recovery_health**, uno de:<br /><br /> ONLINE_IN_PROGRESS<br /><br /> ONLINE<br /><br /> NULL|  
|**synchronization_health**|**tinyint**|Refleja un resumen de la **synchronization_health** de todas las réplicas de disponibilidad del grupo de disponibilidad. A continuación se muestran los valores posibles y sus descripciones.<br /><br /> 0: no funciona correctamente. Ninguna de las réplicas de disponibilidad tiene un **synchronization_health** (2 = HEALTHY).<br /><br /> 1: parcialmente correcto. El estado de sincronización de algunas réplicas de disponibilidad, pero no de todas, es correcto.<br /><br /> 2: correcto. El estado de sincronización de todas las réplicas de disponibilidad es correcto.<br /><br /> Para obtener información sobre el estado de sincronización de réplica, vea el **synchronization_health** columna [sys.dm_hadr_availability_replica_states &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql.md).|  
|**synchronization_health_desc**|**nvarchar(60)**|Descripción de **synchronization_health**, uno de:<br /><br /> NOT_HEALTHY<br /><br /> PARTIALLY_HEALTHY<br /><br /> HEALTHY|  
  
## <a name="security"></a>Seguridad  
  
### <a name="permissions"></a>Permissions  
 es necesario contar con el permiso VIEW SERVER STATE en el servidor.  
  
## <a name="see-also"></a>Vea también  
 [Supervisar grupos de disponibilidad &#40; Transact-SQL &#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [Grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [Siempre en funciones y vistas de administración dinámica de grupos de disponibilidad &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)  
  
  
