---
title: Traducciones de cubo | Documentos de Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: olap
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1e4d4200def774bce340af8704009c096ad128a8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="cube-translations"></a>Traducciones de cubo
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Una traducción es un mecanismo simple para cambiar las etiquetas y títulos mostrados de un idioma a otro. Cada traducción se define como un par de valores: una cadena con el texto traducido y un número con el identificador de idioma. Todos los objetos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] disponen de traducción. Las dimensiones también pueden tener los valores de atributo traducidos. La aplicación cliente es responsable de localizar la configuración de idioma que el usuario ha definido y efectuar el cambio para mostrar todos los títulos y etiquetas en dicho idioma. Un objeto puede tener tantas traducciones como se desee.  
  
 Un objeto <xref:Microsoft.AnalysisServices.Translation> simple está compuesto por el número del identificador de idioma y el título traducido. El número de Id. de idioma es un **entero** con el identificador de idioma. El título traducido es el texto traducido.  
  
 En [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], una traducción de cubo es una representación específica del lenguaje del nombre de un objeto de cubo, como un título o una carpeta para mostrar. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] también admite traducciones de nombres de dimensión y de miembro.  
  
 Las traducciones ofrecen compatibilidad de servidor para aplicaciones cliente que admitan varios idiomas. Con frecuencia, usuarios de distintos países ven los datos de un cubo. Resulta útil poder traducir los distintos elementos de un cubo a diferentes idiomas para que los usuarios de estos idiomas puedan ver y comprender los metadatos del cubo. Por ejemplo, un usuario corporativo en Francia puede obtener acceso a un cubo desde una estación de trabajo con una configuración regional en francés y ver los valores de las propiedades del objeto en francés. Igualmente, un usuario corporativo en Alemania puede obtener acceso al mismo cubo desde una estación de trabajo con una configuración regional en alemán y ver los valores de las propiedades del objeto en alemán.  
  
 La información de intercalación e idioma para el equipo cliente se almacena con formato de identificador de configuración regional (LCID). Tras la conexión, el cliente pasa el LCID a la instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. La instancia utiliza el LCID para determinar el conjunto de traducciones que se utiliza al proporcionar metadatos de objetos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] a cada usuario corporativo. Si un objeto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] no contiene la traducción especificada, el idioma predeterminado se utiliza para devolver el contenido al cliente.  
  
## <a name="see-also"></a>Vea también  
 [Traducciones de dimensiones](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimension-translations.md)   
 [Compatibilidad con traducción en Analysis Services](../../analysis-services/translation-support-in-analysis-services.md)   
 [Sugerencias de globalización y mejores prácticas & #40; Analysis Services & #41;](../../analysis-services/globalization-tips-and-best-practices-analysis-services.md)  
  
  
