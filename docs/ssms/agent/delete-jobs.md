---
title: Eliminar trabajos | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: delete jobs
ms.assetid: bffb915e-bc84-4417-aa35-183243ca3312
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a9badc23a8ca3c438fb70672e8ca8d477fedf7f5
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="delete-jobs"></a>Eliminar trabajos
Un trabajo es una serie específica de operaciones que el Agente SQL Server realiza secuencialmente. De forma predeterminada, los trabajos no se eliminan cuando finaliza la ejecución. Puede eliminar uno o más trabajos del Agente [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] independientemente del éxito o del fracaso del trabajo. También puede configurar el Agente [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] para que elimine los trabajos automáticamente cuando se realizan correctamente, con error o se completan.  
  
De forma predeterminada, los miembros del rol fijo de servidor **sysadmin** pueden ejecutar el procedimiento almacenamiento del sistema [sp_delete_job (Transact-SQL)](http://msdn.microsoft.com/en-us/b85db6e4-623c-41f1-9643-07e5ea38db09) para eliminar un trabajo. Al resto de usuarios se les debe conceder uno de los siguientes roles fijos de base de datos del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] en la base de datos **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
Para detalles sobre los permisos de estos roles, consulte [Roles fijos de base de datos del Agente SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
Los miembros del rol fijo de servidor **sysadmin** pueden ejecutar **sp_delete_job** para eliminar cualquier trabajo. Un usuario que no sea miembro del rol fijo de servidor **sysadmin** solo puede eliminar los trabajos de los que sea propietario.  
  
## <a name="related-tasks"></a>Tareas relacionadas  
  
|||  
|-|-|  
|**Description**|**Tema**|  
|Describe cómo eliminar uno o varios de los trabajos del Agente [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .|[Eliminar uno o más trabajos](../../ssms/agent/delete-one-or-more-jobs.md)|  
|Describe cómo configurar el Agente [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] para que elimine los trabajos automáticamente cuando se realizan correctamente, con error o se completan.|[Automatically Delete a Job](../../ssms/agent/automatically-delete-a-job.md)|  
  
