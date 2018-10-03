---
title: Crear un paquete de implementación de modelo mediante MDSModelDeploy | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
ms.assetid: c2687e39-dc20-494f-a707-2aa29f4c329e
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: a9df35b685d9814636acaa194d5cb30741e9b994
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2018
ms.locfileid: "48122765"
---
# <a name="create-a-model-deployment-package-by-using-mdsmodeldeploy"></a>Crear un paquete de implementación de modelo mediante MDSModelDeploy
  En [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], utilice la herramienta MDSModelDeploy para crear un paquete. Dependiendo de los comandos que especifique, el paquete puede contener:  
  
-   Solo objetos de modelo.  
  
-   Objetos de modelo y datos.  
  
 Si desea implementar un paquete que solo contiene objetos de modelo, puede usar en su lugar el Asistente para la implementación de modelos en la aplicación web de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Para obtener más información, consulte [Crear un paquete de implementación de modelo mediante el asistente](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md).  
> [!NOTE]  
> Esta versión de la herramienta MDSModelDeploy no puede usar más de gigabytes (GB) de memoria. Al crear o implementar modelos grandes mediante **objetos y datos de modelo** opción, puede experimentar errores de "Stream era demasiado larga" o "memoria insuficiente". Para resolver este problema, utilice para implementar los datos; de ensayo de MDS o actualizar a 2016 MDS o una versión posterior, que incluye la versión actualizada de la herramienta MDSModelDeploy.
## <a name="prerequisites"></a>Requisitos previos  
 Para realizar este procedimiento:  
  
1.  Los permisos básicos necesarios para ejecutar la herramienta de MDSModelDeploy son los siguientes:  
  
    -   El mismo permiso de Windows que para el administrador de configuración de MDS (administrador de Windows)  
  
    -   Permiso DBA en la base de datos de MDS.  
  
2.  Los permisos necesarios para crear el paquete mediante la herramienta MDSModelDeploy son los siguientes:  
  
    -   Permiso de administrador de modelo MDS en el modelo de datos.  
  
    -   Permiso de la función de administración de integraciones de MDS.  
  
3.  Los permisos necesarios para implementar un modelo mediante la herramienta MDSModelDeploy son los siguientes:  
  
    -   Permiso de la función de explorador de MDS  
  
    -   Permiso de la función de administración de integraciones de MDS  
  
    -   Permiso de la función de administración del sistema de MDS.  
  
4.  Los permisos necesarios para mostrar modelos mediante la herramienta MDSModelDeploy son los siguientes:  
  
    -   Permiso de la función de explorador de MDS  
  
    -   Permiso de administrador de modelos de MDS en el modelo de datos en orden para ver el modelo en la lista.  
  
 Debe existir un modelo para que se pueda crear un paquete del mismo. Para obtener más información, consulte [Crear un modelo &#40;Master Data Services&#41;](create-a-model-master-data-services.md).  
  
 Para obtener más información, vea [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).  
  
### <a name="to-create-a-model-deployment-package-by-using-mdsmodeldeploy"></a>Para crear un paquete de implementación de modelo mediante MDSModelDeploy  
  
1.  Abra un símbolo del sistema.  
  
2.  Navegue a la ubicación de MDSModelDeploy.exe.  
  
    -   Si MDS se instaló en la ubicación predeterminada, el archivo está en *unidad*: \Program Files\Microsoft SQL Server\120\Master Data Services\Configuration.  
  
    -   Si MDS no se instaló en la ubicación predeterminada, busque en el equipo local MDSModelDeploy.exe.  
  
3.  Opcional. Vea las opciones y la Ayuda.  
  
    -   Para mostrar todas las opciones disponibles, escriba `MDSModelDeploy` y presione Entrar.  
  
    -   Para mostrar la ayuda de una opción, escriba lo siguiente, donde *OptionName* es el nombre de la opción: `MDSModelDeploy help OptionName`.  
  
4.  Opcional. Si tiene varias aplicaciones web, determine el nombre del servicio en el que vaya a hacer las implementaciones; para ello, escriba este comando y presione ENTRAR:  
  
    ```  
    MDSModelDeploy listservices  
    ```  
  
     Se devuelve una lista de valores, por ejemplo `MDS1, Default Web Site, MDS`. El primer valor de esta lista (en este caso, `MDS1`) es necesario para implementar el modelo.  
  
5.  Para crear un paquete que contenga objetos de modelo y datos, escriba lo siguiente, donde *ModelName*, *VersionName*, *ServiceName*y *PackageName* son los nombres del modelo, la versión, el servicio y el archivo de salida .pkg, respectivamente:  
  
    ```  
    MDSModelDeploy createpackage -model ModelName -version VersionName -service ServiceName -package PackageName -includedata  
    ```  
  
     Si no desea incluir datos, no utilice los modificadores `-version` y `-includedata` .  
  
6.  Presione ENTRAR. Cuando el paquete se crea correctamente, se muestra un mensaje que indica que “la operación de MDSModelDeploy se completó correctamente”.  
  
## <a name="next-steps"></a>Pasos siguientes  
  
-   [Implementar un paquete de implementación de modelo mediante MDSModelDeploy](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)  
  
## <a name="see-also"></a>Vea también  
 [Opciones de implementación de modelos &#40;Master Data Services&#41;](../../2014/master-data-services/model-deployment-options-master-data-services.md)   
 [Implementación de modelos &#40;Master Data Services&#41;](../../2014/master-data-services/deploying-models-master-data-services.md)  
  
  
