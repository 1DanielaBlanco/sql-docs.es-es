---
title: MSSQLSERVER_21892 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 21892 (Database Engine error)
ms.assetid: 199818e8-28f4-440e-ad85-7bea88f51153
caps.latest.revision: 6
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 3ce5f5c4d88232aee27695aae35bfcf55734497d
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver21892"></a>MSSQLSERVER_21892
  
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|SQL Server|  
|Identificador del evento|21892|  
|Origen del evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|SQLErrorNum21892|  
|Texto del mensaje|No se puede consultar sys.availability_replicas en el principal de grupo de disponibilidad asociado con el nombre de red virtual '%s' para los nombres de servidor de las réplicas de miembro: error = %d, mensaje de error = %s.',|  
  
## <a name="explanation"></a>Explicación  
**sp_validate_replica_hosts_as_publishers** consulta el principal actual del grupo de disponibilidad asociado al publicador redireccionado para determinar las instancias de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que hospedan las réplicas de miembro.  Cuando se produce un error en esta consulta, se devuelve el error 21892.  
  
**sp_validate_replica_hosts_as_publishers** se encuentra normalmente en el primer uso del servidor vinculado temporal por lo que, si hay problemas de conectividad, probablemente aparecerán primero con **sp_validate_replica_hosts_as_publishers**. A diferencia de **sp_validate_redirected_publisher**, el servidor vinculado que usa **sp_validate_replica_hosts_as_publishers** siempre emplea las credenciales del autor de la llamada al conectarse a cualquiera de los hosts de la réplica de grupo de disponibilidad.  
  
## <a name="user-action"></a>Acción del usuario  
Al ejecutar este procedimiento almacenado, asegúrese de que se ejecutar desde un inicio de sesión que sea válido en todas las réplicas. El inicio de sesión requiere autorización suficiente para consultar las tablas de metadatos del grupo de disponibilidad, así como para consultar las tablas de metadatos de suscripción en la réplica de base de datos del publicador.  
  
Examine el error de referencia original para determinar la causa del error y llevar a cabo la acción correctiva adecuada.  
  

