---
title: Ver actividad de trabajo | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- viewing job activity
- jobs [SQL Server Agent], viewing
- SQL Server Agent jobs, viewing
- displaying job activity
ms.assetid: 5c284e5e-7775-435d-ac49-f3f12a27ddc7
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 48c5a7cff0b48fa137d6c39d4e08b1cf713d88f2
ms.contentlocale: es-es
ms.lasthandoff: 06/22/2017

---
# <a name="view-job-activity"></a>Ver actividad de trabajo
En este tema se describe cómo ver el estado de ejecución de los trabajos del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] en [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] o [!INCLUDE[tsql](../../includes/tsql_md.md)].  
  
Cuando se inicia el servicio del Agente [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , se crea una nueva sesión y la tabla **sysjobactivity** de la base de datos **msdb** se rellena con todos los trabajos definidos que existen. En esta tabla se registra la actividad y el estado actuales de los trabajos. Puede utilizar el Monitor de actividad de trabajo del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] para ver el estado actual de los trabajos. Si el servicio del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] finaliza inesperadamente, puede consultar la tabla **sysjobactivity** para ver qué trabajos se estaban ejecutando cuando finalizó el servicio.  
  
**En este tema**  
  
-   **Antes de empezar:**  
  
    [Seguridad](#Security)  
  
-   **Para ver la actividad de los trabajos, utilizando:**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
## <a name="before-you-begin"></a>Antes de comenzar  
  
### <a name="Security"></a>Seguridad  
Para obtener información detallada, vea [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Usar SQL Server Management Studio  
  
#### <a name="to-view-job-activity"></a>Para ver la actividad de los trabajos  
  
1.  En el **Explorador de objetos**, conéctese a una instancia del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]y, a continuación, expándala.  
  
2.  Expanda **Agente SQL Server**.  
  
3.  Haga clic con el botón derecho en **Monitor de actividad de trabajo** y, luego, haga clic en **Ver actividad de trabajo**.  
  
4.  En el **Monitor de actividad de trabajo**, puede ver los detalles de cada trabajo definido para este servidor.  
  
5.  Haga clic con el botón secundario en un trabajo para iniciarlo, detenerlo, habilitarlo o deshabilitarlo, actualizar el estado que se muestra en el Monitor de actividad de trabajo, eliminarlo o ver su historial o sus propiedades.  Para iniciar, detener, habilitar o deshabilitar, o actualizar varios trabajos, seleccione varias filas en el Monitor de actividad de trabajo y haga clic con el botón secundario en la selección.  
  
6.  Para actualizar el Monitor de actividad de trabajo, haga clic en **Actualizar**. Para ver menos filas, haga clic en **Filtro** y escriba los parámetros del filtro.  
  
## <a name="TSQL"></a>Usar Transact-SQL  
  
#### <a name="to-view-job-activity"></a>Para ver la actividad de los trabajos  
  
1.  En el **Explorador de objetos**, conéctese a una instancia del [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  En la barra de Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue el siguiente ejemplo en la ventana de consulta y haga clic en **Ejecutar**.  
  
    ```  
    -- lists activity for all jobs that the current user has permission to view.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_jobactivity ;  
    GO  
    ```  
  
Para más información, consulte [sp_help_jobactivity (Transact-SQL)](http://msdn.microsoft.com/en-us/d344864f-b4d3-46b1-8933-b81dec71f511).  
  

