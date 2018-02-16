---
title: Desarrollar aplicaciones con Analysis Services Scripting Language (ASSL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Analysis Services Scripting Language
- ASSL
ms.assetid: ce9aca4d-b7ad-451e-bb7f-20c2b0c03f29
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a3fd425fe03387cd20eb6c63bb0a8e9b6ed8e572
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2018
---
# <a name="developing-with-analysis-services-scripting-language-assl"></a>Desarrollar aplicaciones con Analysis Services Scripting Language (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
El lenguaje de scripting de Analysis Services (ASSL) es una extensión de XMLA que agrega un lenguaje de definición de objetos y un lenguaje de comandos para crear y administrar estructuras Analysis Services directamente en el servidor. Puede utilizar ASSL en la aplicación personalizada para comunicarse con Analysis Services a través del protocolo XMLA. ASSL consta de dos partes:  
  
-   Un lenguaje de definición de datos (DDL), o lenguaje de definición de objetos, que define y describe una instancia de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], así como las bases de datos y los objetos de base de datos que la instancia contiene.  
  
-   Un lenguaje de comandos que envía comandos de acción, como **crear**, **Alter**, o **proceso**, a una instancia de Analysis Services. Este lenguaje de comandos se describe en el [XML for Analysis &#40; XMLA &#41; Referencia](../../../analysis-services/xmla/xml-for-analysis-xmla-reference.md).  
  
 Para ver el ASSL que describe una solución multidimensional en [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)], puede utilizar el comando Ver código en el nivel de proyecto. También puede crear o modificar el script de ASSL en [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] utilizando el editor de consultas XMLA. Los scripts que cree pueden usarse para administrar objetos o ejecutar comandos en el servidor.  
  
## <a name="see-also"></a>Vea también  
 [Objetos y características de objetos ASSL](../../../analysis-services/multidimensional-models/scripting-language-assl/assl-objects-and-object-characteristics.md)   
 [Convenciones XML de ASSL](../../../analysis-services/multidimensional-models/scripting-language-assl/assl-xml-conventions.md)   
 [Orígenes de datos y enlaces &#40; SSAS Multidimensional &#41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)  
  
  
