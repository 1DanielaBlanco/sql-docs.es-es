---
title: MSSQL_REPL020011 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_REPL020011 error
ms.assetid: f72072d7-bbb6-48ad-ac88-afa74aeb4d58
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ba583ef9cd69e7aa0256d8075c511edde2fd0a45
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2018
ms.locfileid: "48123565"
---
# <a name="mssqlrepl020011"></a>MSSQL_REPL020011
    
## <a name="message-details"></a>Detalles del mensaje  
  
|||  
|-|-|  
|Nombre del producto|SQL Server|  
|Identificador del evento|20011|  
|Origen del evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nombre simbólico||  
|Texto del mensaje|El proceso no pudo ejecutar '%1' en '%2'.|  
  
## <a name="explanation"></a>Explicación  
 Este error se puede generar en una serie de circunstancias durante el procesamiento de la replicación transaccional, por ejemplo, cuando el Agente de registro del LOG ejecuta **sp_replcmds** (el proceso no pudo ejecutar "sp_replcmds" en \<nombreDeServidor>) o **sp_repldone** (el proceso no pudo ejecutar "sp_repldone" en \<nombreDeServidor>).  
  
## <a name="user-action"></a>Acción del usuario  
 Si este error se genera en una base de datos que acaba de restaurar de una copia de seguridad, asegúrese de que ha seguido los pasos descritos en la documentación referente a copias de seguridad y restauración, incluida la ejecución de **sp_replrestart** si fuese necesario. Para más información, consulte [Estrategias para hacer copias de seguridad y restaurar replicación de instantáneas o replicación transaccional](administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md).  
  
 Se trata de un error de procesamiento interno y si se genera en circunstancias diferentes a una restauración, normalmente indica que la replicación se debe quitar y volver a configurar. Si no puede quitar la replicación, póngase en contacto con el soporte técnico para obtener ayuda.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de errores y eventos &#40;replicación&#41;](errors-and-events-reference-replication.md)   
 [sp_replcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql)   
 [sp_repldone &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-repldone-transact-sql)  
  
  
