---
title: Descripción del proveedor WMI para la administración de configuración | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- WMI Provider for Configuration Management, operations supported
ms.assetid: 92323972-7943-4208-bbf4-050774fb6027
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 238e8e52ec238e8387fd49d82f15368ef9be3d0b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2018
ms.locfileid: "48222338"
---
# <a name="understanding-the-wmi-provider-for-configuration-management"></a>Descripción del proveedor WMI para la administración de configuración
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proporciona el proveedor WMI para la administración de configuración. Esto permite usar Instrumental de administración de Windows (WMI) para administrar servicios de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], configuración de red de cliente y servidor de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], y alias de servidor. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] servicios, configuración de red y alias se representan mediante objetos WMI en el root\Microsoft\SqlServer\ComputerManagement*nn* espacio de nombres del equipo. Una vez establecida una conexión con el proveedor WMI en el equipo especificado, se pueden consultar los servicios, la configuración de red y el alias mediante WQL o un lenguaje de scripting.  
  
 El Proveedor WMI es un proveedor de instancias. Proporciona instancias de la [clases WMI](../wmi-provider-configuration-classes/wmi-provider-for-configuration-management-classes.md) y admite las siguientes operaciones asincrónicas.  
  
 Recuperación de instancias  
 Recuperación de una instancia de tipo de clase determinada.  
  
 Enumeración  
 Enumeración de todas las instancias de un tipo de clase.  
  
 Modificación  
 Modificación de una instancia de tipo de clase determinada.  
  
 Las clases tienen métodos que permiten modificar sus propiedades.  
  
 Eliminación  
 Quita una instancia de tipo de clase determinada.  
  
 Procesamiento de consultas  
 La enumeración de instancias de un tipo de clase basada en un filtro.  
  
 Para obtener ejemplos de aplicación de administración mediante el proveedor de WMI para la administración de configuración, consulte [usar WQL y lenguajes de secuencias de comandos con el proveedor WMI para la administración de configuración](using-wql-and-scripting-languages-with-the-wmi-provider.md).  
  
 Para obtener más información sobre la programación de aplicaciones de administración con el proveedor de WMI, vea la documentación de WMI en el [!INCLUDE[msCoName](../../includes/msconame-md.md)] SDK de .NET Framework.  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con el proveedor WMI para la administración de configuración](working-with-the-wmi-provider-for-configuration-management.md)   
 [Uso de WQL y lenguajes de scripting con el proveedor WMI para la administración de configuración](using-wql-and-scripting-languages-with-the-wmi-provider.md)  
  
  
