---
title: Configurar registros de errores del Agente SQL Server (página General) | Microsoft Docs
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
- sql13.ag.errorlog.configure.f1
ms.assetid: e08de622-6f87-470c-aee0-b2d6cb6cca88
caps.latest.revision: ''
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 813a6a89e211bd3b524b80ddf12113b6e52a817d
ms.sourcegitcommit: 34766933e3832ca36181641db4493a0d2f4d05c6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="configure-sql-server-agent-error-logs-general-page"></a>Configurar registros de errores del Agente SQL Server (página General)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> En [Instancia administrada de Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la mayoría de las características de agente SQL Server son compatibles actualmente, aunque no todas. Vea [Diferencias de T-SQL en Instancia administrada de Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent) para obtener más información.

Utilice esta pantalla para ver y actualizar la configuración del registro de errores del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
## <a name="options"></a>.  
**Archivo de registro de errores**  
Especifique el archivo en el que el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] escribe los registros de errores.  
  
**...**  
Permite buscar el archivo del registro de errores.  
  
**Escribir registro de errores OEM**  
Escribe el archivo de registro de errores como un archivo no Unicode. De esta forma, se reduce el espacio en disco que utiliza el archivo de registro. Sin embargo, si se habilita esta opción, puede resultar más difícil leer los mensajes que incluyen datos Unicode.  
  
**Errores**  
Solo escribe errores y mensajes informativos en el archivo de registro.  
  
**Advertencias**  
Solo escribe advertencias y mensajes informativos en el archivo de registro.  
  
**Información**  
Solo escribe mensajes informativos en el archivo de registro.  
  
## <a name="see-also"></a>Ver también  
[Registro de errores del Agente SQL Server](../../ssms/agent/sql-server-agent-error-log.md)  
  
