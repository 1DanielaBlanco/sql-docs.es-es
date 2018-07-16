---
title: Crear una vista de suscripción (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- subscription views [Master Data Services], creating
- creating subscription views [Master Data Services]
ms.assetid: a5e28961-af16-414a-9845-d2e06aac5214
caps.latest.revision: 4
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 4d8114d933027d5392896f14c33e1ea9685841b4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37252287"
---
# <a name="create-a-subscription-view-master-data-services"></a>Crear una vista de suscripciones (Master Data Services)
  Crear una vista de suscripciones cuando desea crear una vista de los datos en el [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] base de datos para su uso en sistemas de suscripción.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para realizar este procedimiento:  
  
-   Debe disponer del permiso para tener acceso al área funcional de **Administración de integraciones** .  
  
-   Debe ser administrador de modelo. Para obtener más información, vea [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-create-a-subscription-view"></a>Crear una vista de suscripción  
  
1.  En [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], haga clic en **Administración de integraciones**.  
  
2.  En la barra de menús, haga clic en **Crear vistas**.  
  
3.  En el **vistas de suscripciones** página, haga clic en **agregar vista de suscripciones**.  
  
4.  En el **Crear vista de suscripciones** panel, en el **nombre de la vista de suscripción** , escriba un nombre para la vista.  
  
5.  En la lista **Modelo** , seleccione un modelo.  
  
6.  Seleccione el **versión** o **marca de versión** opción y, a continuación, seleccione en la lista correspondiente.  
  
    > [!TIP]  
    >  Cree una vista de suscripción basada en una marca de versión. Al bloquear una versión, puede reasignar la marca a una versión abierta sin actualizar la vista de suscripción.  
  
7.  Seleccione el **entidad** o **jerarquía derivada** opción y, a continuación, seleccione en la lista correspondiente.  
  
8.  En la lista **Formato** , seleccione un formato de vista de suscripción.  
  
9. Si elige **Niveles explícitos** o **Niveles derivados** en la lista **Formato** , escriba el número de niveles en la jerarquía que se incluirán en la vista.  
  
10. Haga clic en **Guardar**.  
  
## <a name="see-also"></a>Vea también  
 [Exportar datos &#40;Master Data Services&#41;](overview-exporting-data-master-data-services.md)   
 [Eliminar una vista de suscripciones &#40;Master Data Services&#41;](delete-a-subscription-view-master-data-services.md)   
 [Crear una marca de versión &#40;Master Data Services&#41;](create-a-version-flag-master-data-services.md)  
  
  
