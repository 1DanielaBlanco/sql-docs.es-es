---
title: MSagent_parameters (Transact-SQL) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSagent_parameters_TSQL
- MSagent_parameters
dev_langs:
- TSQL
helpviewer_keywords:
- MSagent_parameters system table
ms.assetid: be30abc9-c00d-446f-b1b4-1269772f37e6
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e6819ab211544394969ac631728991373fab879f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="msagentparameters-transact-sql"></a>MSagent_parameters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  El **MSagent_parameters** tabla contiene parámetros asociados a un perfil de agente. Los nombres de los parámetros son los mismos que los que admite el agente. Esta tabla se almacena en la **msdb** base de datos.  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**profile_id**|**int**|El identificador de perfil de la **MSagent_profiles** tabla.|  
|**parameter_name**|**sysname**|Nombre del parámetro.|  
|**value**|**nvarchar(255)**|El valor del parámetro.|  
  
## <a name="see-also"></a>Vea también  
 [Tablas de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vistas de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
