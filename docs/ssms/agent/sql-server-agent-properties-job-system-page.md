---
title: "Propiedades de Agente SQL Server (página Sistema de trabajo) | Microsoft Docs"
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
- sql13.ag.agent.job.f1
ms.assetid: e171d13e-1302-4f0e-88be-67d656aec8d3
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4d98026d219c3cfc834b96b0d7b5a402622df1be
ms.contentlocale: es-es
ms.lasthandoff: 06/22/2017

---
# <a name="sql-server-agent-properties-job-system-page"></a>Propiedades de Agente SQL Server (página Sistema de trabajo)
Utilice esta página para ver y modificar la forma en que el servicio Agente [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] administra los trabajos.  
  
## <a name="options"></a>Opciones  
**Intervalo de tiempo de espera de cierre (en segundos)**  
Especifica el número de segundos que el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] espera a que los trabajos finalicen antes del cierre. Si el trabajo sigue en ejecución después del intervalo especificado, el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] detendrá de manera obligatoria el trabajo.  
  
**Usar una cuenta de proxy de usuarios que no sean administradores**  
Establece una cuenta de proxy de usuarios que no sean administradores para el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] . [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)] y las versiones posteriores admiten varios servidores proxy; por tanto, esta opción solo es aplicable al administrar versiones del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] anteriores a [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)].  
  
**Nombre de usuario.**  
Escriba el nombre del usuario de la cuenta proxy de usuarios que no sean administradores. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] admite varios servidores proxy; por tanto, esta opción solo es aplicable al administrar versiones del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] anteriores a [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)].  
  
**Contraseña**  
Escriba la contraseña del usuario de la cuenta proxy de usuarios que no sean administradores. [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)] y las versiones posteriores admiten varios servidores proxy; por tanto, esta opción solo es aplicable al administrar versiones del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] anteriores a [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)].  
  
**Dominio**  
Escriba el dominio del usuario de la cuenta proxy de usuarios que no sean administradores. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] admite varios servidores proxy; por tanto, esta opción solo es aplicable al administrar versiones del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] anteriores a [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)].  
  
## <a name="see-also"></a>Vea también  
[Implementar trabajos](../../ssms/agent/implement-jobs.md)  
  

