---
title: "Las características de Master Data Services en desuso | Documentos de Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8506bda-66dd-45a4-bfc9-3a10fa665acc
caps.latest.revision: 18
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e4d9b433e72c916ae6611520498b0eb8fa85c8f6
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="deprecated-master-data-services-features"></a>Características en desuso de Master Data Services
  Este tema describe las características desusadas de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] que siguen estando disponibles en [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Está previsto quitar estas características en una futura versión de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Las características en desuso no se deben usar en nuevas aplicaciones.  
  
## <a name="explicit-hierarchies-collections-and-related-components"></a>Jerarquías explícitas, colecciones y componentes relacionados  
 Las jerarquías explícitas, las colecciones y los componentes relacionados están en desuso. Los miembros que antes se modelaban como tipos de miembro consolidados (primario de jerarquía explícita) y tipos de miembro de colección se modelarán como miembros hoja en jerarquías derivadas. Las siguientes características nuevas permiten que las jerarquías derivadas ocupen el lugar de las jerarquías explícitas.  
  
-   Las jerarquías derivadas recursivas ahora se pueden usar para asignar permisos de seguridad de miembro.  
  
     Una jerarquía explícita es análoga a una jerarquía derivada recursiva con un único nivel no recursivo por debajo del nivel recursivo. Una jerarquía derivada recursiva puede ser compleja mediante la inclusión de niveles por debajo y/o por encima de un nivel recursivo.  
  
-   En el Explorador, la página de jerarquía derivada muestra ahora miembros sin asignar (sin usar) para cada nivel de jerarquía. Los nodos sin usar se agrupan por nivel de la jerarquía. Los miembros se pueden mover entre los nodos sin usar y raíz, arrastrando y colocando o cortando y pegando.  
  
     En Administración del sistema, están visibles en los nodos sin usar el panel **Vista previa** . En Seguridad, los nodos sin usar se muestran en el panel **Permisos de los miembros de la jerarquía** . Se puede asignar un permiso a cualquier miembro, ya sea bajo el nodo **Raíz** o **Sin usar** . También se puede asignar permisos a los seudomiembros **Raíz**, **Sin usar**y **Sin usar** .  
  
-   El procedimiento almacenado, mdm.udpConvertCollectionAndConsolidatedMembersToLeaf, convierte jerarquías explícitas en jerarquías derivadas recursivas, y convierte miembros consolidados y de colección en miembros hoja.  
  
     Las jerarquías explícitas y los tipos de miembro consolidados y de colección se siguen admitiendo, por lo que la ejecución del procedimiento almacenado es opcional. Sin embargo, si utiliza estos elementos, se recomienda ejecutar el procedimiento almacenado porque ya están en desuso.  
  
 Para obtener información sobre jerarquías explícitas, colecciones y miembros consolidados, vea los temas siguientes.  
  
-   [Jerarquías explícitas &#40;Master Data Services&#41;](../master-data-services/explicit-hierarchies-master-data-services.md)  
  
-   [Colecciones &#40;Master Data Services&#41;](../master-data-services/collections-master-data-services.md)  
  
-   [Miembros &#40;Master Data Services&#41;](../master-data-services/members-master-data-services.md)  
  
## <a name="attribute-entity-transaction-log-type"></a>Tipo de registro de transacciones de entidad Attribute  
El tipo de registro de transacciones de entidad "Attribute" está en desuso, migre al tipo de registro de transacciones de entidad "Member". Para obtener información sobre los tipos de registro de transacciones de entidad, consulte el tema siguiente:
* [Cambio del tipo de registro de transacciones de entidad (Master Data Services)](../master-data-services/change-the-entity-transaction-log-type-master-data-services.md)
* [Historial de revisiones de miembro](../master-data-services/member-revision-history-master-data-services.md)
  
## <a name="external-resources"></a>Recursos externos  
 Entrada de blog, [Deprecated: Explicit Hierarchies and Collections](http://go.microsoft.com/fwlink/p/?LinkId=615373)(En desuso: jerarquías explícitas y colecciones), en msdn.com.  
  
## <a name="see-also"></a>Vea también  
 [Características descontinuadas de Master Data Services](../master-data-services/discontinued-master-data-services-features.md)  
  
  
