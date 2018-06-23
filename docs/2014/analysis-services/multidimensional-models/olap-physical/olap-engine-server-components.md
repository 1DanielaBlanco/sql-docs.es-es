---
title: Componentes de servidor del motor OLAP | Documentos de Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Analysis Services, architecture
- ports [Analysis Services]
- XML/A listener
- server architecture [Analysis Services]
ms.assetid: 5193c976-9dcd-459c-abba-8c3c44e7a7f2
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: a3486ed70d6da2d2091da02cf7e2a55fcd2b1d1b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36105969"
---
# <a name="olap-engine-server-components"></a>Componentes de servidor del motor OLAP
  El componente de servidor de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] es el **msmdsrv.exe** aplicación, que se ejecuta como un servicio de Windows. Esta aplicación está formada por componentes de seguridad, un componente de escucha XML for Analysis (XMLA), un componente de procesador de consultas y otros componentes internos que realizan las siguientes funciones:  
  
-   Analizar instrucciones recibidas de clientes  
  
-   Administrar metadatos  
  
-   Controlar transacciones  
  
-   Procesar cálculos  
  
-   Almacenar datos de celdas y dimensiones  
  
-   Crear agregaciones  
  
-   Programar consultas  
  
-   Almacenar objetos en memoria caché  
  
-   Administrar recursos del servidor  
  
## <a name="architectural-diagram"></a>Diagrama de la arquitectura  
 Las instancias de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] se ejecutan como un servicio independiente y la comunicación con el servicio se produce a través de XML for Analysis (XMLA), mediante HTTP o TCP. AMO es el nivel que existe entre la aplicación de usuario y la instancia de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Este nivel proporciona acceso a los objetos administrativos de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. AMO es una biblioteca de clases que toma los comandos de una aplicación cliente y los convierte en mensajes XMLA para la instancia de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] . AMO muestra los objetos de instancia de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] a la aplicación de usuario final como clases, con miembros de método que ejecutan comandos y miembros de propiedad que contienen los datos de los objetos de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .  
  
 La siguiente ilustración muestra la arquitectura de componentes de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], incluidos todos los elementos principales que se ejecutan dentro de la instancia de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] y todos los componentes de usuario que interactúan con ella. La ilustración también muestra que la única manera de tener acceso a la instancia es utilizando el agente de escucha de XML for Analysis (XMLA), ya sea mediante HTTP o TCP.  
  
 ![Diagrama de arquitectura de sistema de Analysis Services](../../../analysis-services/dev-guide/media/analysisservicessystemarchitecture.gif "diagrama de arquitectura de sistema de Analysis Services")  
  
## <a name="xmla-listener"></a>Componente de escucha XMLA  
 El componente de escucha XMLA controla todas las comunicaciones XMLA entre [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] y sus clientes. El [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] `Port` opción de configuración en el archivo msmdsrv.ini puede usarse para especificar un puerto en el que un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instancia escucha. Un valor de 0 en este archivo indica que [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] escucha en el puerto predeterminado. A menos que se especifique lo contrario, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] utiliza los siguientes puertos TCP predeterminados:  
  
|Puerto|Descripción|  
|----------|-----------------|  
|2383|Instancia predeterminada de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|2382|Redirector de otras instancias de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|Se asigna dinámicamente al iniciar el servidor.|Instancia con nombre de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
  
 Vea [configurar Firewall de Windows para permitir el acceso a Analysis Services](../../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) para obtener más detalles.  
  
## <a name="see-also"></a>Vea también  
 [Las reglas para nombres de objeto &#40;Analysis Services&#41;](object-naming-rules-analysis-services.md)   
 [Arquitectura física &#40;Analysis Services - datos multidimensionales&#41;](understanding-microsoft-olap-physical-architecture.md)   
 [Arquitectura lógica &#40;Analysis Services - datos multidimensionales&#41;](../olap-logical/understanding-microsoft-olap-logical-architecture.md)  
  
  