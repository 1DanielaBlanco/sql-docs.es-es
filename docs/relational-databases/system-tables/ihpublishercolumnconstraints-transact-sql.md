---
title: IHpublishercolumnconstraints (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- IHpublishercolumnconstraints
- IHpublishercolumnconstraints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublishercolumnconstraints system table
ms.assetid: d7a41da6-e067-430a-8da2-3f6745b8a4f3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 00b937c949019bf1952977685cf063bf05c23e73
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47724863"
---
# <a name="ihpublishercolumnconstraints-transact-sql"></a>IHpublishercolumnconstraints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  El **IHpublishercolumnconstraints** tabla del sistema asigna las columnas de una publicación que no son de SQL Server en el [IHpublishercolumns](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md) tabla del sistema a las restricciones en el [IHpublisherconstraints ](../../relational-databases/system-tables/ihpublisherconstraints-transact-sql.md) tabla del sistema. Esta tabla se almacena en la base de datos de distribución.  
  
## <a name="definition"></a>Definición  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**publishercolumn_id**|**int**|Identifica la columna de [IHpublishercolumns](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md) con una restricción asociada.|  
|**publisherconstraint_id**|**int**|Identifica una restricción de [IHpublisherconstraints](../../relational-databases/system-tables/ihpublisherconstraints-transact-sql.md) asociado a la columna.|  
|**indid**|**int**|Indica la posición de la columna en la tabla publicada.|  
  
## <a name="see-also"></a>Vea también  
 [Replicación de bases de datos heterogéneas](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Las tablas de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vistas de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
