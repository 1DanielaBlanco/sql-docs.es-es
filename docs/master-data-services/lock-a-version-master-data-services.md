---
title: "Bloquear una versión (Master Data Services) | Documentos de Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- versions [Master Data Services], locking
- locking versions [Master Data Services]
ms.assetid: 7bb62a84-12d8-4b29-9b6e-6aa25410618e
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8edd7ce020ad20917c4bdc76c636b8cf7a06fadd
ms.contentlocale: es-es
ms.lasthandoff: 08/02/2017

---
# <a name="lock-a-version-master-data-services"></a>Bloquear una versión (Master Data Services)
  En [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], bloquee una versión de un modelo para impedir cambios en los miembros del modelo y en sus atributos.  
  
> [!NOTE]  
>  Aunque se bloquee una versión, los superusuarios y administradores del modelo pueden continuar agregando, modificando y quitando miembros. Otros usuarios con permiso en el modelo solo pueden ver los miembros.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para realizar este procedimiento:  
  
-   Debe ser administrador de modelo. Para obtener más información, vea [Administradores &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   El estado de la versión debe ser **Abierta**.  
  
-   Debe disponer del permiso para tener acceso al área funcional de Administración de versiones. Para obtener más información, consulte [Permisos del área funcional &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md).  
  
### <a name="to-lock-a-version"></a>Para bloquear una versión  
  
1.  En [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], haga clic en **Administración de versiones**.  
  
2.  En la página **Administrar versiones** , seleccione la fila de la versión que desea bloquear.  
  
3.  Haga clic en **Bloquear**.  
  
4.  En el cuadro de diálogo de confirmación, haga clic en **Aceptar**.  
  
## <a name="next-steps"></a>Pasos siguientes  
  
-   [Validar una versión con las reglas de negocios &#40; Master Data Services &#41;](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
-   [Confirmar una versión &#40; Master Data Services &#41;](../master-data-services/commit-a-version-master-data-services.md)  
  
## <a name="see-also"></a>Vea también  
 [Versiones de &#40; Master Data Services &#41;](../master-data-services/versions-master-data-services.md)   
 [Desbloquear una versión &#40; Master Data Services &#41;](../master-data-services/unlock-a-version-master-data-services.md)  
  
  
