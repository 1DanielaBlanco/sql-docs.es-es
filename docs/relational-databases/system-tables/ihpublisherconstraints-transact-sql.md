---
title: IHpublisherconstraints (Transact-SQL) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/03/2017
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
- IHpublisherconstraints
- IHpublisherconstraints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublisherconstraints system table
ms.assetid: 537b1e1a-7228-4680-aa27-5ad7072ea01e
caps.latest.revision: 23
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 001caaf03b1bef6ccacad41da171ccd6bdb65283
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "33000582"
---
# <a name="ihpublisherconstraints-transact-sql"></a>IHpublisherconstraints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  El **IHpublisherconstraints** tabla del sistema contiene una fila por cada restricción replicada desde no publicadores de SQL Server utilizando el distribuidor actual. Esta tabla se almacena en la base de datos de distribución.  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**publisherconstraint_id**|**int**|Identifica una restricción publicada.|  
|**table_id**|**int**|Identifica la tabla de [IHpublishertables](../../relational-databases/system-tables/ihpublishertables-transact-sql.md) a la que pertenece la restricción.|  
|**publisher_id**|**smallint**|Identifica el no - publicador de SQL Server desde el que se publica la columna.|  
|**Nombre**|**sysname**|Nombre de la restricción publicada.|  
|**Tipo**|**nvarchar(255)**|Tipo de restricción admitido de la [IHconstrainttypes](../../relational-databases/system-tables/ihconstrainttypes-transact-sql.md) tabla del sistema.|  
  
## <a name="see-also"></a>Vea también  
 [Replicación de bases de datos heterogéneas](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Tablas de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vistas de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
