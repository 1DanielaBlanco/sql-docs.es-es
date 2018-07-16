---
title: Escenarios de globalización para Analysis Services multidimensional | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- multiple language support [Analysis Services]
- languages [Analysis Services]
- SSAS, international considerations
- international considerations [Analysis Services]
- global considerations [Analysis Services]
- SQL Server Analysis Services, international considerations
- Analysis Services, international considerations
ms.assetid: e8af85ff-ef33-4659-a003-bb34578eb2a2
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0c8aeb19e6773b3f772ae0a62e7d72f647ee365e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37185402"
---
# <a name="globalization-scenarios-for-analysis-services-multiidimensional"></a>Escenarios de globalización para Analysis Services Multidimensional
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] almacena y manipula datos multilingües y metadatos en ambos modelos de datos tabulares y multidimensionales. El almacenamiento de datos es Unicode (UTF-16), en los juegos de caracteres que utilizan la codificación Unicode. Si carga datos ANSI en un modelo de datos, los caracteres se almacenan con puntos de código equivalentes de Unicode.  
  
 Con la compatibilidad con Unicode, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] puede almacenar datos en cualquiera de los idiomas admitidos por los sistemas operativos de servidor y cliente Windows, y permite la lectura, escritura, ordenación y comparación de datos en todos los juegos de caracteres que se usan en un equipo Windows. Las aplicaciones cliente de BI que consumen datos de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] pueden representar datos en el idioma que elija el usuario, siempre que haya datos en ese idioma dentro del modelo.  
  
 La compatibilidad de idiomas puede tener diferentes implicaciones para cada persona. En la siguiente lista se tratan algunas cuestiones comunes relacionadas con la forma en que Analysis Services es compatible con idiomas.  
  
-   Los datos, como ya se indicó, se almacenan en cualquier conjunto de caracteres con codificación Unicode de un sistema operativo de cliente Windows.  
  
-   Los metadatos, como los nombres de objetos, los identificadores y las descripciones, también pueden estar en cualquier idioma y alfabeto de Unicode. Esto se cumple aunque las herramientas y el entorno estén en otro idioma. Por ejemplo, en un entorno de desarrollo en el que se usen el idioma inglés y una intercalación latina en toda la pila, puede incluir en el modelo un objeto que utilice caracteres cirílicos en su nombre.  
  
     Solo en el caso de los modelos multidimensionales, los títulos y los miembros de atributos pueden expresarse como traducciones. Puede definir una o más traducciones y, luego, utilizar un identificador de configuración regional para determinar qué traducción se devolverá al cliente. Consulte [Características](#bkmk_features) , más adelante, para ver más detalles.  
  
-   Error, advertencia y mensajes informativos que devuelve el [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] motor (msmdsrv) están localizados a los 43 idiomas compatibles con Office y Office 365. No se requiere ninguna configuración para obtener mensajes en un idioma específico. La configuración regional de la aplicación cliente determina las cadenas que se devuelven.  
  
-   El archivo de configuración (msmdsrv.ini) y PowerShell AMO solo están disponibles en inglés.  
  
-   Los archivos de registro contienen una mezcla de mensajes en inglés y localizados, si instaló un paquete de idioma en el servidor Windows Server en el que se ejecuta Analysis Services.  
  
-   La documentación y las herramientas, como [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] y [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)], están traducidas a los siguientes idiomas: alemán, chino tradicional, chino simplificado, coreano, español, francés, italiano, japonés, portugués (Brasil) y ruso. Para usar una versión específica del lenguaje de las herramientas, instale una versión específica del lenguaje de SQL Server (por ejemplo, instalar la versión en alemán de SQL Server para tener Management Studio en alemán) o ejecutar el programa de instalación independiente en el idioma de destino para [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)].  
  
 Analysis Services le permite configurar el idioma, la intercalación y las traducciones de forma independiente en toda la jerarquía de objetos.  
  
 Los escenarios habilitados con idiomas, intercalaciones y traducciones incluyen:  
  
-   Un modelo de datos que proporciona varios títulos traducidos para que los valores y nombres de campo aparezcan en el idioma de elección. Para empresas que operen en países bilingües como Canadá, Bélgica y Suiza, la compatibilidad con varios idiomas en todas las aplicaciones de cliente y servidor es un requisito de codificación estándar. Este escenario se habilita con las traducciones y conversiones de divisa. Consulte [Características](#bkmk_features) , más adelante, para ver información detallada y vínculos.  
  
-   Los entornos de desarrollo y producción están ubicados geográficamente en distintos países. Cada vez es más común que una solución se desarrolle en un país y, luego, se implemente en otro. Saber cómo configurar las propiedades de idioma e intercalación es fundamental si tiene que preparar una solución desarrollada en un idioma para su implementación en un servidor que utiliza otro paquete de idioma. Configurar estas propiedades le permite invalidar los valores predeterminados heredados que obtiene del sistema host original. Consulte [Languages and Collations &#40;Analysis Services&#41;](languages-and-collations-analysis-services.md) para obtener más información sobre la configuración de propiedades.  
  
##  <a name="bkmk_features"></a> Características para crear una solución multidimensional globalizada  
 [!INCLUDE[applies](../includes/applies-md.md)] Solo modelos de datos multidimensionales  
  
 En el nivel de cliente, las aplicaciones globalizadas que consumen o manipulan [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] datos multidimensionales pueden utilizar las características multilingües y multiculturales en [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]:  
  
-   [Traducciones &#40;Analysis Services&#41; ](translations-analysis-services.md) se utilizan para incrustar varios títulos para un único objeto, donde cada cadena traducida puede existir junto con otras traducciones. Puede usar [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] para definir las traducciones del título, la descripción y los tipos de cuenta de cubos y medidas, dimensiones y atributos. Puede recuperar datos y metadatos de los objetos de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] en los que se han definido las traducciones automáticamente proporcionando un identificador de configuración regional cuando se conecte con una instancia de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
     Encontrará una lección sobre cómo usar esta característica en [Lección 9: Definir perspectivas y traducciones](lesson-9-defining-perspectives-and-translations.md), en el tutorial de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
-   [Conversiones de moneda &#40;Analysis Services&#41; ](currency-conversions-analysis-services.md) es a través de scripts MDX especializados que convierten medidas que contengan datos de moneda. Puede usar el Asistente de Business Intelligence de [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)] para generar un script MDX que utilice una combinación de datos y metadatos de dimensiones, atributos y grupos de medida para convertir las medidas que contienen datos de divisas.  
  
## <a name="in-this-section"></a>En esta sección  
  
|Tema|Descripción|  
|-----------|-----------------|  
|[Idiomas e intercalaciones &#40;Analysis Services&#41;](languages-and-collations-analysis-services.md)|Especifique el idioma y la intercalación de Windows predeterminados de una instancia de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Las opciones afectan a los datos y metadatos administrados por [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].|  
|[Traducciones &#40;Analysis Services&#41;](translations-analysis-services.md)|Definir las traducciones de un [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] base de datos y los objetos que contiene la base de datos. En este tema, se explica cómo [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] resuelve las solicitudes de datos y metadatos traducidos de las aplicaciones cliente.|  
|[Conversiones de moneda &#40;Analysis Services&#41;](currency-conversions-analysis-services.md)|Defina una conversión de divisa con el Asistente de Business Intelligence.|  
|[Sugerencias de globalización y procedimientos recomendados &#40;Analysis Services&#41;](globalization-tips-and-best-practices-analysis-services.md)|Revisa varios procedimientos de diseño y codificación que pueden ayudarle a evitar problemas relacionados con los datos en diversos idiomas.|  
  
## <a name="see-also"></a>Vea también  
 [Internacionalización para aplicaciones de Windows](http://msdn.microsoft.com/library/windows/desktop/dd318661%28v=vs.85%29.aspx)   
 [Ir al Centro para desarrolladores Global](http://msdn.microsoft.com/goglobal/bb871628.aspx)   
 [Aplicaciones de escritura Windows Store con diseño adaptable basado en la configuración regional](http://blogs.windows.com/buildingapps/2014/03/06/writing-windows-store-apps-with-locale-based-adaptive-design/)   
 [Desarrollo de aplicaciones Windows universales con C# y XAML](http://www.microsoftvirtualacademy.com/training-courses/developing-universal-windows-apps-with-c-and-xaml)  
  
  
