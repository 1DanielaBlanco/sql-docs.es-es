---
title: Filtrar los Id. de proceso de servidor (SPID) en un seguimiento (SQL Server Profiler) | Documentos de Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: sql-server-profiler
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- filters [SQL Server], traces
- filters [SQL Server], SPIDs
- traces [SQL Server], filters
ms.assetid: f5945c39-be6b-4632-91cb-92066c80e188
caps.latest.revision: "25"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b113e50edcd72ff72717cae44166817478c959b9
ms.sourcegitcommit: 34d3497039141d043429eed15d82973b18ad90f2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2018
---
# <a name="filter-server-process-ids-spids-in-a-trace-sql-server-profiler"></a>Filtrar los Id. de proceso de servidor (SPID) en un seguimiento (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Este tema describe cómo filtrar identificadores de proceso de servidor (SPID) en un seguimiento mediante [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-filter-system-ids-in-a-trace"></a>Para filtrar identificadores de sistema en un seguimiento  
  
1.  En el menú **Archivo** , haga clic en **Nuevo seguimiento**y, a continuación, conéctese a una instancia de SQL Server.  
  
     Aparecerá el cuadro de diálogo **Propiedades de seguimiento** .  
  
    > [!NOTE]  
    >  Si **iniciar la traza inmediatamente tras realizar la conexión** está activada, el **propiedades de seguimiento** no aparecerá el cuadro de diálogo y en su lugar, se iniciará el seguimiento. Para desactivar esta configuración, en la **herramientas** menú, haga clic en **opciones**y desactive el **iniciar la traza inmediatamente tras realizar la conexión** casilla de verificación.  
  
2.  En el cuadro **Nombre de seguimiento** , escriba un nombre para el seguimiento.  
  
3.  En el **usar la plantilla** , seleccione una plantilla de seguimiento.  
  
4.  Opcionalmente, especifique una tabla o un archivo de destino donde guardar los resultados del seguimiento.  
  
5.  En el **selección de eventos** , haga clic en el **SPID** encabezado de columna para iniciar la **Editar filtro** cuadro de diálogo. También puede hacer clic con el botón derecho en el encabezado de la columna y seleccionar **Editar filtro de columna**. Si no aparece la columna **SPID** , active la casilla **Mostrar todas las columnas** .  
  
6.  En el cuadro de diálogo **Editar filtro** , expanda el operador de comparación adecuado y especifique un SPID como valor para la comparación.  
  
## <a name="see-also"></a>Vea también  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
