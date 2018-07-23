---
title: Usar objetos de rendimiento | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, monitoring
- SQL Server Agent service, monitoring
- SQL Server Agent service, performance objects
- SQL Server Agent, performance objects
- performance objects [SQL Server Agent]
- monitoring [SQL Server], SQL Server Agent
- monitoring [SQL Server Agent]
- performance counters [SQL Server], SQL Server Agent
- counters [SQL Server], SQL Server Agent
ms.assetid: 830b843a-6b2a-4620-a51b-98358e9fc54b
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 01d245a9ac6eb32bd38978bd2ed4189f774332ca
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/12/2018
ms.locfileid: "38982417"
---
# <a name="use-performance-objects"></a>Usar objetos de rendimiento
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> En [Instancia administrada de Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la mayoría de las características de agente SQL Server son compatibles actualmente, aunque no todas. Vea [Diferencias de T-SQL en Instancia administrada de Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent) para obtener más información.

[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] El Agente incluye objetos y contadores de rendimiento para supervisar el rendimiento del servicio. Estos objetos de rendimiento le permiten utilizar el Monitor de rendimiento, una herramienta de Windows, para identificar las actividades que realiza el servicio Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] en segundo plano. Por ejemplo, puede identificar cuántos trabajos activos ejecuta actualmente el servicio Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] para identificar los trabajos bloqueados.  
  
Hay objetos y contadores de rendimiento del servicio Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] para cada instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] instalada en el equipo. La denominación que adoptan los objetos de rendimiento depende de la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] que representa cada uno de ellos.  
  
La tabla siguiente muestra cómo se denominan los objetos de rendimiento del servicio Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] :  
  
|Tipo de instancia|Nombre del objeto|  
|-----------------|---------------|  
|Valor predeterminado|**SQLAgent:***objeto*:*número*|  
|Con nombre|**SQLAgent$**<br /> **&#42;nombre_de_instancia&#42; :***objeto*:*número*|  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] incluye los siguientes objetos de rendimiento para el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
|Nombre del objeto|Descripción|  
|---------------|---------------|  
|[SQLAgent:Jobs](http://msdn.microsoft.com/225b5e2d-4a78-4178-b2b6-b419df83c4aa)|Información de rendimiento acerca de trabajos que se han iniciado, tasas de éxito y estado actual|  
|[SQLAgent:JobSteps](http://msdn.microsoft.com/44f9983c-1753-4fe0-8475-973aa2460b3a)|Información de estado acerca de pasos de trabajos|  
|[SQLAgent:Alerts](http://msdn.microsoft.com/e5e37f74-ee88-46d0-ad8f-71fd1b1fa64a)|Información acerca del número de alertas y notificaciones|  
|[SQLAgent:Statistics](http://msdn.microsoft.com/ebe92bfa-0721-48aa-9ba6-e7904ad265a1)|Información general de rendimiento|  
  
## <a name="see-also"></a>Ver también  
[Supervisión y optimización del rendimiento](http://msdn.microsoft.com/87f23f03-0f19-4b2e-bfae-efa378f7a0d4)  
[Cómo iniciar el Monitor de sistema (Windows)](http://msdn.microsoft.com/5e51bb79-5737-470b-9c47-fac330c001c5)  
  
