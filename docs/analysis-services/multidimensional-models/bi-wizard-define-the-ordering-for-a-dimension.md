---
title: "Definir la ordenación en una dimensión | Documentos de Microsoft"
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
- OrderBy property
- dimensions [Analysis Services], ordering
- Business Intelligence enhancements [Analysis Services], ordering
- dimensions [Analysis Services], Business Intelligence enhancements
- ordering dimensions [Analysis Services]
- OrderByAttributeID property
ms.assetid: c42fbd58-244d-4e0a-b715-6f919cbc3ad9
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1b37dde7f32df56fdea9cb595796948f710a652f
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2017
---
# <a name="bi-wizard---define-the-ordering-for-a-dimension"></a>Asistente de BI - definir la ordenación en una dimensión
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Agregue el atributo mejora a un cubo o dimensión para especificar cómo se ordenan los miembros de un atributo de orden. Los miembros pueden ordenarse por el nombre o la clave del atributo, o bien por el nombre o la clave de otro atributo (en función de la relación de atributo). De forma predeterminada, los miembros se ordenan por nombre. Esta mejora cambia la configuración de las propiedades **OrderBy** y **OrderByAttributeID** de los atributos para una dimensión.  
  
 Para agregar el orden de atributos, se usa el Asistente de Business Intelligence y se selecciona la opción **Especificar el orden de los atributos** en la página **Elegir mejora** . A continuación, este asistente le guía por los pasos para seleccionar una dimensión a la que desee aplicar el orden de los atributos y especificar cómo se deben ordenar los atributos para la dimensión seleccionada.  
  
## <a name="selecting-a-dimension"></a>Seleccionar una dimensión  
 En la primera página **Especificar el orden de los atributos** del asistente, se especifica la dimensión a la que se desea aplicar el orden de los atributos. La mejora de orden de los atributos agregada a esta dimensión seleccionada produce cambios en la dimensión. Estos cambios son heredados por todos los cubos que incluyan la dimensión seleccionada.  
  
## <a name="specifying-ordering"></a>Especificar el orden  
 En la segunda página **Especificar el orden de los atributos** del asistente, se especifica de qué manera se ordenan todos los atributos de la dimensión.  
  
 En la columna **Atributo de orden** , se puede cambiar el atributo utilizado para aplicar el orden. Si el atributo que desea usar para ordenar los miembros no está en la lista, desplácese hacia abajo en la lista y, a continuación, seleccione  **\<nuevo atributo... >** para abrir el **seleccione una columna** cuadro de diálogo, siempre que sea posible Seleccione una columna en una tabla de dimensiones. Al seleccionar una columna mediante el cuadro de diálogo **Seleccionar una columna** se crea un atributo adicional con el que se ordenan los miembros de un atributo.  
  
 En la columna **Criterios** , puede seleccionar si ordena los miembros del atributo por **Clave** o **Nombre**.  
  
  
