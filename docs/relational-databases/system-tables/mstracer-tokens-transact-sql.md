---
title: MStracer_tokens (Transact-SQL) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
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
- MStracer_tokens_TSQL
- MStracer_tokens
dev_langs:
- TSQL
helpviewer_keywords:
- MStracer_tokens system table
ms.assetid: b273aa48-8188-4213-8e2c-311543c3236f
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 1822cdc0dd42a2e7797dec4aeb3a5b9627b4eac8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="mstracertokens-transact-sql"></a>MStracer_tokens (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  El **MStracer_tokens** tabla mantiene un registro de registros de token de seguimiento insertados en una publicación. Esta tabla se almacena en la base de datos de distribución y es utilizada por la replicación para la supervisión del rendimiento.   
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**tracer_id**|**int**|Identifica un registro de un token de seguimiento.|  
|**publication_id**|**int**|Identifica la publicación en la que se ha insertado el registro del token de seguimiento.|  
|**publisher_commit**|**datetime**|La fecha y la hora en que se ha confirmado el registro del token de seguimiento en el publicador.|  
|**distributor_commit**|**datetime**|La fecha y la hora en que se ha confirmado el registro del token de seguimiento en el distribuidor.|  
  
## <a name="see-also"></a>Vea también  
 [Tablas de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vistas de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
