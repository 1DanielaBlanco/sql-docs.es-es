---
title: Sys.dm_hadr_name_id_map (Transact-SQL) | Documentos de Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_hadr_name_id_map
- sys.dm_hadr_name_id_map_TSQL
- dm_hadr_name_id_map
- dm_hadr_name_id_map_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.dm_hadr_name_id_map dynamic management view
ms.assetid: e07bb8a9-37de-4a39-a257-950d7c3ae8fb
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 69b1fd2e09b4f7c13540928328e4d5ca0697a530
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmhadrnameidmap-transact-sql"></a>sys.dm_hadr_name_id_map (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Muestra la asignación de grupos de disponibilidad AlwaysOn que la instancia actual de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se ha unido a tres identificadores únicos: un disponibilidad Id. de grupo, un identificador de recurso WSFC y un identificador de grupo de WSFC. La finalidad de esta asignación es controlar el escenario en el que cambia el nombre del recurso o el grupo de WSFC.  
   
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**ag_name**|**nvarchar(256)**|Nombre del grupo de disponibilidad. Se trata de un nombre especificado por el usuario que debe ser único dentro del clúster del clúster de conmutación por error de Windows Server (WSFC).|  
|**ag_id**|**uniqueidentifier**|Identificador único (GUID) del grupo de disponibilidad.|  
|**ag_resource_id**|**nvarchar(256)**|Identificador único del grupo de disponibilidad como un recurso del clúster de WSFC.|  
|**ag_group_id**|**nvarchar(256)**|Identificador de grupo WSFC único del grupo de disponibilidad.|  
  
## <a name="permissions"></a>Permissions  
 es necesario contar con el permiso VIEW SERVER STATE en el servidor.  
  
## <a name="see-also"></a>Vea también  
 [Funciones y vistas de administración dinámica de grupos de disponibilidad AlwaysOn &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)   
 [Vistas de catálogo de grupos de disponibilidad AlwaysOn &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [Supervisar grupos de disponibilidad & #40; Transact-SQL & #41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [Grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
