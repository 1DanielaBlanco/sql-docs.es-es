---
title: "Establecer la duración y el tiempo de inactividad de la CPU (SQL Server Management Studio) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CPU [SQL Server], idle conditions
- time [SQL Server], CPU idle and duration
- duration of CPU idle [SQL Server]
- SQL Server Agent, CPU idle conditions
- idle time [SQL Server]
ms.assetid: 8647b465-d899-4cc7-9640-134a506d0a2e
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4d4d86084f15df2934b95dce22a7f2e63c20bf6f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="set-cpu-idle-time-and-duration-sql-server-management-studio"></a>Establecer la duración y el tiempo de inactividad de la CPU (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] En este tema se explica cómo definir la condición de inactividad de la CPU para el servidor en [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]. La definición de inactividad de la CPU influye en la forma en que el Agente [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] responde a los eventos. Por ejemplo, supongamos que define la condición de inactividad de la CPU como el momento en que el uso de la CPU se sitúa por debajo del 10% y permanece en este nivel durante 10 minutos. En este caso, si ha definido trabajos que deben ejecutarse cuando la CPU del servidor alcance una condición de inactividad, estos trabajos se iniciarán cuando el uso de la CPU se sitúe por debajo del 10% y permanezca en este nivel durante 10 minutos. Si se trata de un trabajo que tiene consecuencias importantes sobre el rendimiento del servidor, es importante la forma en que define la condición de inactividad de la CPU.  
  
## <a name="SSMSProcedure"></a>Usar SQL Server Management Studio  
  
#### <a name="to-set-cpu-idle-time-and-duration"></a>Para establecer la duración y el tiempo de inactividad de la CPU  
  
1.  En el **Explorador de objetos** , conéctese a una instancia de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]y, después, expándala.  
  
2.  Haga clic con el botón derecho en el **Agente SQL Server**, haga clic en **Propiedades**y seleccione la página **Avanzadas** .  
  
3.  En **Condición de CPU inactiva**, haga lo siguiente:  
  
    -   Active la opción **Definir condición de CPU inactiva**.  
  
    -   Especifique un porcentaje para el cuadro **El promedio de uso de la CPU baja de** (para todas las CPU). Esto establece el nivel de uso por debajo del cual debe situarse la CPU para que se considere inactiva.  
  
    -   Especifique un número de segundos para el cuadro **Y permanece por debajo durante** . Esto establece la duración del uso mínimo de la CPU para que ésta se considere inactiva.  
  
