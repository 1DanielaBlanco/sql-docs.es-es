---
title: sys.dm_xe_session_event_actions (Transact-SQL) | Microsoft Docs
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
- dm_xe_session_event_actions_TSQL
- sys.dm_xe_session_event_actions_TSQL
- dm_xe_session_event_actions
- sys.dm_xe_session_event_actions
dev_langs:
- TSQL
helpviewer_keywords:
- extended events [SQL Server], views
- sys.dm_xe_session_event_actions dynamic management view
ms.assetid: 0c22a546-683e-4c84-ab97-1e9e95304b03
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d5e342265fe96a892983af51e6efc119a5bac914
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmxesessioneventactions-transact-sql"></a>sys.dm_xe_session_event_actions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve información sobre las acciones de la sesión de eventos. Se ejecutan las acciones cuando se activan los eventos. Esta vista de administración agrega estadísticas del número de veces que se ha ejecutado una acción y el tiempo de ejecución total de la acción.  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary(8)**|La dirección de memoria de la sesión de eventos. No admite valores NULL.|  
|action_name|**nvarchar(60)**|El nombre de la acción. No admite valores NULL.|  
|action_package_guid|**uniqueidentifier**|El GUID del paquete que contiene la acción. No admite valores NULL.|  
|event_name|**nvarchar(60)**|Nombre del evento al que se enlaza la acción. No admite valores NULL.|  
|event_package_guid|**uniqueidentifier**|El GUID para el paquete que contiene el evento. No admite valores NULL.|  
  
## <a name="permissions"></a>Permissions  
 es necesario contar con el permiso VIEW SERVER STATE en el servidor.  
  
### <a name="relationship-cardinalities"></a>Cardinalidades de relación  
  
|De|En|Relación|  
|----------|--------|------------------|  
|sys.dm_xe_session_event_actions.event_session_address|sys.dm_xe_sessions.address|Varios a uno|  
|sys.dm_xe_session_event_actions.action_name<br /><br /> sys.dm_xe_session_event_actions.action_package_guid|sys.dm_xe_objects.name<br /><br /> sys.dm_xe_session_events.event_package_guid|Varios a uno|  
|sys.dm_xe_session_event_actions.event_name<br /><br /> sys.dm_xe_session_event_actions.event_package_guid|sys.dm_xe_objects.name<br /><br /> sys.dm_xe_objects.package_guid|Varios a uno|  
  
## <a name="change-history"></a>Historial de cambios  
  
|Contenido actualizado|  
|---------------------|  
|Se actualiza la tabla "Cardinalidades de relación" con los nombres de las vistas de administración dinámica correctos y los nombres de las columnas.|  
  
## <a name="see-also"></a>Vea también  
 [Funciones y vistas de administración dinámica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

