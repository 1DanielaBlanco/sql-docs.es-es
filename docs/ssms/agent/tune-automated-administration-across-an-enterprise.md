---
title: Optimizar la administración automatizada en una empresa | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- performance [SQL Server], automated administration
- tuning automated administration [SQL Server]
- monitoring performance [SQL Server], automated administration
ms.assetid: 671fed35-3859-4b0d-8f38-4dd07436857e
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 4a4623b604e052f9e98e3f1897a97afa8bedabd7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47745353"
---
# <a name="tune-automated-administration-across-an-enterprise"></a>Optimizar la administración automatizada en una empresa
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> En [Instancia administrada de Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la mayoría de las características de agente SQL Server son compatibles actualmente, aunque no todas. Vea [Diferencias de T-SQL en Instancia administrada de Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent) para obtener más información.

La administración multiservidor con el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de Microsoft aprovecha las características de optimización automática de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Por tanto, en condiciones normales no es necesaria la optimización adicional de trabajos. Sin embargo, la carga de red aumenta al ejecutar trabajos, generar alertas y notificar operadores. Puede optimizar la administración automatizada en una empresa para minimizar el tráfico de red que causan estas actividades.  
  
## <a name="see-also"></a>Ver también  
[Supervisar el rendimiento del motor de flujo de datos](../../integration-services/performance/performance-counters.md)  
  
