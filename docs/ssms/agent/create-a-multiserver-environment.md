---
title: Crear un entorno multiservidor | Microsoft Docs
ms.custom: 
ms.date: 01/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent, multiserver environments
- master servers [SQL Server], about master servers
- target servers [SQL Server], about target servers
- multiserver environments [SQL Server]
ms.assetid: edc2b60d-15da-40a1-8ba3-f1d473366ee6
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: cd9eee1cd80634bd3472bcf4e948658eed3a60f2
ms.contentlocale: es-es
ms.lasthandoff: 04/11/2017

---
# <a name="create-a-multiserver-environment"></a>Crear un entorno multiservidor
La administración multiservidor requiere que se configure un servidor maestro (MSX) y uno o más servidores de destino (TSX). Los trabajos que se van a procesar en todos los servidores de destino se definen primero en el servidor maestro y luego se descargan en los servidores de destino.  
  
De forma predeterminada, el cifrado SSL (Capa de sockets seguros) y la validación de certificados completos se habilitan para las conexiones entre los servidores maestros y los servidores de destino. Para más información, [Establecer opciones de cifrado en servidores de destino](../../ssms/agent/set-encryption-options-on-target-servers.md).  
  
Si tiene un muchos servidores de destino, no defina el servidor maestro en un servidor de producción con requisitos de rendimiento elevados de otras funciones de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , ya que el tráfico del servidor de destino puede afectar negativamente al rendimiento del servidor de producción. Si también reenvía eventos a este servidor maestro dedicado, puede centralizar la administración en un servidor. Para más información, consulte [Administrar eventos](../../ssms/agent/manage-events.md).  
  
> [!NOTE]  
> Para usar el procesamiento de trabajos multiservidor, la cuenta de servicio del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] debe ser miembro del rol **TargetServersRole** de la base de datos **msdb** del servidor maestro. El Asistente para servidor maestro agrega automáticamente la cuenta de servicio a este rol como parte del proceso de alta.  
  
## <a name="considerations-for-multiserver-environments"></a>Consideraciones para entornos multiservidor  
  
Considere lo siguiente cuando cree un entorno multiservidor:  
  
-   Utilice la versión más reciente como servidor maestro. Se admiten dos las versiones anteriores y la actual.

-   Cada servidor de destino notifica únicamente a un servidor maestro. Para dar de alta un servidor de destino en otro servidor maestro, primero debe darlo de baja en el servidor maestro actual.  
  
-   Si desea cambiar el nombre de un servidor de destino, debe darlo de baja antes de cambiar el nombre y volver a darlo de alta después del cambio.  
  
-   Si desea anular una configuración multiservidor, debe dar de baja todos los servidores de destino del servidor maestro.  
  
-   SQL Server Integration Services solo admite servidores de destino que tengan la misma versión que el servidor maestro o una superior.  
  
## <a name="related-tasks"></a>Tareas relacionadas  
En los temas siguientes se presentan las tareas habituales para crear un entorno multiservidor.  
  
|Description|Tema|  
|---------------|---------|  
|Describe cómo crear un servidor maestro.|[Establecer un servidor maestro](../../ssms/agent/make-a-master-server.md)|  
|Describe cómo crear un servidor de destino.|[Establecer un servidor de destino](../../ssms/agent/make-a-target-server.md)|  
|Describe cómo dar de alta un servidor de destino en un servidor maestro.|[Dar de alta un servidor de destino en un servidor maestro](../../ssms/agent/enlist-a-target-server-to-a-master-server.md)|  
|Describe cómo dar de baja un servidor de destino en un servidor maestro.|[Dar de baja un servidor de destino desde un servidor maestro](../../ssms/agent/defect-a-target-server-from-a-master-server.md)|  
|Describe cómo dar de baja varios servidores de destino en un servidor maestro.|[Dar de baja varios servidores de destino desde un servidor maestro](../../ssms/agent/defect-multiple-target-servers-from-a-master-server.md)|  
|Describe cómo comprobar el estado de un servidor de destino.|[sp_help_targetserver (Transact-SQL)](http://msdn.microsoft.com/en-us/f841d3bd-901a-4980-ad0b-1c6eeba3f717)<br /><br />[sp_help_targetservergroup (Transact-SQL)](http://msdn.microsoft.com/en-us/ec3a4a68-b591-431c-9518-053ede522d0c)|  
  
## <a name="see-also"></a>Vea también  
[Solucionar problemas de trabajos multiservidor que usan servidores proxy](../../ssms/agent/troubleshoot-multiserver-jobs-that-use-proxies.md)  
  

