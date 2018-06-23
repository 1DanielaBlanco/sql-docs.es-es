---
title: Información general del proceso de actualización | Documentos de Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- upgrading SQL Server
- Upgrade Advisor [SQL Server], process description
- SQL Server Upgrade Advisor, process description
- upgrade process [Upgrade Advisor]
ms.assetid: f77ffbab-a195-4124-acce-9c538f7ca9ce
caps.latest.revision: 39
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1cab41d5ec522964887237decdf426da3cf833d0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36104629"
---
# <a name="upgrade-process-overview"></a>Información general sobre el proceso de actualización
  En este tema se proporciona información sobre el procedimiento recomendado para el Asesor de actualizaciones de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y un resumen del proceso recomendado para actualizar a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="upgrade-process"></a>Proceso de actualización  
 Los servidores que estén ejecutando [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] o [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] se pueden actualizar a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Mientras que algunos [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] componentes pueden actualizarse en su lugar, otros usuarios se deben migrar y todavía otras personas han sido sustituidos por nuevos componentes. Por ejemplo, a partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) reemplaza Data Transformation Services (DTS) y DTS ya no se admite en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Al formular el plan de actualización, es posible que sea necesario planear la actualización de los paquetes DTS a los paquetes [!INCLUDE[ssIS](../../includes/ssis-md.md)].  
  
 El Asesor de actualizaciones permite evaluar instalaciones, componentes y archivos relacionados de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] actuales para identificar problemas conocidos que aparecerán durante y después de la migración o actualización a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Algunos de estos problemas conocidos bloquean la actualización de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. En el informe del Asesor de actualizaciones, estos problemas se identifican como Bloqueos de la actualización. Si no ha solucionado los bloqueos de la actualización antes de ejecutar el programa de instalación, el programa de instalación de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] sale y recomienda actualizar el Asesor de actualizaciones para identificar los problemas específicos que impiden la actualización.  
  
 Como práctica recomendada antes de actualizar a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], recomendamos que haga copia de seguridad de sus datos y configuraciones del sistema, y que siga los pasos estratégicos descritos en las instrucciones operativas definidas para su organización. Siga los pasos que se detallan a continuación para completar la actualización:  
  
1.  Vea [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).  
  
2.  Haga una copia de seguridad de los datos y de la configuración del sistema.  
  
3.  Ejecute el Asesor de actualizaciones.  
  
     El Asesor de actualizaciones no modificará los datos ni cambiará la configuración de su equipo.  
  
4.  Revise los problemas identificados en el informe del Asesor de actualizaciones.  
  
5.  Resuelva cualquier problema de bloqueo que pudiera impedir la actualización a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
6.  Resuelva cualquier otro problema previo a la actualización.  
  
7.  Ejecute el Asesor de actualizaciones para comprobar que se han resuelto todos los problemas conocidos.  
  
8.  Ejecute el programa de instalación de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
9. Resuelva cualquier problema de migración o posterior a la actualización.  
  
## <a name="see-also"></a>Vea también  
 [Ejecutar el Asesor de actualizaciones &#40;interfaz de usuario&#41;](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md)   
 [Uso de informes](../../../2014/sql-server/install/using-reports.md)   
 [Trabajar con el Asesor de actualizaciones](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  