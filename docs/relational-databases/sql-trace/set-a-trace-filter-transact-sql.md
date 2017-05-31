---
title: Establecer un filtro de seguimiento (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- filters [SQL Server], traces
- traces [SQL Server], filters
ms.assetid: 7b976a84-7381-43a6-a828-ba83ada71cbe
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 991f41c8eefc83710b90782e364a55a91c20335f
ms.contentlocale: es-es
ms.lasthandoff: 04/11/2017

---
# <a name="set-a-trace-filter-transact-sql"></a>Establecer un filtro de seguimiento (Transact-SQL)
  En este tema se describe el modo de utilizar procedimientos almacenados para crear un filtro que solo recupere la información necesaria en un evento que se está trazando.  
  
### <a name="to-set-a-trace-filter"></a>Para establecer un filtro de seguimiento  
  
1.  Si el seguimiento ya se está ejecutando, ejecute **sp_trace_setstatus** con **@status = 0** para detener el seguimiento.  
  
2.  Ejecute **sp_trace_setfilter** para configurar el tipo de información que se debe recuperar para el evento objeto del seguimiento.  
  
> [!IMPORTANT]  
>  A diferencia de los procedimientos almacenados normales, los parámetros de todos los procedimientos almacenados del [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] (**sp_trace_*xx***) deben escribirse de forma precisa y no admiten la conversión automática de tipos de datos. Si no se llama a estos parámetros con los tipos de datos de parámetros de entrada correctos, según se especifica en la descripción del argumento, el procedimiento almacenado devolverá un error.  
  
## <a name="see-also"></a>Vea también  
 [Filtrar un seguimiento](../../relational-databases/sql-trace/filter-a-trace.md)   
 [sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)   
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Procedimientos almacenados de SQL Server Profiler &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql.md)  
  
  
