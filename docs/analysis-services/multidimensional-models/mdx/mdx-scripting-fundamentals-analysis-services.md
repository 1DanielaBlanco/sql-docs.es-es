---
title: Aspectos básicos (Analysis Services) de Scripting de MDX | Documentos de Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: mdx
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 07966beb130bae8e144b0380c332ade91cfe466c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-scripting-fundamentals-analysis-services"></a>Aspectos básicos de scripting MDX (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  En [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], un script de expresiones multidimensionales (MDX) se compone de una o más expresiones o instrucciones MDX que llenan un cubo con cálculos.  
  
 Un script MDX define el proceso de cálculo del cubo. Los scripts MDX también se consideran parte del cubo. Por lo tanto, si se cambia un script MDX asociado a un cubo, también se cambia de forma inmediata el proceso de cálculo del cubo.  
  
 Para crear scripts MDX, puede utilizar el Diseñador de cubos de [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]. Para más información, vea [Definir asignaciones y otros comandos de script](../../../analysis-services/multidimensional-models/define-assignments-and-other-script-commands.md) e [Introduction to MDX Scripting in Microsoft SQL Server 2005 (Introducción a la creación de scripts en Microsoft SQL Server 2005)](http://go.microsoft.com/fwlink/?LinkId=81892).  
  
 Encontrará información acerca de los problemas de rendimiento relacionados con los cálculos y las consultas MDX en la sección dedicada a la optimización de MDX de la [guía de rendimiento de SQL Server Analysis Services](http://go.microsoft.com/fwlink/p/?LinkId=399050).  
  
## <a name="in-this-section"></a>En esta sección  
  
|Tema|Description|  
|-----------|-----------------|  
|[El Script MDX básico & #40; MDX & #41;](../../../analysis-services/multidimensional-models/mdx/the-basic-mdx-script-mdx.md)|Incluye información detallada sobre el script MDX básico, incluido el script MDX predeterminado proporcionado en cada cubo, así como información sobre el funcionamiento general de los scripts MDX en los cubos de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Administración de ámbito y contexto & #40; MDX & #41;](../../../analysis-services/multidimensional-models/mdx/managing-scope-and-context-mdx.md)|Describe cómo utilizar la instrucción [CALCULATE](../../../mdx/mdx-scripting-calculate.md) , la instrucción [SCOPE](../../../mdx/mdx-scripting-scope.md) y la función [This](../../../mdx/this-mdx.md) para administrar el contexto y el ámbito de un script MDX.|  
|[Uso de Variables y parámetros & #40; MDX & #41;](../../../analysis-services/multidimensional-models/mdx/using-variables-and-parameters-mdx.md)|Describe cómo utilizar las variables y los parámetros en un script MDX.|  
|[Control de errores & #40; MDX & #41;](../../../analysis-services/multidimensional-models/mdx/error-handling-mdx.md)|Explica cómo administrar los errores en un script MDX.|  
|[Compatibilidad con MDX & #40; MDX & #41;](../../../analysis-services/multidimensional-models/mdx/supported-mdx-mdx.md)|Proporciona una lista de operadores, instrucciones y funciones MDX admitidos en un script MDX.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia del lenguaje MDX & #40; MDX & #41;](../../../mdx/mdx-language-reference-mdx.md)  
  
  
