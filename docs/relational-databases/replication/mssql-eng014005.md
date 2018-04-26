---
title: MSSQL_ENG014005 | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG014005 error
ms.assetid: f168f0d6-cb11-45d4-9781-c374d7f388ee
caps.latest.revision: 13
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 020815a26ca91ab53243b543a2d5cc66603d75a3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="mssqleng014005"></a>MSSQL_ENG014005
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Detalles del mensaje  
  
|||  
|-|-|  
|Nombre del producto|SQL Server|  
|Identificador del evento|14005|  
|Origen del evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nombre simbólico||  
|Texto del mensaje|No se pudo quitar la publicación. Hay una suscripción para ella.|  
  
## <a name="explanation"></a>Explicación  
 Ha intentado quitar una publicación que tiene asociadas una o varias suscripciones. Una publicación se puede quitar únicamente si no hay suscripciones asociadas.  
  
## <a name="user-action"></a>Acción del usuario  
 Quite las suscripciones antes de quitar la publicación. Si utiliza [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] para quitar la publicación, se le ofrecerá la opción de quitar automáticamente todas las suscripciones asociadas antes de quitar la publicación. Si utiliza procedimientos almacenados, primero debe quitar explícitamente las suscripciones. Para obtener más información, consulte [Delete a Push Subscription](../../relational-databases/replication/delete-a-push-subscription.md) y [Delete a Pull Subscription](../../relational-databases/replication/delete-a-pull-subscription.md).  
  
 Si parece no existir ninguna suscripción para la publicación o si ve este error cuando crea la publicación, es posible que tenga una suscripción anterior que no se limpiara completamente cuando se quitó. Ejecute [sp_removedbreplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) en la base de datos para eliminar todos los objetos y la configuración completa relacionados con la replicación.  
  
## <a name="see-also"></a>Ver también  
 [Referencia de errores y eventos &#40;replicación&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
