---
title: Control de errores (MDX) | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scripts [MDX], exceptions
- exceptions [MDX]
ms.assetid: bc6ff0af-9fe6-44d6-bc3c-801d71ea41a9
caps.latest.revision: "26"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8679c6d912e6dab8fa89f4f67ddfa9070c04460f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="error-handling-mdx"></a>Control de errores (MDX)
  Todos los cubos pueden controlar la forma en que se administran los errores de los scripts de expresiones multidimensionales (MDX). El control de errores se realiza mediante el enumerador **ScriptErrorHandlingMode** . Los valores posibles que admite este enumerador son los siguientes:  
  
 **IgnoreNone**  
 Hace que el servidor genere un error cuando [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] detecta un error en el script MDX.  
  
 **IgnoreAll**  
 Hace que el servidor omita todos los comandos del script MDX que contengan un error, incluidos los errores de sintaxis, de resolución de nombres y otros.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.AnalysisServices.Cube.ScriptErrorHandlingMode%2A>  
  
  
