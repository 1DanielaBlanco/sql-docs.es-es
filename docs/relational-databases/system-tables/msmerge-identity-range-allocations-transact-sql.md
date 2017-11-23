---
title: MSmerge_identity_range_allocations (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- MSmerge_identity_range_allocations
- MSmerge_identity_range_allocations_TSQL
dev_langs: TSQL
helpviewer_keywords: MSmerge_identity_range_allocations system table
ms.assetid: 6362e35e-0ab3-4638-855b-1ce013f5fd6d
caps.latest.revision: "13"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ad5ad628c5f839c64d88c54e777aca7e0bc52b7e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="msmergeidentityrangeallocations-transact-sql"></a>MSmerge_identity_range_allocations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  El **MSmerge_identity_range_allocations** tabla sirve para realizar un seguimiento del historial de asignaciones de intervalo de identidad, a los publicadores y suscriptores, de los artículos publicados. Esta tabla se almacena en la base de datos de distribución.  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**iddeeditor**|**smallint**|El identificador del publicador.|  
|**publisher_db**|**nvarchar (128)**|El nombre de la base de datos de publicación.|  
|**publicación**|**nvarchar (128)**|Nombre de la publicación.|  
|**artículo**|**nvarchar (128)**|El nombre del artículo.|  
|**suscriptor**|**nvarchar (128)**|Nombre del suscriptor.|  
|**subscriber_db**|**nvarchar (128)**|El nombre de la base de datos de suscripción.|  
|**is_pub_range**|**bit**|Muestra si el intervalo de identidad está asignado a un publicador.|  
|**ranges_allocated**|**tinyint**|Número de intervalos de identidad asignados.|  
|**range_begin**|**numeric(38)**|Valor inicial del intervalo.|  
|**range_end**|**numeric(38)**|Último valor del intervalo.|  
|**next_range_begin**|**numeric(38)**|Valor inicial del siguiente intervalo que se va a asignar.|  
|**next_range_end**|**numeric(38)**|Último valor del siguiente intervalo que se va a asignar.|  
|**max_used**|**numeric(38)**|Mayor valor de identidad utilizado.|  
|**time_of_allocation**|**datetime**|Hora en la que se realizó la asignación.|  
  
## <a name="see-also"></a>Vea también  
 [Tablas de replicación &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vistas de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
