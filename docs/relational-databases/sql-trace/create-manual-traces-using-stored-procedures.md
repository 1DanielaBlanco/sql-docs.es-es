---
title: "Crear seguimientos manuales mediante procedimientos almacenados | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f6f47fa2-7c17-41d4-9f69-9be144d56832
caps.latest.revision: 7
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 7
---
# Crear seguimientos manuales mediante procedimientos almacenados
  Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ofrece procedimientos almacenados del sistema [!INCLUDE[tsql](../../includes/tsql-md.md)] para crear seguimientos en una instancia del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Puede utilizar estos procedimientos almacenados del sistema desde sus propias aplicaciones para crear seguimientos manualmente, en lugar de utilizar el [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Esto permite escribir aplicaciones personalizadas específicas para las necesidades de la organización.  
  
## En esta sección  
 En la tabla siguiente se enumeran los procedimientos almacenados del sistema para realizar el seguimiento de una instancia del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
|Procedimiento almacenado|Tarea realizada|  
|----------------------|--------------------|  
|[sys.fn_trace_geteventinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql.md)|Devuelve información acerca de los eventos incluidos en el seguimiento.|  
|[sys.fn_trace_getinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md)|Devuelve información acerca de un seguimiento especificado o de todas los seguimientos existentes.|  
|[sp_trace_create &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)|Crea una definición de seguimiento. El nuevo seguimiento estará en estado de detención.|  
|[sp_trace_generateevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)|Crea un evento definido por el usuario.|  
|[sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)|Agrega o quita una clase de evento o columna de datos de un seguimiento.|  
|[sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)|Inicia, detiene o cierra un seguimiento.|  
|[sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md)|Devuelve información acerca de los filtros que se aplicaron a un seguimiento.|  
|[sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)|Aplica un filtro nuevo o modificado a un seguimiento.|  
  
 **Para definir su propio seguimiento mediante procedimientos almacenados**  
  
1.  Especifique los eventos que quiera capturar con **sp_trace_setevent**.  
  
2.  Especifique los filtros de eventos. Para obtener más información, vea [Establecer un filtro de seguimiento &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/set-a-trace-filter-transact-sql.md).  
  
3.  Especifique el destino de los datos de eventos capturados con **sp_trace_create**.  
  
 Para obtener un ejemplo de cómo usar los procedimientos almacenados de seguimiento, vea [Crear un seguimiento &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/create-a-trace-transact-sql.md).  
  
 **Para configurar los valores predeterminados de definición de seguimiento**  
  
 [SQL Server Profiler](../../tools/sql-server-profiler/set-trace-definition-defaults-sql-server-profiler.md)  
  
 **Para establecer las opciones predeterminadas de presentación de seguimiento**  
  
 [SQL Server Profiler](../../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md)  
  
 **Para crear un seguimiento**  
  
 [SQL Server Profiler](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
 [Transact-SQL](../../relational-databases/sql-trace/create-a-trace-transact-sql.md)  
  
 **Para agregar o quitar eventos de una plantilla de seguimiento**  
  
 [SQL Server Profiler](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
  
 [Transact-SQL](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  