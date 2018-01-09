---
title: "Agregar o eliminar una jerarquía definida por el usuario | Documentos de Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hierarchies [Analysis Services], adding
- removing hierarchies
- adding hierarchies
- deleting hierarchies
- hierarchies [Analysis Services], removing
ms.assetid: 953818b4-9543-4c01-bb20-1d45ec6dfb91
caps.latest.revision: "51"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: efa987972b10642f176e96bd93a9deee58aa06ec
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="user-defined-hierarchies---add-or-delete-a-user-defined-hierarchy"></a>Jerarquías definidas por el usuario - agregar o eliminar una jerarquía definida por el usuario
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Para agregar una jerarquía definida por el usuario o quitar una jerarquía definida por el usuario en una dimensión en el **estructura de dimensión** ficha en el Diseñador de dimensiones en [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Al agregar una jerarquía definida por el usuario, no está a disposición de los usuarios hasta que se crea una instancia de ella en una instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] y se procesa la dimensión. Para obtener más información, vea [Bases de datos de modelos multidimensionales &#40;SSAS&#41;](../../analysis-services/multidimensional-models/multidimensional-model-databases-ssas.md) y [Procesar un modelo multidimensional &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
### <a name="to-add-a-user-defined-hierarchy-to-a-dimension"></a>Para agregar una jerarquía definida por el usuario a una dimensión  
  
1.  En [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], abra el proyecto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] correspondiente y a continuación, abra la dimensión con la que desea trabajar.  
  
     La dimensión se abre en la pestaña **Estructura de dimensión** del Diseñador de dimensiones.  
  
2.  Arrastre el atributo que quiera usar de la jerarquía definida por el usuario desde el panel **Atributos** hasta el panel **Jerarquías** .  
  
3.  Arrastre atributos adicionales para formar niveles en la jerarquía definida por el usuario.  
  
     El orden en que se muestran los atributos en la jerarquía es importante. Por ejemplo, en una jerarquía de tiempo, los años deberían aparecer por encima de los días.  
  
4.  Opcionalmente, vuelva a ordenar los niveles de la jerarquía definida por el usuario arrastrándolos a las posiciones correctas.  
  
5.  Si lo desea, puede modificar las propiedades de la jerarquía definida por el usuario o sus niveles.  
  
     Por ejemplo, quizá quiera especificar un nombre para la jerarquía definida por el usuario, cambiar el nombre de alguno de sus niveles y definir un nombre personalizado para el nivel Todos. Para obtener más información, vea [Propiedades de jerarquía de usuario](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)y [Propiedades del nivel](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies-level-properties.md).  
  
    > [!NOTE]  
    >  De forma predeterminada, una jerarquía definida por el usuario simplemente es una ruta de acceso que permite a los usuarios profundizar para obtener información. Sin embargo, si hay relaciones entre los niveles, puede mejorar el rendimiento de las consultas configurando relaciones de atributo entre los niveles. Para obtener más información, vea [Relaciones de atributo](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md) y [Definir relaciones de atributo](../../analysis-services/multidimensional-models/attribute-relationships-define.md).  
  
### <a name="to-remove-a-user-defined-hierarchy-from-a-dimension"></a>Para quitar una jerarquía definida por el usuario de una dimensión  
  
-   En la pestaña **Estructura de dimensión** , haga clic en la jerarquía definida por el usuario que quiera quitar en el panel **Jerarquías** . En la barra de herramientas, haga clic en **Eliminar**.  
  
     — o —  
  
-   Haga clic con el botón derecho en la jerarquía definida por el usuario que quiera quitar en el panel **Jerarquías** y, después, haga clic en **Eliminar**.  
  
     — o —  
  
-   Arrastre la jerarquía definida por el usuario fuera de de la superficie de diseño.  
  
## <a name="see-also"></a>Vea también  
 [Jerarquías de usuario](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)   
 [Crear jerarquías definidas por el usuario](../../analysis-services/multidimensional-models/user-defined-hierarchies-create.md)  
  
  
