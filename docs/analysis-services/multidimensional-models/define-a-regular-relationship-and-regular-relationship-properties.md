---
title: "Definir una relación normal y las propiedades de relación normal | Documentos de Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- granularity attribute
- relationships [Analysis Services], regular relationships
ms.assetid: 840280d8-20c3-46c0-99ea-62479469c36b
caps.latest.revision: "9"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 10025f3c362a0be45d782644ca36a41661e13c68
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2017
---
# <a name="define-a-regular-relationship-and-regular-relationship-properties"></a>Definir relaciones normales y propiedades de las relaciones normales
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Al definir una nueva dimensión de cubo o un nuevo grupo de medida, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] intentará detectar si una relación normal existe y, a continuación, establezca la configuración de uso de dimensiones en **Regular**. Puede ver o modificar una relación de dimensión normal en la pestaña **Uso de dimensiones** del Diseñador de cubos.  
  
 Al definir la relación de una dimensión de cubo con un grupo de medida, también se especifica el atributo de granularidad de esa relación. El atributo de granularidad define el nivel mínimo de detalle disponible en el cubo para dicha dimensión, que suele ser el atributo clave de la dimensión. Sin embargo, en algunos casos, quizás desee establecer la granularidad de determinada dimensión de cubo de determinado grupo de medida en otra granularidad. Por ejemplo, si utiliza un grupo de medida Sales Quotas o Budget, quizás desee establecer el atributo de granularidad de la dimensión Time en el atributo Month, no en el atributo Day. Al especificar que el atributo de granularidad sea distinto del atributo clave, se debe garantizar que los demás atributos de la dimensión estén directa o indirectamente vinculados a este otro atributo por medio de relaciones de atributo. De lo contrario, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] no podrá agregar los datos correctamente.  
  
  
