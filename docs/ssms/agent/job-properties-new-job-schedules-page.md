---
title: 'Propiedades del trabajo: Nuevo trabajo (página Programaciones) | Microsoft Docs'
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
- sql13.ag.job.schedules.f1
ms.assetid: 0b03585b-a510-484d-8a63-9b32459def9c
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: e69e0df6afbc2dfec2df32d064f943b26b05a85b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="job-properties---new-job-schedules-page"></a>Propiedades del trabajo - Nuevo trabajo (página Programaciones)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> En [Instancia administrada de Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la mayoría de las características de agente SQL Server son compatibles actualmente, aunque no todas. Vea [Diferencias de T-SQL en Instancia administrada de Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent) para obtener más información.

Utilice esta página para ver y organizar las programaciones de un trabajo del Agente [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
## <a name="options"></a>Opciones  
**Lista de programaciones**  
Muestra las programaciones para este trabajo.  
  
**Nueva**  
Crea una nueva programación. Una vez que se haya creado la programación, ésta se agregará al trabajo.  
  
**Seleccionar**  
Selecciona una de las programaciones existentes. Puesto que un trabajo y una programación deben tener el mismo propietario, esta opción solo le permitirá seleccionar programaciones de su propiedad.  
  
**Editarar**  
Edita la programación seleccionada para cambiar las propiedades de programación del trabajo.  
  
**Quitar**  
Quita la programación seleccionada del trabajo. Si no hay otros trabajos que utilicen la programación, ésta se elimina de la base de datos.  
  
## <a name="see-also"></a>Ver también  
[Implementar trabajos](../../ssms/agent/implement-jobs.md)  
  
