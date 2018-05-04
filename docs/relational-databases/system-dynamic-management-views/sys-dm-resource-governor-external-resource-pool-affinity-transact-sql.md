---
title: Sys.dm_resource_governor_external_resource_pool_affinity (Transact-SQL) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/13/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_external_resource_pool_affinity
- sys.dm_resource_governor_external_resource_pool_affinity_TSQL
- dm_resource_governor_external_resource_pool_affinity
- dm_resource_governor_external_resource_pool_affinity_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_resource_governor_external_resource_pool_affinity
- dm_resource_governor_external_resource_pool_affinity
ms.assetid: e32fac49-5161-47c0-8540-af3fe730c00c
caps.latest.revision: 8
author: jeannt
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 11a7ff1947d3c7cf53370a912bcba9368fb4302d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmresourcegovernorexternalresourcepoolaffinity-transact-sql"></a>Sys.dm_resource_governor_external_resource_pool_affinity (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]
**Se aplica a:** [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] y [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

Devuelve información de afinidad de CPU sobre la configuración actual del grupo de recursos externos.
  
|Nombre de columna|Tipo de datos|Description|
|----------------|---------------|-----------------|
|pool_id|**int**|El identificador del grupo de recursos externos. No admite valores NULL.|
|processor_group|**smallint**|Identificador del grupo de procesadores lógicos de Windows. No admite valores NULL.|
|cpu_mask|**bigint**|La máscara binaria que representa las CPU asociadas a este grupo. No admite valores NULL.|
  
## <a name="remarks"></a>Comentarios

Los grupos creados con la afinidad de `AUTO` no aparecen en esta vista porque no tienen ninguna afinidad. Para obtener más información, consulte el [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41; ](../../t-sql/statements/create-external-resource-pool-transact-sql.md) y [ALTER EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41; ](../../t-sql/statements/alter-external-resource-pool-transact-sql.md) instrucciones.

## <a name="permissions"></a>Permissions

Requiere el permiso `VIEW SERVER STATE`.

## <a name="see-also"></a>Vea también

[Resource governance for machine learning in SQL Server](../../advanced-analytics/r/resource-governance-for-r-services.md) (Gobierno de recursos para aprendizaje automático en SQL Server)

[sys.dm_resource_governor_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md)

[Opción de configuración de servidor Scripts externos habilitados](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)

[ALTER EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)
