---
title: Validar una instalación de SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: install
ms.reviewer: ''
ms.suite: sql
ms.technology: install
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- validating installations [SQL Server]
ms.assetid: 1689af50-d2b8-4aa6-8f27-cc7127157fc8
caps.latest.revision: 31
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ad9dc7ac3ef4ec01a68a6544482122d9c0f371fb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="validate-a-sql-server-installation"></a>Validar una instalación de SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  
  El informe de detección de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se puede utilizar para comprobar la versión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y las características de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instaladas en el equipo. En el **Informe de detección de características instaladas de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** se muestra un informe de todos los productos y características de [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] y [!INCLUDE[ssSQL15](../../includes/sssqlv14-md.md)] que están instalados en el servidor local. El informe de detección de características de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] está disponible en la página **Herramientas** del Centro de instalación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 ## <a name="run-includessnoversionincludesssnoversion-mdmd-features-discovery-report"></a>Ejecutar el informe de detección de características de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
 Inicie el centro de instalación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; para ello, en el menú **Inicio**, seleccione **Todos los programas**, **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<nombre de la versión>**, **Herramientas de configuración** y haga clic en **Centro de instalación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**. Para ejecutar el informe de detección de características de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], haga clic en **Herramientas** en el área de navegación izquierda del **Centro de instalación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** y haga clic en **Informe de detección de características instaladas de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**.  
  
 El informe de detección de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se guarda en %ProgramFiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\*nnn*\Setup Bootstrap\Log\\<última sesión de instalación\>.  
  
 También puede generar el informe de detección a través de la línea de comandos. Ejecute "Setup.exe /Action=RunDiscovery" desde un símbolo del sistema. Si agrega "/q" a la línea de comandos anterior, no se mostrará ninguna IU, pero el informe se creará igualmente en %ProgramFiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\*nnn*\Setup Bootstrap\Log\\<última sesión de instalación\>.  
  
## <a name="see-also"></a>Vea también  
 [Ver y leer los archivos de registro de instalación de SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  
