---
title: MSSQL_ENG021286 | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG021286 error
ms.assetid: b63620b7-1c6d-46f7-90ea-3a8e99af8de4
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 94e5042a99ef6ea6df482cf86323f9444e006dbd
ms.contentlocale: es-es
ms.lasthandoff: 06/22/2017

---
# <a name="mssqleng021286"></a>MSSQL_ENG021286
    
## <a name="message-details"></a>Detalles del mensaje  
  
|||  
|-|-|  
|Nombre del producto|SQL Server|  
|Identificador del evento|21286|  
|Origen del evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nombre simbólico||  
|Texto del mensaje|La tabla de conflictos '%1!' no existe.|  
  
## <a name="explanation"></a>Explicación  
 Este error se produce si la tabla de conflictos de un artículo mencionado en [sysmergearticles &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysmergearticles-transact-sql.md) no existe realmente. El error se puede producir al intentar agregar o quitar una columna de una tabla publicada para la replicación de mezcla.  
  
## <a name="user-action"></a>Acción del usuario  
 Ejecute [DBCC CHECKDB &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) en la base de datos donde falta la tabla en conflicto para comprobar que no existen problemas de coherencia de datos.  
  
 Si la tabla de conflictos falta en un suscriptor, quite y vuelva a crear la suscripción. Si la tabla de conflictos falta en un publicador, quite todas las suscripciones, quite la publicación y vuelva a crear la publicación y todas las suscripciones. Para obtener más información sobre la creación de publicación, vea [Publicar datos y objetos de base de datos](../../relational-databases/replication/publish/publish-data-and-database-objects.md) y [Suscribirse a publicaciones](../../relational-databases/replication/subscribe-to-publications.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia de errores y eventos &#40;replicación&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  

