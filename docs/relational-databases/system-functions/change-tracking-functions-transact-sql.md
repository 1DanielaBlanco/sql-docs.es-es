---
title: Funciones (Transact-SQL) el seguimiento de cambios | Documentos de Microsoft
ms.custom: ''
ms.date: 08/08/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- functions [SQL Server], change tracking
- change tracking [SQL Server], functions
ms.assetid: 04eb53c4-8b69-414e-9696-185d227fea35
caps.latest.revision: 10
author: rothja
ms.author: jroth
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: c478d4ca59db55cefe5e13444fd81ea7bf64dbea
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "33227271"
---
# <a name="change-tracking-functions-transact-sql"></a>Funciones de seguimiento de cambios (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  El mecanismo de seguimiento de cambios registra las operaciones de inserción, actualización y eliminación aplicadas sobre las tablas con seguimiento, y proporciona los detalles de los cambios en un formato relacional de fácil uso. Las siguientes funciones devuelven información acerca de los cambios.  
  
|Función|Descripción|  
|--------------|-----------------|  
|[CHANGETABLE (CHANGES)](../../relational-databases/system-functions/changetable-transact-sql.md)|Devuelve información de seguimiento de todos los cambios en una tabla producidos desde una versión especificada.|  
|[CHANGETABLE (VERSION)](../../relational-databases/system-functions/changetable-transact-sql.md)|Devuelve la última información de seguimiento de cambios para una fila especificada.|  
|[CHANGE_TRACKING_MIN_VALID_VERSION)](../../relational-databases/system-functions/change-tracking-min-valid-version-transact-sql.md)|Devuelve la versión mínima que es válida para su uso en la obtención de seguimiento de cambios de la tabla especificada cuando utilizas el [CHANGETABLE](../../relational-databases/system-functions/changetable-transact-sql.md) función.|  
|[CHANGE_TRACKING_CURRENT_VERSION](../../relational-databases/system-functions/change-tracking-current-version-transact-sql.md)|Obtiene una versión que está asociada a la última transacción confirmada. Puede utilizar esta versión la próxima vez que se enumeren los cambios mediante CHANGETABLE.|  
|[CHANGE_TRACKING_IS_COLUMN_IN_MASK](../../relational-databases/system-functions/change-tracking-is-column-in-mask-transact-sql.md)|Interpreta el valor SYS_CHANGE_COLUMNS devuelto por la función CHANGETABLE (CHANGES …).|  
|[WITH CHANGE_TRACKING_CONTEXT](../../relational-databases/system-functions/with-change-tracking-context-transact-sql.md)|Habilita la especificación de un contexto de cambios, como un Id. del autor, cuando una aplicación cambia los datos.|  
  
## <a name="see-also"></a>Vea también  
 [Seguimiento de cambios de datos &#40;SQL Server&#41;](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
  
