---
title: 'Propiedades del trabajo: Nuevo trabajo (página General) | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.ag.job.general.f1
ms.assetid: b6832840-1c18-4db8-94fc-080db880ae9f
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 968a5efa89f2e75d1e41240712f66c48b07e352b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="job-properties---new-job-general-page"></a>Propiedades del trabajo - Nuevo trabajo (página General)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> En [Instancia administrada de Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la mayoría de las características de agente SQL Server son compatibles actualmente, aunque no todas. Vea [Diferencias de T-SQL en Instancia administrada de Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent) para obtener más información.

Use esta página para ver y modifica las propiedades generales de un trabajo del Agente [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
## <a name="options"></a>Opciones  
**Nombre**  
Cambie el nombre del trabajo.  
  
**Propietario**  
Seleccione el propietario del trabajo.  
  
**Categoría**  
Seleccione la categoría del trabajo.  
  
**...**  
Muestra los trabajos de la categoría seleccionada.  
  
**Descripción**  
Cambie la descripción del trabajo.  
  
**Enabled**  
Habilita el trabajo. Si el trabajo no está habilitado, no se ejecuta como respuesta a una programación o una alerta; sin embargo, puede iniciarlo con el procedimiento almacenado **sp_start_job** .  
  
**Source**  
Muestra el servidor maestro del trabajo. Solo está disponible en la página **Job PropertiesGeneral** .  
  
**Creado**  
Muestra la fecha y la hora de creación del trabajo. Solo está disponible en la página **Job PropertiesGeneral** .  
  
**Modificado por última vez**  
Muestra la fecha y la hora de la última modificación del trabajo. Solo está disponible en la página **Job PropertiesGeneral** .  
  
**Ejecutado por última vez**  
Muestra la fecha y la hora del inicio de la última ejecución del trabajo. Solo está disponible en la página **Job PropertiesGeneral** .  
  
**Ver historial de trabajos**  
Muestra el historial de trabajos. Solo está disponible en la página **Job PropertiesGeneral** .  
  
## <a name="see-also"></a>Ver también  
[Implementar trabajos](../../ssms/agent/implement-jobs.md)  
[Categorías de trabajo - Administrar categorías de trabajo](../../ssms/agent/job-categories-manage-job-categories.md)  
  
