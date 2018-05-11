---
title: Definir grupos de miembros | Documentos de Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a23b6fa72baeee354892c254f9b000ee12a1c9ea
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
---
# <a name="attribute-properties---define-member-groups"></a>Propiedades de atributo: definir los grupos de miembros
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Si un atributo contiene muchos miembros, puede elegir agruparlos en cubos, reduciendo así el número de miembros que los usuarios ven cuando exploran los datos en una jerarquía. También puede determinar el número de cubos en los que se agrupan los miembros y establecer un esquema de nomenclatura para los cubos. Para más información, vea [Agrupar miembros de atributos &#40;Discretización&#41;](../../analysis-services/multidimensional-models/attribute-properties-group-attribute-members.md).  
  
 Los miembros se agrupan estableciendo la propiedad **DiscretizationMethod** , a la que puede obtener acceso mediante la ventana **Propiedades** de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Al crear grupos de miembros, los cambios no están a disposición de los usuarios hasta que se procesa la dimensión. Para obtener más información, vea [Procesar un modelo multidimensional &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
### <a name="to-create-member-groups"></a>Para crear grupos de miembros  
  
1.  Abra la dimensión con la que desea trabajar. De forma predeterminada, se abrirá la pestaña **Estructura de dimensión** .  
  
2.  En **Atributos**, haga clic con el botón derecho en el atributo cuyos miembros quiere agrupar y, después, haga clic en **Propiedades**.  
  
3.  En la lista desplegable junto a **DiscretizationMethod**, seleccione un método para agrupar los miembros. Para más información sobre la configuración de **DiscretizationMethod**, vea [Agrupar miembros de atributos &#40;Discretización&#41;](../../analysis-services/multidimensional-models/attribute-properties-group-attribute-members.md).  
  
  
