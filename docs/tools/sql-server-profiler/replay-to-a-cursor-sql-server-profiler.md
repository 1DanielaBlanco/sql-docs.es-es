---
title: "Reproducir hasta un cursor (SQL Server Profiler) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "reproducir cursores"
  - "seguimientos [SQL Server], reproducir"
  - "reproducir seguimientos"
ms.assetid: 89eadc41-4424-4a1c-ba61-0b52c851cdb1
caps.latest.revision: 22
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 22
---
# Reproducir hasta un cursor (SQL Server Profiler)
  En este tema se describe cómo reproducir archivos o tablas de seguimiento que se ponen en pausa al alcanzar un cursor mediante el [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. La pausa de seguimientos en cursores es compatible con la depuración porque la reproducción de scripts de seguimiento largos se puede dividir en segmentos cortos que se pueden analizar de forma incremental.  
  
### Para reproducir hasta el cursor  
  
1.  Abra el archivo o la tabla de seguimiento que desea reproducir. Para obtener más información, vea [Abrir un archivo de seguimiento &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) o [Abrir una tabla de seguimiento &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md).  
  
     Asegúrese de que el archivo o la tabla de seguimiento que abre contiene las clases de evento necesarias para la reproducción. Para más información, consulte [Replay Requirements](../../tools/sql-server-profiler/replay-requirements.md).  
  
2.  En la ventana de seguimiento, haga clic en un evento.  
  
3.  En el menú **Reproducir** , haga clic en **Ejecutar hasta el cursor**y, a continuación, conéctese al servidor en el que desea reproducir el seguimiento.  
  
4.  Compruebe la configuración en el cuadro de diálogo **Configuración de reproducción** y haga clic en **Aceptar**.  
  
     Se inicia la reproducción, que se pone en pausa al alcanzar el primer cursor.  
  
5.  Presione F5 para reanudar el seguimiento.  
  
6.  Repita el paso 5 hasta el final del seguimiento.  
  
## Vea también  
 [Reproducir hasta un punto de interrupción &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/replay-to-a-breakpoint-sql-server-profiler.md)   
 [Reproducir seguimientos](../../tools/sql-server-profiler/replay-traces.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  