---
title: Copiar elementos de proyecto | Documentos de Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data sources [Integration Services], copying
- packages [Integration Services], copying
- copying data source views
- copying data sources
- copying packages
- data source views [Integration Services], copying
ms.assetid: 1606c54d-20f9-49f3-a4ef-caad83a772aa
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 57c3263617b89bfa9ca39f81fb0890b45532a744
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36114299"
---
# <a name="copy-project-items"></a>Copiar los elementos de proyectos
  En este tema se describe cómo copiar objetos dentro de un proyecto de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] o entre proyectos de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . También puede copiar objetos entre los otros tipos de proyectos de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] , [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] y [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Para copiar entre proyectos, el proyecto debe formar parte de la misma solución de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] . Para obtener más información, vea [Proyectos de Integration Services &#40;SSIS&#41;](integration-services-ssis-projects-and-solutions.md).  
  
### <a name="to-copy-project-level-items"></a>Para copiar elementos de nivel de proyecto  
  
1.  En [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], abra la solución o el proyecto de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] con el que desea trabajar.  
  
2.  Expanda el proyecto y la carpeta de elementos desde donde se copiará.  
  
3.  Haga clic con el botón derecho en el elemento y, después, haga clic en **Copiar**.  
  
4.  Haga clic con el botón derecho en el proyecto de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] y luego haga clic en **Pegar**.  
  
     Los elementos se copian automáticamente en la carpeta correcta. Si copia elementos en el proyecto de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] que no son paquetes, estos elementos se copian a la carpeta **Varios** .  
  
## <a name="see-also"></a>Vea también  
 [Servicios de integración &#40;SSIS&#41; paquetes](../../2014/integration-services/integration-services-ssis-packages.md)   
 [Copiar objetos de paquete](../../2014/integration-services/copy-package-objects.md)  
  
  