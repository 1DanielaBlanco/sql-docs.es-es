---
title: 'Grupos de disponibilidad AlwaysOn: interoperabilidad (SQL Server) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Availability Groups [SQL Server], about
- Availability Groups [SQL Server], interoperability
ms.assetid: daf87f90-2623-42ca-912c-b8f07d210510
caps.latest.revision: 18
author: rothja
ms.author: jroth
manager: jhubbard
ms.openlocfilehash: e7a8ea0a461bb261b8a85769b0fe2048e6cc569c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36201017"
---
# <a name="always-on-availability-groups-interoperability-sql-server"></a>Grupos de disponibilidad AlwaysOn: interoperabilidad (SQL Server)
  En este tema se documenta la interoperabilidad de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] con otras características de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  

  
##  <a name="Interop"></a> Características que interoperan con grupos de disponibilidad AlwaysOn  
 En la tabla siguiente se enumeran las características de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que interoperan con [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] en [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Los vínculos de la columna **Más información** indican que existen consideraciones de interoperabilidad sobre una determinada característica.  
  
|Característica|Más información|  
|-------------|----------------------|  
|captura de datos modificados|[Replicación, seguimiento de cambios, captura de datos modificados y grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](replicate-track-change-data-capture-always-on-availability.md)|  
|seguimiento de cambios|[Replicación, seguimiento de cambios, captura de datos modificados y grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](replicate-track-change-data-capture-always-on-availability.md)|  
|Bases de datos independientes|[Bases de datos independientes con grupos de disponibilidad AlwaysOn (SQL Server)](always-on-availability-groups-sql-server.md)|  
|Clave de cifrado de la base de datos|[Cifrado de bases de datos con grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](encrypted-databases-with-always-on-availability-groups-sql-server.md)|  
|Instantáneas de base de datos|[Base de datos de instantáneas con grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](database-snapshots-with-always-on-availability-groups-sql-server.md)|  
|FILESTREAM y FileTable|[FILESTREAM y FileTable con grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](filestream-and-filetable-with-always-on-availability-groups-sql-server.md)|  
|Búsqueda de texto completo|Nota: Los índices de texto completo se sincronizan con las bases de datos secundarias AlwaysOn.|  
|Trasvase de registros|[Requisitos previos para la migración de trasvase de registros a grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)|  
|Almacén remoto de blobs (RBS)|[Almacén remoto de blobs &#40;RBS&#41; y grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](remote-blob-store-rbs-and-always-on-availability-groups-sql-server.md)|  
|Replicación[configurar la replicación para grupos de disponibilidad AlwaysOn (SQL Server)](configure-replication-for-always-on-availability-groups-sql-server.md)<br /><br /> [Mantener una base de datos de publicación AlwaysOn &#40;SQL Server&#41;](maintaining-an-always-on-publication-database-sql-server.md)<br /><br /> [Replicación, seguimiento de cambios, captura de datos modificados y grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](replicate-track-change-data-capture-always-on-availability.md)<br /><br /> [Los suscriptores de replicación y grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](replication-subscribers-and-always-on-availability-groups-sql-server.md)|  
|Analysis Services|[Analysis Services con grupos de disponibilidad AlwaysOn](analysis-services-with-always-on-availability-groups.md)|  
|Reporting Services|Use réplicas secundarias de solo lectura como un origen de datos de notificación y reduzca la carga en la réplica de lectura-escritura principal.<br /><br /> [Reporting Services con grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](reporting-services-with-always-on-availability-groups-sql-server.md)|  
|Service Broker|[Service Broker con grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](service-broker-with-always-on-availability-groups-sql-server.md)|  
|Agente SQL Server||  
  
##  <a name="NoInterop"></a> Características que no interoperan con grupos de disponibilidad AlwaysOn  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] no interopera con las siguientes características:  
  
-   Transacciones entre bases de datos y transacciones distribuidas  
  
     Si quiere saber por qué no se admiten estas transacciones, vea [Transacciones entre bases de datos no compatibles para la creación de reflejo de la base de datos o grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](transactions-always-on-availability-and-database-mirroring.md).  
  
-   Creación de reflejo de base de datos  
  
##  <a name="RelatedContent"></a> Contenido relacionado  
  
-   **Blogs:**  
  
     [Guía de migración: migrar a clústeres de conmutación por error y grupos de disponibilidad de SQL Server 2012 desde implementaciones anteriores de agrupación en clústeres y creación de reflejo](http://blogs.msdn.com/b/sqlalwayson/archive/2012/04/09/now-available-migration-guide-migrating-to-sql-server-2012-failover-clustering-and-availability-groups-from-prior-clustering-and-mirroring-deployments.aspx)  
  
     [Blogs del equipo de AlwaysOn SQL Server: El Blog oficial del SQL Server AlwaysOn equipo](http://blogs.msdn.com/b/sqlalwayson/)  
  
     [Blogs de los ingenieros de SQL Server de CSS](http://blogs.msdn.com/b/psssql/)  
  
-   **Notas del producto:**  
  
     [Guía de migración: Migrar a grupos de disponibilidad AlwaysOn desde implementaciones anteriores que combinan creación de reflejo de la base de datos y trasvase de registros](http://msdn.microsoft.com/library/jj635217)  
  
     [Guía de soluciones de Microsoft SQL Server AlwaysOn para alta disponibilidad y recuperación ante desastres](http://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [Notas del producto de Microsoft para SQL Server 2012](http://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Notas del producto del equipo de asesoramiento al cliente de SQL Server](http://sqlcat.com/)  
  
## <a name="see-also"></a>Vea también  
 [Información general de los grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Requisitos previos, restricciones y recomendaciones para grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)  
  
  