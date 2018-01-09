---
title: "Arquitectura lógica (Analysis Services - datos multidimensionales) | Documentos de Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- Analysis Services, architecture
- logical architecture [Analysis Services Multidimensional Data]
ms.assetid: 1b9cae0a-8990-4194-af5f-a1ea5f2aff06
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 85b98af5dc33f21da4b54f14e60179594382c934
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="understanding-microsoft-olap-logical-architecture"></a>Descripción de la arquitectura lógica de OLAP de Microsoft
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)][!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] usa componentes de servidor y cliente para proporcionar procesamiento analítico en línea (OLAP) y funcionalidad de minería de datos para aplicaciones de business intelligence:  
  
-   El componente de servidor de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] se implementa como servicio de Microsoft Windows. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] admite varias instancias en el mismo equipo, con cada instancia de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] implementa como una instancia independiente del servicio de Windows.  
  
-   Los clientes se comunican con [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] mediante el estándar público XML for Analysis (XMLA), protocolo basado en SOAP para emitir comandos y recibir respuestas, que se expone como servicio web. Además, se proporcionan modelos de objetos de cliente en XMLA, a los que se puede obtener acceso mediante un proveedor administrado, como ADOMD.NET, o un proveedor OLE DB nativo.  
  
-   Pueden emitirse comandos de consulta mediante los siguientes lenguajes: SQL; MDX (Expresiones multidimensionales), un lenguaje de consulta estándar para el análisis; o Extensiones de minería de datos (DMX), un lenguaje de consulta estándar orientado a la minería de datos. También se puede usar el lenguaje de script de Analysis Services (ASSL) para administrar objetos de base de datos de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] también admite un motor de cubo local que permite a las aplicaciones en clientes desconectados examinar datos multidimensionales almacenados localmente. Para obtener más información, vea [requisitos de la arquitectura de cliente para el desarrollo de Analysis Services](../../../analysis-services/multidimensional-models/olap-physical/client-architecture-requirements-for-analysis-services-development.md)  
  
## <a name="in-this-section"></a>En esta sección  
 **Introducción a la arquitectura lógica**  
 [Introducción a la arquitectura lógica &#40; Analysis Services - datos multidimensionales &#41;](../../../analysis-services/multidimensional-models/olap-logical/logical-architecture-overview-analysis-services-multidimensional-data.md)  
  
 **Objetos de servidor**  
 [Objetos de servidor &#40; Analysis Services - datos multidimensionales &#41;](../../../analysis-services/multidimensional-models/olap-logical/server-objects-analysis-services-multidimensional-data.md)  
  
 **Objetos de base de datos**  
 [Objetos de base de datos &#40; Analysis Services - datos multidimensionales &#41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
 **Objetos de dimensión**  
 [Objetos de dimensión &#40; Analysis Services - datos multidimensionales &#41;](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimension-objects-analysis-services-multidimensional-data.md)  
  
 **Objetos de cubo**  
 [Objetos de cubo &#40; Analysis Services - datos multidimensionales &#41;](../../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)  
  
 **Seguridad de acceso del usuario**  
 [Arquitectura de seguridad de acceso de usuario](http://msdn.microsoft.com/library/71b44e10-2bd0-44f7-8de9-7c8f5b7ac082)  
  
## <a name="see-also"></a>Ver también  
 [Descripción de la arquitectura OLAP de Microsoft](../../../analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)   
 [Arquitectura física &#40; Analysis Services - datos multidimensionales &#41;](../../../analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-physical-architecture.md)  
  
  
