---
title: "Réplica de disponibilidad desconectada | Microsoft Docs"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.swb.agdashboard.arp2connected.issues.f1
helpviewer_keywords: Availability Groups [SQL Server], policies
ms.assetid: 1a2162d3-54fb-4356-b349-effbdc15a5a4
caps.latest.revision: "12"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c81fc6a1851792d62ed947d88591675eeeed5366
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="availability-replica-is-disconnected"></a>Réplica de disponibilidad desconectada
    
## <a name="introduction"></a>Introducción  
  
|||  
|-|-|  
|**Nombre de directiva**|Estado de conexión de la réplica de disponibilidad|  
|**Problema**|La réplica de disponibilidad está desconectada.|  
|**Categoría**|**Crítico**|  
|**Faceta**|Réplica de disponibilidad|  
  
## <a name="description"></a>Descripción  
 Esta directiva comprueba el estado de conexión entre las réplicas de disponibilidad. La directiva está en mal estado cuando el estado de conexión de la réplica de disponibilidad es DISCONNECTED. De lo contrario, la directiva está en un estado correcto.  
  
> [!NOTE]  
>  Para esta versión de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], la información sobre las posibles causas y soluciones se encuentra en el artículo [Réplica de disponibilidad desconectada](http://go.microsoft.com/fwlink/p/?LinkId=220857) en TechNet Wiki.  
  
## <a name="possible-causes"></a>Posibles causas  
 La réplica secundaria no está conectada a la réplica principal. El estado de conexión es DISCONNECTED. Este problema puede deberse a lo siguiente:  
  
-   El puerto de conexión puede estar en conflicto con otra aplicación.  
  
-   El tipo de cifrado o el algoritmo no coinciden.  
  
-   Se ha eliminado o no se ha iniciado el extremo de la conexión.  
  
-   El transporte está desconectado.  
  
## <a name="possible-solutions"></a>Soluciones posibles  
 Las siguientes son posibles soluciones para este problema:  
  
-   Compruebe la configuración del extremo de creación de reflejo de la base de datos para las instancias de la réplica principal y secundaria, y actualice la configuración que no coincide.  
  
-   Compruebe si el puerto está en conflicto y, si en ese caso, cambie el número de puerto.  
  
## <a name="see-also"></a>Vea también  
 [Información general de los grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Usar el Panel AlwaysOn &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
