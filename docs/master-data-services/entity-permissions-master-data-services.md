---
title: Permisos de entidad (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: ''
ms.component: non-specific
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- entities [Master Data Services], permissions
- permissions [Master Data Services], entities
ms.assetid: 22785062-4faf-46ee-bffa-01cbd6d5a5b3
caps.latest.revision: 6
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 767f71d4bd15a40c070609828121ff7ee221b151
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="entity-permissions-master-data-services"></a>Permisos de entidad (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Los permisos de entidad se aplican a:  
  
-   Todos los atributos de la entidad, incluidos **Nombre** y **Código**, para los miembros hoja y consolidados.  
  
-   Todas las colecciones de la entidad.  
  
-   Pertenencia y relaciones de jerarquía explícita.  
  
 Cuando disponga de permisos para una entidad, podrá agregar y quitar miembros de la misma, de sus jerarquías explícitas y de sus colecciones.  
  
> [!NOTE]  
>  Estos permisos solo se aplican al área funcional del **Explorador** de la interfaz de usuario.  
  
|Permiso|Description|  
|----------------|-----------------|  
|**Lectura**|El usuario puede leer miembros, atributos, pertenencias a la jerarquía o pertenencias a la colección.|  
|**Crear**|El usuario puede crear miembros hoja y asignar valores de atributo durante la creación.|  
|**Update**|El usuario puede actualizar miembros, atributos, pertenencias a la jerarquía o pertenencias a la colección.|  
|**Eliminar**|El usuario puede eliminar miembros.|  
|**Denegar**|Denegar todo acceso a la entidad.|  
  
 Los permisos de lectura, creación, actualización y eliminación se pueden combinar. Cuando se asignan permisos de Crear, Actualizar y Eliminar, el permiso de lectura se asigna automáticamente.  
  
## <a name="see-also"></a>Ver también  
 [Asignar permisos de objeto de modelo &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Permisos de objeto del modelo &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)   
 [Entidades &#40;Master Data Services&#41;](../master-data-services/entities-master-data-services.md)  
  
  
