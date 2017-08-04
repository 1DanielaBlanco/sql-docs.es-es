---
title: "Validar una versión con reglas de negocios (Master Data Services) | Documentos de Microsoft"
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
- validating versions [Master Data Services]
- validating versions [Master Data Services], about validating versions
- versions [Master Data Services], validating
- business rules [Master Data Services], applying to all members
ms.assetid: 5aee7901-6d05-41d4-8bbb-c6f26791d1df
caps.latest.revision: 8
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 036659fbe3b6cafd1272180bbd37737062ed0967
ms.contentlocale: es-es
ms.lasthandoff: 08/02/2017

---
# <a name="validate-a-version-against-business-rules-master-data-services"></a>Validar una versión con las reglas de negocios (Master Data Services)
  En [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], valide una versión para aplicar las reglas de negocios a todos los miembros de la versión del modelo.  
  
 En este procedimiento se explica cómo usar la aplicación web de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] para validar datos. Si tiene permisos en la base de datos de MDS, puede usar un procedimiento almacenado en su lugar. Para obtener más información, consulte [Validation Stored Procedure &#40;Master Data Services&#41;](../master-data-services/validation-stored-procedure-master-data-services.md).  
  
> [!NOTE]  
>  Todos los miembros deben superar la validación antes de que se pueda confirmar una versión.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para realizar este procedimiento:  
  
-   Debe disponer del permiso para tener acceso al área funcional de **Administración de versiones** .  
  
-   Debe ser administrador de modelo. Para obtener más información, vea [Administradores &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   El estado de la versión debe ser **Abrir** o **Bloqueado**.  
  
-   En la página **Validar versiones** , los miembros deben existir con un estado que no sea **Validación correcta**.  
  
### <a name="to-validate-a-version"></a>Validar una versión  
  
1.  En [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], haga clic en **Administración de versiones**.  
  
2.  En la página **Administrar versiones** , en la barra de menús, haga clic en **Validar versión**.  
  
3.  En la página **Validar versiones** , seleccione el modelo y la versión que desea validar.  
  
4.  Haga clic en **Validar**.  
  
5.  En el cuadro de diálogo de confirmación, haga clic en **Aceptar**.  
  
    > [!NOTE]  
    >  Cuando ya no se muestre el indicador de progreso, la validación de la versión habrá terminado.  
  
## <a name="next-steps"></a>Pasos siguientes  
  
-   [Bloquear una versión &#40; Master Data Services &#41;](../master-data-services/lock-a-version-master-data-services.md)  
  
## <a name="see-also"></a>Vea también  
 [Estados de validación &#40; Master Data Services &#41;](../master-data-services/validation-statuses-master-data-services.md)   
 [Almacenado de validación del procedimiento &#40; Master Data Services &#41;](../master-data-services/validation-stored-procedure-master-data-services.md)   
 [Versiones de &#40; Master Data Services &#41;](../master-data-services/versions-master-data-services.md)   
 [Las reglas de negocios &#40; Master Data Services &#41;](../master-data-services/business-rules-master-data-services.md)   
 [Validar a miembros específicos con las reglas de negocios &#40; Master Data Services &#41;](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
  
