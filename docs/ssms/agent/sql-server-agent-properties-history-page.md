---
title: "Propiedades de Agente SQL Server (página Historial) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ag.agent.history.f1
ms.assetid: dc73734c-b3c3-407f-bbd1-8714b4fa47b0
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 51839ab3d459e2350c582810fe003fc5086de3eb
ms.contentlocale: es-es
ms.lasthandoff: 06/22/2017

---
# <a name="sql-server-agent-properties-history-page"></a>Propiedades de Agente SQL Server (página Historial)
Utilice esta página para ver y modificar los valores de configuración para administrar el registro del historial de servicios del Agente [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
## <a name="options"></a>Opciones  
**Limitar tamaño del registro de historial de trabajos**  
Establece los límites para la cantidad de información del historial de trabajos que el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] conserva en el registro.  
  
**Tamaño máximo del registro de historial de trabajos (filas)**  
Establece el número máximo de filas que conserva el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] . Cuando el registro crece para contener este número de filas, el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] elimina las filas más antiguas del registro a medida que se van incluyendo filas nuevas.  
  
**Máximo de filas de historial de trabajos por trabajo**  
Establece el número máximo de filas que el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] conserva por trabajo. Cuando el historial para un trabajo determinado crece para contener este número de filas, el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] quita las filas más antiguas del registro a medida que se van incluyendo filas nuevas.  
  
**Quitar historial del agente**  
Especifica que el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] quitará las entradas que han permanecido en el registro más tiempo que el especificado. Es una ejecución única para quitar el historial. Si es necesaria la repetición de un trabajo, cree y programe un plan de mantenimiento con un trabajo de limpieza.  
  
**Anterior a**  
Establece el tiempo que el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] conservará las entradas.  
  
## <a name="see-also"></a>Vea también  
[Registro de errores del Agente SQL Server](../../ssms/agent/sql-server-agent-error-log.md)  
  

