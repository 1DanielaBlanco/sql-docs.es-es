---
title: Reproducir un Script de Transact-SQL (SQL Server Profiler) | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- traces [SQL Server], replaying
- scripts [SQL Server], traces
- replaying traces
ms.assetid: 9c0eb222-e6e3-4bc1-a25f-a41e962d361b
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: eed8da389f0c2422b3aee7ec947e5f34958f190d
ms.contentlocale: es-es
ms.lasthandoff: 08/02/2017

---
# <a name="replay-a-transact-sql-script-sql-server-profiler"></a>Reproducir un script Transact-SQL (SQL Server Profiler)
  Cuando pruebe posibles soluciones para un problema de rendimiento, utilice el [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] para reproducir scripts [!INCLUDE[tsql](../../includes/tsql-md.md)] y compare el rendimiento antes y después de los cambios.  
  
### <a name="to-replay-a-transact-sql-script"></a>Para reproducir un script Transact-SQL  
  
1.  En el menú **Archivo** , seleccione **Abrir**y haga clic en **Archivo de script**.  
  
2.  Seleccione el archivo de script [!INCLUDE[tsql](../../includes/tsql-md.md)] que desee abrir. Asegúrese de que el script [!INCLUDE[tsql](../../includes/tsql-md.md)] contiene los eventos necesarios para la reproducción. Para más información, consulte [Replay Requirements](../../tools/sql-server-profiler/replay-requirements.md).  
  
3.  En el menú **Reproducir** , haga clic en **Iniciar**y conéctese al servidor en el que desee reproducir el script.  
  
4.  Compruebe la configuración en el cuadro de diálogo **Configuración de reproducción** y haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Vea también  
 [Reproducir seguimientos](../../tools/sql-server-profiler/replay-traces.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  

