---
title: dbo.sysproxysubsystem (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.sysproxysubsystem_TSQL
- dbo.sysproxysubsystem
- sysproxysubsystem_TSQL
- sysproxysubsystem
dev_langs: TSQL
helpviewer_keywords: sysproxysubsystem system table
ms.assetid: 6d7713f5-1253-4a19-b1fb-635c377c95c1
caps.latest.revision: "13"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 900fccb96581933857d2c8d38419d1a454d93dd1
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="dbosysproxysubsystem-transact-sql"></a>dbo.sysproxysubsystem (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Registra qué subsistema del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se utiliza en cada cuenta de proxy. Esta tabla se almacena en la **msdb** base de datos.  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**subsystem_id**|**int**|Id. del subsistema. Este valor corresponde a la **subsystem_id** columna en el **syssubsystems** tabla.|  
|**proxy_id**|**int**|Id. de la cuenta de proxy. Este valor corresponde a la **proxy_id** columna en el **sysproxies** tabla.|  
  
## <a name="remarks"></a>Comentarios  
 Solo los miembros de la **sysadmin** rol fijo de servidor puede tener acceso a esta tabla.  
  
## <a name="see-also"></a>Vea también  
 [dbo.syssubsystems &#40; Transact-SQL &#41;](../../relational-databases/system-tables/dbo-syssubsystems-transact-sql.md)   
 [dbo.sysproxies &#40; Transact-SQL &#41;](../../relational-databases/system-tables/dbo-sysproxies-transact-sql.md)  
  
  
