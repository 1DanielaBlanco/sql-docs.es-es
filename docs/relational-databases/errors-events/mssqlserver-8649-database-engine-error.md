---
title: MSSQLSERVER_8649 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 8649 (Database Engine error)
ms.assetid: 992dbc74-7c3a-498b-9f1b-b28387640677
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e87c496b60ce000ec148b79e7556a5cd15edfcdf
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver8649"></a>MSSQLSERVER_8649
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|SQL Server|  
|Identificador del evento|8649|  
|Origen del evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|COST_TOO_HIGH|  
|Texto del mensaje|Se ha cancelado la consulta porque el costo estimado de esta consulta (%d) supera el umbral configurado de %d. Póngase en contacto con el administrador del sistema.|  
  
## <a name="explanation"></a>Explicación  
La consulta se canceló porque el costo estimado de la misma supera el umbral configurado establecido para QUERY_GOVERNOR_COST_LIMIT.  
  
## <a name="user-action"></a>Acción del usuario  
Establezca la opción QUERY_GOVERNOR_COST_LIMIT en un valor mayor.  
  
## <a name="see-also"></a>Ver también  
[SET QUERY_GOVERNOR_COST_LIMIT &#40;Transact-SQL&#41;](~/t-sql/statements/set-query-governor-cost-limit-transact-sql.md)  
  
