---
title: Grupo de disponibilidad no preparado para conmutación automática por error | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.agdashboard.agp3autofailover.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 28261014-342c-442a-bd89-6d04b8d4e8b7
caps.latest.revision: 10
author: rothja
ms.author: jroth
manager: jhubbard
ms.openlocfilehash: b06939bd2c4581ee224f1cdbe00a41062036b572
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36196990"
---
# <a name="availability-group-is-not-ready-for-automatic-failover"></a>Grupo de disponibilidad no preparado para conmutación automática por error
    
## <a name="introduction"></a>Introducción  
  
|||  
|-|-|  
|**Nombre de directiva**|Preparación para la conmutación automática por error del grupo de disponibilidad|  
|**Problema**|Grupo de disponibilidad no preparado para conmutación automática por error.|  
|**Categoría**|**Crítico**|  
|**Faceta**|grupo de disponibilidad|  
  
## <a name="description"></a>Descripción  
 Esta directiva realiza comprobaciones para asegurarse de que el grupo de disponibilidad tenga al menos una réplica secundaria que esté preparada para la conmutación por error. La directiva está en mal estado y se genera una alerta cuando el modo de conmutación por error de la réplica principal es automático, pero ninguna de las réplicas secundarias del grupo de disponibilidad están listas para la conmutación por error.  
  
 La directiva está en un estado correcto cuando al menos una réplica secundaria está lista para la conmutación automática por error.  
  
> [!NOTE]  
>  En esta versión de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], la información sobre las posibles causas y soluciones se encuentra en el artículo [El grupo de disponibilidad no está listo para la conmutación automática por error](http://go.microsoft.com/fwlink/p/?LinkId=220851) en TechNet Wiki.  
  
## <a name="possible-causes"></a>Posibles causas  
 Grupo de disponibilidad no preparado para la conmutación automática por error. La réplica principal está configurada para la conmutación automática por error; sin embargo, la réplica secundaria no está lista para la conmutación automática por error. La réplica secundaria configurada para la conmutación automática por error podría no estar disponible o su estado de sincronización de datos no es actualmente SYNCHRONIZED.  
  
## <a name="possible-solutions"></a>Soluciones posibles  
 Las siguientes son posibles soluciones para este problema:  
  
-   Compruebe que al menos una réplica secundaria está configurada como conmutación automática por error. Si no hay una réplica secundaria configurada como conmutación automática por error, actualice la configuración de una réplica secundaria para que sea el destino de la conmutación automática por error con confirmación sincrónica.  
  
-   Use la directiva para comprobar que los datos están en un estado de sincronización y el destino de la conmutación automática por error es SYNCHRONIZED y, a continuación, resuelva el problema en la réplica de disponibilidad.  
  
## <a name="see-also"></a>Vea también  
 [Información general de los grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Usar el Panel de AlwaysOn &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  