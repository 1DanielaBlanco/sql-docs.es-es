---
title: MSSQLSERVER_18264 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 18264 (Database Engine error)
ms.assetid: 3050fc56-2be5-43cf-916b-50a3ac5f89aa
caps.latest.revision: 12
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 06ae22f5e2e7344a5934493bb893a07bdb20383a
ms.contentlocale: es-es
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver18264"></a>MSSQLSERVER_18264
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|Microsoft SQL Server|  
|Identificador del evento|18264|  
|Origen del evento|MSSQLENGINE|  
|Componente|SQLEngine|  
|Nombre simbólico|STRMIO_DBDUMP|  
|Texto del mensaje|Se ha realizado una copia de seguridad de la base de datos. Base de datos: %s, fecha de creación (tiempo): %s(%s), páginas volcadas: %d, primer LSN: %s, último LSN: %s, número de dispositivos de volcado: %d, información del dispositivo: (%s). Esto es solo un mensaje informativo. No se requiere ninguna acción del usuario.|  
  
## <a name="explanation"></a>Explicación  
De forma predeterminada, cada copia de seguridad correcta agrega este mensaje informativo al registro de errores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y al registro de eventos del sistema. Si hace una copia de seguridad del registro de transacciones con frecuencia, estos mensajes pueden acumularse rápidamente y crear registros de errores muy grandes, que pueden dificultar la búsqueda de otros mensajes.  
  
## <a name="user-action"></a>Acción del usuario  
Puede suprimir estas entradas de registro usando la marca de seguimiento de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **3226**. Habilitar esta marca de seguimiento es útil si ejecuta frecuentemente copias de seguridad de los registros y ninguno de los scripts depende de esas entradas.  
  
Para obtener información sobre cómo usar marcas de seguimiento, vea los Libros en pantalla de SQL Server.  
  
## <a name="see-also"></a>Vea también  
[Marcas de seguimiento &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)  
  

