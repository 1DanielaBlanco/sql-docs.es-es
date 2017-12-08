---
title: "Cuentas de servicio (Asistente para la configuración de seguridad de la creación de reflejo de bases de datos) | Microsoft Docs"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: database-mirroring
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.swb.configdbmsecurwiz.serviceaccounts.f1
ms.assetid: d58d8f93-7888-4d66-af4d-969ef6a2dbee
caps.latest.revision: "34"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2e14ac303dd658c19e09083446dfd6fba95069ff
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2017
---
# <a name="service-accounts-configure-database-mirroring-security-wizard"></a>Cuentas de servicio (Asistente para la configuración de seguridad de la creación de reflejo de bases de datos)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Al utilizar la autenticación de Windows, si las instancias del servidor usan cuentas diferentes, especifique las cuentas de servicio para [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Estas cuentas de servicio deben ser cuentas de dominio (en el mismo dominio o en dominios de confianza).  
  
 Si todas las instancias del servidor utilizan la misma cuenta de dominio o la autenticación basada en certificados, deje los campos en blanco. Basta con hacer clic en **Finalizar**y el asistente configura automáticamente las cuentas en función de la cuenta del asistente actual.  
  
> [!IMPORTANT]  
>  Si los extremos de creación de reflejo de la base de datos de las instancias de servidor están configurados para usar certificados, debe dejar vacíos los campos de cuenta de servicio.  
  
 **Para configurar la creación de reflejo de la base de datos mediante SQL Server Management Studio**  
  
-   [Establecer una sesión de creación de reflejo de la base de datos mediante la autenticación de Windows &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/establish-database-mirroring-session-windows-authentication.md)  
  
-   [Iniciar el Asistente para la configuración de seguridad de la creación de reflejo de la base de datos &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a>Opciones  
 **Principal**  
 Especifique la cuenta de servicio de la instancia de servidor principal. Escriba el nombre del dominio en mayúsculas:  
  
 *NOMBREDEDOMINIO*\\*nombreDeUsuario*  
  
 **Reflejo**  
 Especifique la cuenta de servicio de la instancia del servidor reflejado. Escriba el nombre del dominio en mayúsculas:  
  
 *NOMBREDEDOMINIO*\\*nombreDeUsuario*  
  
 **Testigo**  
 Especifique la cuenta de servicio de la instancia de servidor testigo. Escriba el nombre del dominio en mayúsculas:  
  
 *NOMBREDEDOMINIO*\\*nombreDeUsuario*  
  
## <a name="see-also"></a>Vea también  
 [Propiedades de la base de datos &#40;página Creación de reflejo&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [Iniciar el Monitor de creación de reflejo de la base de datos &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [Creación de reflejo de la base de datos &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [Configurar cuentas de inicio de sesión para la creación de reflejo de la base de datos o grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](../../database-engine/database-mirroring/set-up-login-accounts-database-mirroring-always-on-availability.md)  
  
  
