---
title: Crear trabajos | Microsoft Docs
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
- jobs [SQL Server Agent], creating
- SQL Server Agent jobs, creating
ms.assetid: 465fb7fc-7622-4252-a178-ea51691c935b
caps.latest.revision: "3"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 757958d84086266fac8dac1585c45e5d9ac96a89
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="create-jobs"></a>Crear trabajos
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Un trabajo es una serie específica de operaciones que el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] realiza secuencialmente. Un trabajo puede realizar una amplia variedad de actividades, incluidos scripts [!INCLUDE[tsql](../../includes/tsql_md.md)] , aplicaciones de símbolo del sistema, scripts de Microsoft ActiveX, paquetes de Integration Services, comandos y consultas de Analysis Services o tareas de replicación. Los trabajos pueden ejecutar tareas repetitivas o que se pueden programar, y pueden notificar automáticamente a los usuarios el estado del trabajo mediante alertas, lo cual simplifica en gran medida la administración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
Para crear un trabajo, el usuario debe ser miembro de uno de los roles fijos de base de datos del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o del rol fijo de servidor **sysadmin** . Solo pueden editar el trabajo el propietario de éste o los miembros del rol **sysadmin** . Los miembros del rol **sysadmin** pueden asignar el valor de propiedad de trabajo a otros usuarios, y pueden ejecutar cualquier trabajo, independientemente del propietario del trabajo. Para más información sobre los roles fijos de base de datos del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , consulte [Roles fijos de base de datos del Agente SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
Se puede escribir un trabajo para que se ejecute en la instancia local de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o en varias instancias de una empresa. Para ejecutar trabajos en varios servidores, debe configurar al menos un servidor maestro, y uno o más servidores de destino. Para más información sobre los servidores maestros y de destino, consulte [Administración automatizada en una empresa](../../ssms/agent/automated-administration-across-an-enterprise.md).  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] El Agente registra la información del trabajo y de los pasos de trabajo en el historial de trabajos.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|||  
|-|-|  
|**Descripción**|**Tema**|  
|Describe cómo crear un trabajo del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .|[Crear un trabajo](../../ssms/agent/create-a-job.md)|  
|Describe cómo volver a asignar a otro usuario la propiedad de los trabajos del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .|[Give Others Ownership of a Job](../../ssms/agent/give-others-ownership-of-a-job.md)|  
|Describe cómo configurar el registro de historial de trabajos del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .|[Set Up the Job History Log](../../ssms/agent/set-up-the-job-history-log.md)|  
  
## <a name="see-also"></a>Ver también  
[Administrar pasos de trabajo](../../ssms/agent/manage-job-steps.md)  
[Administración automatizada en una empresa](../../ssms/agent/automated-administration-across-an-enterprise.md)  
[Crear y adjuntar programaciones a trabajos](../../ssms/agent/create-and-attach-schedules-to-jobs.md)  
[Ejecutar trabajos](../../ssms/agent/run-jobs.md)  
[Ver o modificar trabajos](../../ssms/agent/view-or-modify-jobs.md)  
  
