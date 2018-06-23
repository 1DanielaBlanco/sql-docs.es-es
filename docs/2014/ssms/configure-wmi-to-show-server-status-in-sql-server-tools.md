---
title: Configurar WMI para mostrar el estado del servidor en Herramientas de SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WMI Provider for Server Events, setting permissions
- WMI permissions [SQL Server]
ms.assetid: 7e97197b-ed4d-40d1-9a52-9ab1d92401d7
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d07c3fe77b0f371e6f01b0546c8fa9615e8bde32
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36112379"
---
# <a name="configure-wmi-to-show-server-status-in-sql-server-tools"></a>Configurar WMI para mostrar el estado del servidor en Herramientas de SQL Server
  En este tema se describe cómo configurar WMI para mostrar el estado del servidor en herramientas de SQL Server en [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Al conectarse a los servidores, los componentes Servidores registrados y Explorador de objetos de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], así como el Administrador de configuración de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , usan Instrumental de administración de Windows (WMI) para obtener el estado de los servicios de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (MSSQLSERVER) y el Agente [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (MSSQLSERVER). Para mostrar el estado del servicio, el usuario debe tener derechos de acceso remoto al objeto WMI. El servidor debe tener WMI instalado para configurar este permiso.  
  
##  <a name="SSMSProcedure"></a> Para configurar los permisos de WMI  
  
1.  En el menú **Inicio** del servidor remoto, haga clic en **Ejecutar**.  
  
2.  En el **abiertos** cuadro, escriba `wmimgmt.msc`y, a continuación, haga clic en **Aceptar**.  
  
3.  En el programa **Windows Management Infrastructure** , haga clic con el botón derecho en **Control WMI (Local)** y, luego, haga clic en **Propiedades**.  
  
4.  En el cuadro de diálogo **Propiedades de Control WMI (Local)** , en la pestaña **Seguridad** , expanda **Raíz**y, luego, haga clic en **CIMV2**.  
  
5.  Haga clic en **Seguridad** para abrir el cuadro de diálogo **Seguridad para ROOT\CIMV2** .  
  
6.  Agregue un grupo o un usuario al cuadro **Nombres de grupos o usuarios** y selecciónelo.  
  
7.  En el **permisos para ***\<usuario o grupo >* cuadro, seleccione la **permitir** columna, para la **llamada remota habilitada** permiso para los usuarios a los que se va a forma remota detectar el estado del servicio.  
  
## <a name="see-also"></a>Vea también  
 [Iniciar, detener o pausar el servicio del Agente SQL Server](agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
  