---
title: "Editar un paquete de implementación de modelos | Documentos de Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b0fdb7d-83dd-4392-9011-4ae642c471f1
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: bcf1d714605d3f1df2e713e3e8d0311ca1440210
ms.contentlocale: es-es
ms.lasthandoff: 08/02/2017

---
# <a name="edit-a-model-deployment-package"></a>Editar un paquete de implementación de modelos
  En este tema se describe cómo implementar partes específicas de un modelo de MDS en lugar de un modelo completo. Para ello, deberá editar un paquete de modelo de MDS con el Editor de paquetes de modelo.  
  
 El asistente del Editor de paquetes de modelo le permite seleccionar las entidades, jerarquías derivadas, vistas de suscripciones y reglas de negocios de un modelo que desea incluir en un paquete de MDS para su posterior implementación. Puede dejar al margen las partes del modelo que no desea implementar. Cuando se selecciona una entidad, se seleccionan automáticamente todos los objetos dependientes de dicha entidad.  
  
 Utilice el Editor de paquetes de modelo para seleccionar partes de un modelo de un archivo de paquete creado por la herramienta MDSModelDeploy (que crea un archivo de paquete que incluye objetos y datos) o por el Asistente para la implementación de modelos (que crea un archivo que incluye solo la estructura del modelo). Después de modificar el modelo del paquete, utilice la herramienta MDSModelDeploy para implementar objetos y datos, o el Asistente para la implementación de modelos para implementar solo la estructura del modelo.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para realizar este procedimiento:  
  
-   Debe ser administrador de modelo. Para obtener más información, vea [Administradores &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   Debe existir un paquete de modelo. Para obtener más información, consulte [Implementar modelos &#40;Master Data Services&#41;](../master-data-services/deploying-models-master-data-services.md) y [Crear un paquete de implementación de modelo mediante el asistente](../master-data-services/create-a-model-deployment-package-by-using-the-wizard.md) o [Crear un paquete de implementación de modelo mediante MDSModelDeploy](../master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md).  
  
### <a name="to-edit-a-model-deployment-package"></a>Para editar un paquete de implementación de modelos  
  
1.  En el Explorador de Windows del servidor de MDS, desplácese hasta *unidad*:\Archivos de programa\Microsoft SQL Server\130\Master Data Services\Configuration.  
  
2.  Ejecute ModelPackageEditor.exe.  
  
3.  En el asistente del Editor de paquetes de modelo, haga clic en **Examinar**, desplácese a la carpeta que contiene los paquetes, seleccione un paquete y, a continuación, haga clic en **Abrir**. Haga clic en **Siguiente**.  
  
4.  Seleccione las entidades, jerarquías derivadas, vistas de suscripciones o reglas de negocios que desea implementar. Anule la selección de los elementos que no desea implementar. Haga clic en **Siguiente**.  
  
5.  Compruebe la lista de elementos que va a implementar. Si desea realizar algún cambio, haga clic en **Atrás** y repita el paso 4.  
  
6.  Haga clic en **Examinar**, desplácese a la carpeta en la que quiera guardar el paquete parcial y escriba el nombre de archivo de ese paquete (con la extensión .pkg). Haga clic en **Guardar**.  
  
7.  Haga clic en **Finalizar**.  
  
## <a name="next-steps"></a>Pasos siguientes  
  
-   [Implementar un paquete de implementación de modelo mediante el Asistente](../master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)  
  
-   [Implementar un paquete de implementación de modelo mediante MDSModelDeploy](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)  
  
  
