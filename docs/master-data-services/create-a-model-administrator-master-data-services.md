---
title: "Crear un administrador de modelo (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "administradores [Master Data Services], crear"
ms.assetid: dae17afc-3b39-490e-b51f-2d8da26d429e
caps.latest.revision: 6
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 6
---
# Crear un administrador de modelo (Master Data Services)
  En [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], cree un administrador de modelo cuando desee que un grupo o usuario tenga todos los permisos para todos los objetos de uno o varios modelos.  
  
> [!TIP]  
>  Para simplificar la administración, cree un grupo local o de Windows, y configúrelo como adminstrator de modelo. Puede agregar usuarios al grupo y quitarlos a continuación sin tener acceso a [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
## Requisitos previos  
 Para realizar este procedimiento:  
  
-   Debe disponer de permiso para tener acceso al área funcional **Permisos de usuario y de grupo** .  
  
-   Debe ser administrador de modelo. Para obtener más información, vea [Administradores &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### Para crear un administrador de modelo  
  
1.  En [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], haga clic en **Permisos de usuario y de grupo**.  
  
2.  En la página **Usuarios** o **Grupos** , seleccione la fila para el usuario o grupo que desea modificar.  
  
3.  Haga clic en **Editar usuario seleccionado**.  
  
4.  Haga clic en la pestaña **Modelos** .  
  
5.  Si lo desea, seleccione un modelo en la lista desplegable **Modelo** .  
  
6.  Haga clic en **Editar**.  
  
7.  Haga clic en el modelo al que desea conceder el permiso.  
  
8.  En el menú, seleccione **Administrador**.  
  
9. Complete los pasos 7 y 8 con cada modelo para el que desee que administren el grupo o el usuario.  
  
10. Haga clic en **Guardar**.  
  
## Vea también  
 [Administradores &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)   
 [Asignar permisos de objeto de modelo &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Asignar los permisos de los miembros de una jerarquía &#40;Master Data Services&#41;](../master-data-services/assign-hierarchy-member-permissions-master-data-services.md)   
 [Permisos de objeto del modelo &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)   
 [Permisos de miembros de la jerarquía &#40;Master Data Services&#41;](../master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  