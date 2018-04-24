---
title: Elegir la cuenta del servicio del Agente para entornos multiservidor | Microsoft Docs
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
helpviewer_keywords:
- SQL Server Agent, service accounts
- multiserver environments [SQL Server], SQL Server Agent service account behavior
ms.assetid: a07e2f38-281c-495b-965b-13fad03ba548
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 93d4ebac4c42aa07ff6714c9d650145e425a3305
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="choose-the-right-sql-server-agent-service-account-for-multiserver-environments"></a>Elegir la cuenta correcta del servicio del Agente SQL Server para entornos multiservidor
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> En [Instancia administrada de Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la mayoría de las características de agente SQL Server son compatibles actualmente, aunque no todas. Vea [Diferencias de T-SQL en Instancia administrada de Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent) para obtener más información.

La cuenta de Windows que elija para el servicio del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] puede afectar al comportamiento de un entorno multiservidor, como se indica a continuación:  
  
-   Si ejecuta el servicio del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] en una cuenta que no sea miembro del grupo de administradores de Windows local, el alta de los servidores de destino en los servidores maestros puede generar un error. Si lo hace, se devuelve un mensaje de error que indica lo siguiente:  
  
    Error en la operación de alta.  
  
    Reinicie [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] y el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] para solucionar este problema.  
  
-   Cuando el servicio del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] se ejecuta en la cuenta del sistema local, las operaciones entre el servidor maestro y el servidor de destino solo se admiten si ambos servidores residen en el mismo equipo. Si usa esta configuración, verá el siguiente mensaje cuando dé de alta los servidores de destino en un servidor maestro:  
  
    "Comprobar que la cuenta de inicio del agente de *<nombre_equipo_servidor_destino>* posea derechos para iniciar la sesión como servidor de destino".  
  
    Puede omitir este mensaje informativo. La operación de alta debe finalizar correctamente.  
  
Para más información sobre cómo elegir una cuenta para el servicio del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , consulte [Seleccionar una cuenta para el servicio del Agente SQL Server](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md).  
  
