---
title: IHpublishercolumnindexes (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHpublishercolumnindexes
- IHpublishercolumnindexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublishercolumnindexes system table
ms.assetid: 95b95a1d-b502-4838-825f-82a456487e25
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 70fce3c0c919a9d898e0dadf9d56e5ae5adaa0a7
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2018
ms.locfileid: "52802487"
---
# <a name="ihpublishercolumnindexes-transact-sql"></a>IHpublishercolumnindexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  El **IHpublishercolumnindexes** tabla del sistema asigna las columnas de una publicación que no son de SQL Server en el [IHpublishercolumns](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md) tabla del sistema a los índices en el [IHpublisherindexes](../../relational-databases/system-tables/ihpublisherindexes-transact-sql.md)tabla del sistema. Esta tabla se almacena en la base de datos de distribución.  
  
## <a name="definition"></a>Definición  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**publishercolumn_id**|**int**|Identifica la columna de [IHpublishercolumns](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md) con un índice asociado.|  
|**publisherindex_id**|**int**|Identifica un índice de la [IHpublisherindexes](../../relational-databases/system-tables/ihpublisherindexes-transact-sql.md) asociado a la columna de tabla.|  
|**indid**|**int**|Indica la posición de la columna en la tabla publicada.|  
  
## <a name="see-also"></a>Vea también  
 [Replicación de bases de datos heterogéneas](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Las tablas de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vistas de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
