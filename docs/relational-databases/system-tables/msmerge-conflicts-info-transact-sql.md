---
title: MSmerge_conflicts_info (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
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
- MSmerge_conflicts_info_TSQL
- MSmerge_conflicts_info
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_conflicts_info system table
ms.assetid: 6b76ae96-737a-4000-a6b6-fcc8772c2af4
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 41388cd1cc2d7a33f0b976ad62eca5e7f55aeade
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39103643"
---
# <a name="msmergeconflictsinfo-transact-sql"></a>MSmerge_conflicts_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  El **MSmerge_conflicts_info** tabla realiza el seguimiento de conflictos que se producen al sincronizar una suscripción a una publicación de combinación. Los datos de la fila perdedora de conflictos se almacenan en el [MSmerge_conflict_publication_article](../../relational-databases/system-tables/msmerge-conflict-publication-article-transact-sql.md) tabla para el artículo donde se produjo el conflicto. Esta tabla se almacena en la base de datos de publicación del publicador y en la base de datos de suscripciones del suscriptor.  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|El alias de la tabla publicada.|  
|**rowguid**|**uniqueidentifier**|Identificador de la fila en conflicto.|  
|**origin_datasource**|**nvarchar(255)**|Nombre de la base de datos donde se originó el cambio conflictivo.|  
|**conflict_type**|**int**|Tipo de conflicto que ocurrió y que puede ser uno de los siguientes:<br /><br /> **1** = conflicto de actualización: el conflicto se detecta en el nivel de fila.<br /><br /> **2** = conflicto de actualización de columna: el conflicto se detecta en el nivel de columna.<br /><br /> **3** = conflicto de actualización eliminar Wins: la eliminación gana el conflicto.<br /><br /> **4** = Wins eliminar conflictos de actualización: la columna rowguid eliminada que pierde el conflicto se registra en esta tabla.<br /><br /> **5** = error de inserción en carga: la inserción desde el suscriptor no pudo aplicarse en el publicador.<br /><br /> **6** = error de inserción en descarga: la inserción desde el publicador no pudo aplicarse en el suscriptor.<br /><br /> **7** = error de eliminación en carga: no se pudo cargar la eliminación en el suscriptor al publicador.<br /><br /> **8** = error de eliminación en descarga: no se pudo descargar la eliminación en el publicador al suscriptor.<br /><br /> **9** = error de actualización en carga: la actualización en el suscriptor no pudo aplicarse en el publicador.<br /><br /> **10** = error de actualización en descarga: la actualización en el publicador no pudo aplicarse al suscriptor.<br /><br /> **11** = resolución<br /><br /> **12** = lógico actualización de registro de Wins eliminar: el registro lógico eliminado que pierde el conflicto se registra en esta tabla.<br /><br /> **13** = lógico registro conflicto de inserción y actualización: insertar en un registro lógico entra en conflicto con una actualización.<br /><br /> **14** = conflicto de actualización gana de eliminación de registro lógico: el registro lógico actualizado que pierde el conflicto se registra en esta tabla.|  
|**reason_code**|**int**|Código de error que puede depender del contexto. En el caso de conflictos de actualización-actualización y eliminación-actualización, el valor utilizado para esta columna es el mismo que el **conflict_type**. No obstante, para los conflictos de cambio con error, el código de motivo es el error que evitó que el Agente de mezcla aplicara el cambio. Por ejemplo, si el agente de mezcla no se puede aplicar una inserción en el suscriptor debido a una infracción de clave principal, registra un **conflict_type** de 6 ("descarga de error de inserción") y un **reason_code** de 2627, que es el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mensaje de error interno de una infracción de clave principal: "infracción de restricción %ls ' %. * ls'. No se puede insertar una clave duplicada en el objeto ' %. \*ls'. "|  
|**reason_text**|**nvarchar(720)**|Descripción del error que puede depender del contexto.|  
|**pubid**|**uniqueidentifier**|El identificador de la publicación.|  
|**MSrepl_create_time**|**datetime**|Momento en el que se produjo el conflicto.|  
|**origin_datasource_id**|**uniqueidentifier**|Identificador de la base de datos donde se originó el cambio conflictivo.|  
  
## <a name="see-also"></a>Vea también  
 [Las tablas de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vistas de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
