---
title: Traducciones en modelos multidimensionales (Analysis Services) | Documentos de Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.asvs.dimensiondesigner.deletelanguagefirm.f1
ms.assetid: 5521f8ef-b10a-4861-9df7-1e43e0a1fb3f
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 87f826e36a3fb58cfb1adba2b30a1375e3b84e71
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="translations-in-multidimensional-models-analysis-services"></a>Particiones en modelos multidimensionales (Analysis Services)
  Puede definir traducciones en [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] utilizando el diseñador adecuado para el objeto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] que se vaya a traducir. Al definir una traducción, se crea un objeto **Translation** asociado con el objeto [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] adecuado que contiene los valores literales explícitos especificados, en el idioma especificado, para las propiedades del objeto [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] asociado.  
  
## <a name="elements-of-a-multi-lingual-data-model"></a>Elementos de un modelo de datos en varios idiomas  
 Un modelo de datos que se use en una solución multilingüe no solo necesitará las etiquetas traducidas (los nombres de campo y las descripciones). También debe proporcionar los valores de los datos que se articulan en los diferentes alfabetos de los idiomas. Para conseguir una solución multilingüe, necesita atributos individuales, enlazados a las columnas de una base de datos externa que devuelva los datos.  
  
 Las bases de datos de muestra de Adventure Works (almacenamiento de datos relacional y multidimensional) muestran las funcionalidades de traducción de Analysis Services. El modelo de muestra incluye descripciones y títulos traducidos. El almacenamiento de datos relacional de muestra contiene columnas de valores traducidos que proporcionan los miembros de atributos localizados del modelo.  
  
 Para ver los valores de datos traducidos de los que dispone el modelo:  
  
1.  Abra el modelo multidimensional de Adventure Works en el diseñador.  
  
2.  En el Explorador de soluciones, abra vistas del origen de datos y haga doble clic en Adventure Works DW\<versión > .dsv.  
  
3.  Busque dimDate, dimProduct, dimProductCategory o dimProductSubcategory. Todas estas dimensiones contienen atributos de miembros traducidos de mes, día de la semana, nombre de producto, nombre de categoría, etc.  
  
4.  Haga clic con el botón derecho en cualquier campo y seleccione **Explorar datos**. Verá las traducciones de inglés, español y francés de cada miembro.  
  
 Los formatos de fecha, hora y moneda no se implementan con traducciones. Para proporcionar de forma dinámica los formatos de cada cultura en función de la configuración regional del cliente, utilice el Asistente de conversión de moneda y la propiedad **FormatString** . Para más información, vea [Conversiones de moneda &#40;Analysis Services&#41;](../../analysis-services/currency-conversions-analysis-services.md) y [Elemento FormatString &#40;ASSL&#41;](../../analysis-services/scripting/properties/formatstring-element-assl.md).  
  
 [Lesson 9: Defining Perspectives and Translations](../../analysis-services/lesson-9-defining-perspectives-and-translations.md) , en el Tutorial de Analysis Services, le guiará por los pasos necesarios para crear y probar las traducciones.  
  
## <a name="defining-translations"></a>Definir traducciones  
  
### <a name="add-translations-to-a-cube"></a>Agregar traducciones a un cubo  
 Puede agregar traducciones al cubo, grupos de medidas, medidas, dimensión del cubo, perspectivas, KPI, acciones, conjuntos con nombre y miembros calculados.  
  
1.  En el Explorador de soluciones, haga doble clic en el nombre del cubo para abrir el Diseñador de cubos.  
  
2.  Haga clic en la pestaña **Traducciones** . Todos los objetos que admitan traducciones se mostrarán en esta página.  
  
3.  Para cada objeto, especifique el idioma de destino (se resuelve internamente en un LCID), el título traducido y la descripción traducida. La lista de idiomas es coherente en todo Analysis Services, tanto si configura el idioma del servidor en Management Studio como si agrega una invalidación de traducción en un solo atributo.  
  
     Recuerde que no puede cambiar la intercalación. Un cubo utiliza básicamente una intercalación, incluso si admite varios idiomas mediante títulos traducidos (hay una excepción para los atributos de dimensión que se describe a continuación). Si los idiomas no se ordenan correctamente en la intercalación compartida, tendrá que hacer copias del cubo para adaptarse a los requisitos de intercalación.  
  
4.  Compile e implemente el proyecto.  
  
5.  Conéctese a la base de datos con una aplicación cliente, como Excel, y modifique la cadena de conexión para usar el identificador de configuración regional. Para más información, vea [Sugerencias de globalización y procedimientos recomendados &#40;Analysis Services&#41;](../../analysis-services/globalization-tips-and-best-practices-analysis-services.md).  
  
### <a name="add-translations-to-a-dimension-and-attributes"></a>Agregar traducciones a una dimensión y atributos  
 Puede agregar traducciones a dimensiones de una base de datos, atributos, jerarquías y niveles de una jerarquía.  
  
 Los títulos traducidos se agregan al modelo manualmente con el teclado o con copiar y pegar, pero en el caso de los miembros de atributos de dimensión, puede obtener valores traducidos de una base de datos externa. En concreto, la propiedad **CaptionColumn** de un atributo se puede enlazar a una columna de una vista de un origen de datos.  
  
 En el nivel del atributo, puede invalidar la configuración de intercalación: por ejemplo, puede ajustar la distinción de ancho o usar una ordenación binaria para un atributo concreto. En [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], la intercalación se expone donde se definen los enlaces de datos. Dado que va a enlazar una traducción de atributo de dimensión con una columna de un origen diferente en la vista del origen de datos (DSV), hay una configuración de intercalación disponible para que pueda especificar la intercalación que utiliza la columna de origen. Consulte [Set or Change the Column Collation](../../relational-databases/collations/set-or-change-the-column-collation.md) para ver más detalles sobre la intercalación de columnas en la base de datos relacional.  
  
1.  En el Explorador de soluciones, haga doble clic en el nombre de la dimensión para abrir el Diseñador de dimensiones.  
  
2.  Haga clic en la pestaña **Traducciones** . Todos los objetos de dimensión que admitan traducciones se mostrarán en esta página.  
  
     Para cada objeto, especifique el idioma de destino (se resuelve en un LCID), el título traducido y la descripción traducida. La lista de idiomas es coherente en todo Analysis Services, tanto si configura el idioma del servidor en Management Studio como si agrega una invalidación de traducción en un solo atributo.  
  
3.  Para enlazar un atributo con una columna que proporciona valores traducidos:  
  
    1.  Aún en el Diseñador de dimensiones | **Traducciones**, agregue una nueva traducción. Elija el idioma. Aparecerá una nueva columna en la página para aceptar los valores traducidos.  
  
    2.  Coloque el cursor en una celda vacía situada junto a uno de los atributos. El atributo no puede ser la clave, pero todos los demás atributos son opciones viables. Debería ver un pequeño botón con un punto dentro de él. Haga clic en el botón para abrir el **cuadro de diálogo Traducción de datos de atributos**.  
  
    3.  Escriba una traducción para el título. Se usará como etiqueta de datos en el idioma de destino: por ejemplo, como nombre de campo en una lista de campos de tabla dinámica.  
  
    4.  Elija la columna de origen que proporciona los valores traducidos de los miembros del atributo. Solo están disponibles las columnas ya existentes en la tabla o la consulta enlazada a la dimensión. Si la columna no existe, deberá modificar la vista del origen de datos, la dimensión y el cubo para elegir la columna.  
  
    5.  Elija la intercalación y el criterio de ordenación, si procede.  
  
4.  Compile e implemente el proyecto.  
  
5.  Conéctese a la base de datos con una aplicación cliente, como Excel, y modifique la cadena de conexión para usar el identificador de configuración regional. Para más información, vea [Sugerencias de globalización y procedimientos recomendados &#40;Analysis Services&#41;](../../analysis-services/globalization-tips-and-best-practices-analysis-services.md).  
  
### <a name="add-a-translation-of-the-database-name"></a>Agregar una traducción del nombre de la base de datos  
 En el nivel de la base de datos, puede agregar traducciones del nombre y la descripción de la base de datos. El nombre traducido de la base de datos puede verse en las conexiones de cliente que especifican el LCID del idioma, pero depende de la herramienta. Por ejemplo, al ver la base de datos en Management Studio, no se mostrará el nombre traducido, aunque especifique el identificador de configuración regional en la conexión. La API que usa Management Studio para conectarse a Analysis Services no lee la propiedad **Language** .  
  
1.  En el Explorador de soluciones, haga clic con el botón derecho en el nombre del proyecto | **Editar base de datos** para abrir el Diseñador de bases de datos.  
  
2.  En Traducciones, especifique el idioma de destino (se resuelve en un LCID), el título traducido y la descripción traducida. La lista de idiomas es coherente en todo Analysis Services, tanto si configura el idioma del servidor en Management Studio como si agrega una invalidación de traducción en un solo atributo.  
  
3.  En la página de propiedades de la base de datos, configure **Language** con el mismo LCID que especificó para la traducción. Si quiere, configure también **Collation** si el valor predeterminado no es adecuado.  
  
4.  Compile e implemente la base de datos.  
  
## <a name="deleting-translation-objects"></a>Eliminar objetos de traducción  
 Puede hacer clic con el botón secundario en un objeto de traducción en el diseñador de cubos o dimensiones para quitarlo de forma definitiva. No es posible restaurar ni reciclar un objeto eliminado, de modo que asegúrese de revisar la lista de objetos afectados antes de continuar.  
  
## <a name="resolving-translations"></a>Resolver traducciones  
 Si una aplicación cliente solicita información en un identificador de idioma concreto, la instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] intenta resolver los datos y los metadatos  de los objetos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] con el identificador de idioma más cercano posible. Si la aplicación cliente no especifica un idioma predeterminado, especifica el identificador de configuración regional neutro (0) o procesa el identificador de idioma predeterminado (1024), [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] usará el idioma predeterminado para que la instancia devuelva los datos y los metadatos de los objetos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Si la aplicación cliente especifica un identificador de idioma diferente al identificador de idioma predeterminado, la instancia recorre en iteración todos las traducciones disponibles para todos los objetos disponibles. Si el identificador de idioma predeterminado coincide con el identificador de idioma de una traducción, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] devuelve esa traducción. Si no se encuentra ninguna coincidencia, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] intenta utilizar uno de los siguientes métodos para devolver traducciones con el identificador de idioma más cercano al identificador de idioma especificado:  
  
-   En los siguientes identificadores de idioma, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] intenta utilizar un identificador de idioma alternativo si no se ha definido una traducción para el identificador de idioma especificado:  
  
    |Identificador de idioma especificado|Identificador de idioma alternativo|  
    |-----------------------------------|-----------------------------------|  
    |3076 - Chino (Hong Kong, ZAE, RPC)|1028 - Chino (Taiwán)|  
    |5124 - Chino (Macao RAE)|1028 - Chino (Taiwán)|  
    |1028 - Chino (Taiwán)|Idioma predeterminado|  
    |4100 - Chino (Singapur)|2052 - Chino (RPC)|  
    |2074 - Croata|Idioma predeterminado|  
    |3098 - Croata (cirílico)|Idioma predeterminado|  
  
-   En los demás identificadores de idioma especificados, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] extrae el idioma principal del identificador de idioma especificado y recupera el identificador de idioma que indica Windows como el mejor resultado del idioma principal. Si no se puede encontrar una traducción para la mejor coincidencia de identificador de idioma, o si el identificador de idioma especificado es la mejor coincidencia para el idioma principal, se utiliza el idioma predeterminado.  
  
## <a name="see-also"></a>Vea también  
 [Escenarios de globalización para Analysis Services](../../analysis-services/globalization-scenarios-for-analysis-services.md)   
 [Idiomas e intercalaciones &#40; Analysis Services &#41;](../../analysis-services/languages-and-collations-analysis-services.md)  
  
  

