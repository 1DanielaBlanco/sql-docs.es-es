---
title: Palabras reservadas (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- reserved words [Master Data Services]
- Master Data Services, reserved words
ms.assetid: 88afd0d0-4362-4394-8357-4e65388fc0fc
caps.latest.revision: 11
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 3386a8c4a37aafd747dd61bb37f3464c0c8efa56
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38003637"
---
# <a name="reserved-words-master-data-services"></a>Palabras reservadas (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  En [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], al crear objetos del modelo o miembros, algunas palabras no se pueden usar. Su uso puede producir errores.  
  
> [!NOTE]  
>  También debe limitar el uso de caracteres especiales (símbolos, guiones, etc.).  
  
-   [Modelos](../master-data-services/reserved-words-master-data-services.md#models)  
  
-   [Entidades](../master-data-services/reserved-words-master-data-services.md#entities)  
  
-   [Jerarquías explícitas](../master-data-services/reserved-words-master-data-services.md#exhierarchies)  
  
-   [Atributos](../master-data-services/reserved-words-master-data-services.md#attributes)  
  
-   [Miembros](../master-data-services/reserved-words-master-data-services.md#members)  
  
##  <a name="models"></a> Modelos  
 Si crea un modelo con el nombre establecido en **Name** o **Code**, no seleccione **Crear entidad con el mismo nombre que el modelo** porque **Name** o **Code** no se puede usar para el nombre de una entidad.  
  
##  <a name="entities"></a> Entidades  
 Para los nombres de entidad, no puede usar **Name** o **Code**.  
  
##  <a name="exhierarchies"></a> Jerarquías explícitas  
 Para los nombres de jerarquía explícita, no puede utilizar **Name** o **Code**.  
  
##  <a name="attributes"></a> Atributos  
  
-   **ID**  
  
-   **Code**  
  
-   **EnterUserName**  
  
-   **LastChgUserName**  
  
-   **Nombre**  
  
-   **EnterDTM**  
  
-   **EnterUserID**  
  
-   **EnterUserName**  
  
-   **LastChgDTM**  
  
-   **LastChgUserID**  
  
-   **Status_ID**  
  
-   **ValidationStatus_ID**  
  
-   **Version_ID**  
  
##  <a name="members"></a> Miembros  
 Para los miembros, no puede usar **MDMMemberStatus**, **MDMUnused**o **ROOT** para el valor de atributo **Code** .  
  
## <a name="see-also"></a>Ver también  
 [Introducción a Master Data Services &#40;MDS&#41;](../master-data-services/master-data-services-overview-mds.md)  
  
  
