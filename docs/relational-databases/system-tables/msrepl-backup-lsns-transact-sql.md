---
title: MSrepl_backup_lsns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSrepl_backup_lsns_TSQL
- MSrepl_backup_lsns
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_backup_Isns system table
ms.assetid: de06c349-82a8-48c6-b602-b5d6938514f6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cba647dea02963f61963115d3e68708136708cfe
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47737343"
---
# <a name="msreplbackuplsns-transact-sql"></a>MSrepl_backup_lsns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  El **MSrepl_backup_lsns** tabla contiene los números de secuencia de registro de transacciones (LSN) para admitir la opción 'sync with backup' de la base de datos de distribución. Esta tabla se almacena en la base de datos de distribución.  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**publisher_database_id**|**int**|El Id. de la base de datos del publicador.|  
|**valid_xact_id**|**varbinary (16)**|El Id. de la transacción que se va a enviar al publicador para marcar el punto de truncamiento del registro. Usar sólo si la base de datos de distribución está en modo 'sync with backup'. Contiene el Id. de la última transacción replicada en la base de datos de distribución de la que se ha hecho una copia de seguridad. Se enviará al publicador para que el lector del registro marque el punto de truncamiento del registro.|  
|**valid_xact_seqno**|**varbinary (16)**|El número de secuencia de la transacción que se va a enviar al publicador para marcar el punto de truncamiento del registro. Se utiliza solamente si la base de datos de distribución está en el modo 'sync with backup'. Es el número de secuencia de registro de la última transacción replicada en la base de datos de distribución de la que se hecho una copia de seguridad. Se enviará al publicador para que el lector del registro marque el punto de truncamiento del registro.|  
|**next_xact_id**|**varbinary (16)**|El número de secuencia de registro temporal que utilizan las operaciones de copia de seguridad.|  
|**nextx_xact_seqno**|**varbinary (16)**|El número de secuencia de registro temporal que utilizan las operaciones de copia de seguridad.|  
  
## <a name="see-also"></a>Vea también  
 [Las tablas de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vistas de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
