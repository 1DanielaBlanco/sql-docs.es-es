---
title: Desarrollar aplicaciones con Analysis Services Scripting Language (ASSL) | Documentos de Microsoft
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
- Analysis Services Scripting Language
- ASSL
ms.assetid: ce9aca4d-b7ad-451e-bb7f-20c2b0c03f29
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e7cc4d26ca41b36bc1472417d64702345911ceec
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36106853"
---
# <a name="developing-with-analysis-services-scripting-language-assl"></a>Desarrollar aplicaciones con Analysis Services Scripting Language (ASSL)
  El lenguaje de scripting de Analysis Services (ASSL) es una extensión de XMLA que agrega un lenguaje de definición de objetos y un lenguaje de comandos para crear y administrar estructuras Analysis Services directamente en el servidor. Puede utilizar ASSL en la aplicación personalizada para comunicarse con Analysis Services a través del protocolo XMLA. ASSL consta de dos partes:  
  
-   Un lenguaje de definición de datos (DDL), o lenguaje de definición de objetos, que define y describe una instancia de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], así como las bases de datos y los objetos de base de datos que la instancia contiene.  
  
-   Un lenguaje de comandos que envía comandos de acción, como `Create`, `Alter`o `Process`, a una instancia de Analysis Services. Este lenguaje de comandos se describe en el [XML for Analysis &#40;XMLA&#41; referencia](../../xmla/xml-for-analysis-xmla-reference.md).  
  
 Para ver el ASSL que describe una solución multidimensional en [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)], puede utilizar el comando Ver código en el nivel de proyecto. También puede crear o modificar el script de ASSL en [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] utilizando el editor de consultas XMLA. Los scripts que cree pueden usarse para administrar objetos o ejecutar comandos en el servidor.  
  
## <a name="see-also"></a>Vea también  
 [Objetos y características de objetos ASSL](assl-objects-and-object-characteristics.md)   
 [Convenciones XML de ASSL](assl-xml-conventions.md)   
 [Orígenes de datos y enlaces &#40;SSAS Multidimensional&#41;](../data-sources-and-bindings-ssas-multidimensional.md)  
  
  