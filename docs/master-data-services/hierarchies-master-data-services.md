---
title: "Jerarquías (Master Data Services) | Documentos de Microsoft"
ms.custom: 
ms.date: 04/01/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hierarchies [Master Data Services]
- hierarchies [Master Data Services], about hierarchies
ms.assetid: 70dbb1fc-ead7-45be-9552-a45e3ccd8d21
caps.latest.revision: 11
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c324cb4c138d2610f33850c4e41fafead64f0bfc
ms.contentlocale: es-es
ms.lasthandoff: 08/02/2017

---
# <a name="hierarchies-master-data-services"></a>Jerarquías (Master Data Services)
  En [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], una jerarquía es una estructura en forma de árbol que se puede usar para:  
  
-   Agrupar miembros similares con fines organizativos.  
  
-   Consolidar y resumir miembros para la elaboración de informes y análisis.  
  
## <a name="what-hierarchies-contain"></a>Qué contienen las jerarquías  
 Cada jerarquía contiene todos los miembros de una o más entidades. Cuando un miembro se agrega, cambia o elimina, todas las jerarquías se actualizan. Esto garantiza que los datos sean exactos en todas las jerarquías. Las jerarquías también ayudan a asegurarse de que cada miembro se cuenta solamente una vez.  
  
 Si desea crear una agrupación de un subconjunto de miembros, considere la posibilidad de usar una colección. Para obtener más información, consulte [Collections &#40;Master Data Services&#41;](../master-data-services/collections-master-data-services.md).  
  
## <a name="kinds-of-hierarchies"></a>Tipos de jerarquías  
 Puede crear varias jerarquías para ver y organizar los miembros de diferentes maneras. Puede crear:  
  
-   Jerarquías irregulares a partir de una entidad única, que se denominan jerarquías explícitas. Para obtener más información, consulte [Explicit Hierarchies &#40;Master Data Services&#41;](../master-data-services/explicit-hierarchies-master-data-services.md).  
  
-   Jerarquías basadas en el nivel a partir de varias entidades, basándose en las relaciones existentes entre las entidades y sus atributos, que se denominan jerarquías derivadas. Para obtener más información, consulte [Derived Hierarchies &#40;Master Data Services&#41;](../master-data-services/derived-hierarchies-master-data-services.md).  
  
> [!NOTE]  
>  Todos los miembros de una jerarquía deben estar dentro del mismo modelo.  
  
## <a name="hierarchies-are-not-taxonomies"></a>Las jerarquías no son taxonomías  
 Las jerarquías son distintas a las taxonomías. Una taxonomía organiza los miembros según diversos atributos al mismo tiempo, mientras que una jerarquía organiza los miembros según un atributo cada vez. Una taxonomía puede incluir al mismo miembro varias veces, mientras que una jerarquía solo incluye un miembro una vez.  
  
 Por ejemplo, la misma bicicleta se puede incluir dos veces en una taxonomía: una vez porque sea roja y otra porque sea de la talla 38. En una jerarquía, la bicicleta solo se incluye una vez, por lo que debe decidir si mostrarla en relación con su color o su tamaño.  
  
## <a name="hierarchy-example"></a>Ejemplo de jerarquía  
 En el ejemplo siguiente, los miembros de Product se agrupan según los miembros de la subcategoría.  
  
 ![Jerarquía agrupada por subcategoría ejemplo](../master-data-services/media/mds-conc-hierarchy.gif "jerarquía agrupada por subcategoría ejemplo")  
  
## <a name="related-tasks"></a>Tareas relacionadas  
  
|Descripción de la tarea|Tema|  
|----------------------|-----------|  
|Crear una jerarquía explícita.|[Crear una jerarquía explícita &#40; Master Data Services &#41;](../master-data-services/create-an-explicit-hierarchy-master-data-services.md)|  
|Crear una jerarquía derivada.|[Crear una jerarquía derivada &#40; Master Data Services &#41;](../master-data-services/create-a-derived-hierarchy-master-data-services.md)|  
|Ocultar o eliminar niveles en una jerarquía derivada existente.|[Ocultar o eliminar niveles en una jerarquía derivada &#40; Master Data Services &#41;](../master-data-services/hide-or-delete-levels-in-a-derived-hierarchy-master-data-services.md)|  
  
## <a name="related-content"></a>Contenido relacionado  
  
-   [Jerarquías explícitas &#40; Master Data Services &#41;](../master-data-services/explicit-hierarchies-master-data-services.md)  
  
-   [Jerarquías derivadas &#40; Master Data Services &#41;](../master-data-services/derived-hierarchies-master-data-services.md)  
  
-   [Jerarquías recursivas &#40; Master Data Services &#41;](../master-data-services/recursive-hierarchies-master-data-services.md)  
  
-   [Jerarquías derivadas con límites explícitos &#40; Master Data Services &#41;](../master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)  
  
-   [Colecciones de &#40; Master Data Services &#41;](../master-data-services/collections-master-data-services.md)  
  
  

