---
title: SQL Errors (objeto de SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Errors object
- SQLServer:SQL Errors
ms.assetid: 6e5273ca-29cb-4618-88a2-70b9b8d6cf76
caps.latest.revision: 14
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0adbd6be8ec228f9f12c205d5aadd5b45ee9ff4c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="sql-server-sql-errors-object"></a>SQL Errors (objeto de SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  El objeto **SQLServer:SQL Errors** de Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proporciona contadores para supervisar los **errores de SQL**.  
  
 En esta tabla se describen los contadores de los [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **errores de SQL** .  
  
|Contadores de errores de SQL de SQL Server|Description|  
|------------------------------------|-----------------|  
|**Errores/seg.**|Número de errores/seg.|  
  
 Cada contador del objeto contiene las instancias siguientes:  
  
|Elemento|Definición|  
|----------|----------------|  
|**_Total**|Información sobre todos los errores.|  
|**DB Offline Errors**|Hace un seguimiento de los errores graves que hacen que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deje sin conexión la base de datos actual.|  
|**Info Errors**|Información relacionada con los mensajes de error que proporcionan información a los usuarios pero no causan errores.|  
|**Kill Connection Errors**|Hace un seguimiento de los errores graves que hacen que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] elimine la conexión actual.|  
|**User Errors**|Información sobre los errores de usuario.|  
  
## <a name="see-also"></a>Ver también  
 [Supervisar el uso de recursos&#40;Monitor de sistema&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
