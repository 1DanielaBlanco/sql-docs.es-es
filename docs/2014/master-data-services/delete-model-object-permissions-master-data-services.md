---
title: Eliminar permisos de objeto de modelo (Master Data Services) | Microsoft Docs
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
- deleting model object permissions [Master Data Services]
- permissions [Master Data Services], deleting model object permissions
- models [Master Data Services], deleting object permissions
ms.assetid: 859c5952-f600-4940-8064-1afd13f7f6dc
caps.latest.revision: 4
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: aff62adeb15d83cdf5e543d5ecea77b70911b76c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37169142"
---
# <a name="delete-model-object-permissions-master-data-services"></a>Eliminar permisos de objeto de modelo (Master Data Services)
  En [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], elimine los permisos del objeto de modelo para quitar las asignaciones que se hayan realizado.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para realizar este procedimiento:  
  
-   Debe disponer de permiso para tener acceso al área funcional **Permisos de usuario y de grupo** .  
  
-   Debe ser administrador de modelo. Para obtener más información, vea [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-delete-model-object-permissions"></a>Eliminar permisos de objeto de modelo  
  
1.  En [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], haga clic en **Permisos de usuario y de grupo**.  
  
2.  En la página **Usuarios** o **Grupos** , seleccione la fila para el usuario o grupo que desea modificar.  
  
3.  Haga clic en **Editar usuario seleccionado**.  
  
4.  Haga clic en la pestaña **Modelos** .  
  
5.  Si lo desea, seleccione un modelo en la lista desplegable **Modelo** .  
  
6.  En el **resumen de permisos de modelo** panel, seleccione la fila para el permiso que desea eliminar.  
  
7.  Haga clic en **Eliminar permiso seleccionado**.  
  
    > [!NOTE]  
    >  No puede quitar un permiso de un usuario si se hereda de un grupo. En su lugar debe quitar el permiso del grupo.  
  
## <a name="see-also"></a>Vea también  
 [Permisos de objeto de modelo &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Asignar permisos de objeto de modelo &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)  
  
  
