---
title: "Propiedades de SQL Server Browser (pestaña iniciar sesión) | Documentos de Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c77871ec-c2f4-4e4a-9a10-5aeb4ae70507
caps.latest.revision: "20"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: acc99f6cace37453d01cbe5a0f3ea790ace7d927
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2017
---
# <a name="sql-server-browser-properties-log-on-tab"></a>Propiedades de SQL Server Browser (pestaña Iniciar sesión)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] programa explorador se ejecuta como un servicio en el servidor. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser escucha las solicitudes entrantes de recursos de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y proporciona información acerca de las instancias de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instaladas en el equipo.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] El Explorador escucha en un puerto UDP y acepta solicitudes no autenticadas que usan el protocolo de resolución de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SSRP).  
  
 Cambiar la contraseña de una cuenta surte efecto inmediato, sin necesidad de reiniciar el servicio.  
  
## <a name="options"></a>Opciones  
 **Cuenta de sistema local**  
 Ejecute el servicio Explorador de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en el contexto de seguridad de la cuenta Sistema local. Si es posible, utilice en su lugar una cuenta con permisos limitados.  
  
 **Esta cuenta**  
 Especifique una cuenta de usuario local o de dominio que utilice la autenticación de Windows. Se recomienda utilizar una cuenta de usuario de dominio que tenga derechos mínimos para los servicios. Para obtener información acerca de cómo seleccionar una cuenta, vea el tema sobre la configuración de cuentas de servicios de Windows en los Libros en pantalla de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Examinar**  
 Busque un usuario o una entidad de seguridad integrada.  
  
> [!IMPORTANT]  
>  Utilice una cuenta con permisos limitados. Para obtener información sobre los permisos necesarios para el servicio Explorador de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vea la sección sobre seguridad del [Servicio SQL Server Browser](../../tools/configuration-manager/sql-server-browser-service.md).  
  
 **Contraseña**  
 Escriba la contraseña de la entidad de seguridad.  
  
 **Confirmar contraseña**  
 Confirme la contraseña de la entidad de seguridad.  
  
 **Estado del servicio**  
 Indica si el servicio está en ejecución, detenido o deshabilitado. "**…**" indica que hay un cambio de estado pendiente.  
  
 **Iniciar**  
 Inicie el servicio Explorador de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Detener**  
 Detenga el servicio Explorador de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Pausar**  
 Pause el servicio Explorador de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Reanudar**  
 Reanude un servicio Explorador de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pausado.  
  
## <a name="see-also"></a>Vea también  
 [Servicio SQL Server Browser](../../tools/configuration-manager/sql-server-browser-service.md)  
  
  
