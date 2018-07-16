---
title: Ubicación de almacenamiento de base de datos | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- databases [Analysis Services], storage location
ms.assetid: cf88c62e-581e-42f2-846f-a9bf1d7c3292
caps.latest.revision: 18
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c62d463a424c1e5245a7b5f5a36e9d7a99fe7c9e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37234255"
---
# <a name="database-storage-location"></a>Ubicación de almacenamiento de las bases de datos
  Con frecuencia se producen situaciones en las que un administrador de bases de datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] desea que una base de datos determinada resida fuera de la carpeta de datos del servidor. Estas situaciones suelen responder a necesidades empresariales, como mejorar el rendimiento o ampliar la capacidad de almacenamiento. Para estas situaciones, el `DbStorageLocation` habilita la propiedad de base de datos la [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dba para especificar la ubicación de la base de datos en un dispositivo de disco o de red local.  
  
## <a name="dbstoragelocation-database-property"></a>Propiedad de base de datos DbStorageLocation  
 El `DbStorageLocation` propiedad de base de datos especifica la carpeta donde [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] crea y administra todos los datos y metadatos de archivos base. Todos los archivos de metadatos se almacenan en el `DbStorageLocation` carpeta, excepto el archivo de metadatos de la base de datos, que se almacena en la carpeta de datos del servidor. Hay dos consideraciones importantes al establecer el valor de `DbStorageLocation` propiedad de base de datos:  
  
-   El `DbStorageLocation` propiedad de base de datos debe establecerse en una ruta UNC de carpeta existente o una cadena vacía. De manera predeterminada, la carpeta de datos del servidor es una cadena vacía. Si la carpeta no existe, se producirá un error al ejecutar un `Create`, `Attach`, o `Alter` comando.  
  
-   El `DbStorageLocation` no se puede establecer la propiedad de base de datos para que apunte a la carpeta de datos del servidor o cualquiera de sus subcarpetas. Si la ubicación apunta a la carpeta de datos del servidor o a cualquiera de sus subcarpetas, se producirá un error al ejecutar un comando `Create`, `Attach` o `Alter`.  
  
> [!IMPORTANT]  
>  Se recomienda que establezca la ruta UNC para utilizar una red SAN, una red basada en iSCSI o un disco local adjunto. Cualquier ruta UNC a un recurso compartido de red o a una solución de almacenamiento remoto de latencia conduce a una instalación no compatible.  
  
### <a name="dbstoragelocation-compared-to-storagelocation"></a>Comparación entre DbStorageLocation y StorageLocation  
 `DbStorageLocation` especifica la carpeta en que residen todos los archivos de datos y de metadatos de la base de datos, mientras que `StorageLocation` especifica la carpeta en que residen una o varias particiones de un cubo. `StorageLocation` se puede establecer independientemente de `DbStorageLocation`. La decisión al respecto la toma el administrador de bases de datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] basándose en los resultados esperados, y muchas veces se usarán ambas propiedades de forma simultánea.  
  
## <a name="dbstoragelocation-usage"></a>Uso de DbStorageLocation  
 El `DbStorageLocation` propiedad de base de datos se utiliza como parte de un `Create` comando en la base de datos un `Detach` / `Attach` secuencia de comandos de base de datos, en un `Backup` / `Restore` secuencia de comandos de base de datos , o en un `Synchronize` comando de base de datos. El cambio de la propiedad de base de datos `DbStorageLocation` se considera un cambio estructural en el objeto de base de datos. Esto significa que deben crearse de nuevo todos los metadatos y volverse a procesar los datos.  
  
> [!IMPORTANT]  
>  No debe cambiar la ubicación de almacenamiento de las bases de datos con un comando `Alter`. En su lugar, se recomienda que use una secuencia de `Detach` / `Attach` comandos de base de datos (consulte [mover una base de datos de Analysis Services](move-an-analysis-services-database.md), [adjuntar y separar Analysis Services Databases](attach-and-detach-analysis-services-databases.md)).  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.AnalysisServices.Database.DbStorageLocation%2A>   
 [Adjuntar y separar bases de datos de Analysis Services](attach-and-detach-analysis-services-databases.md)   
 [Mover una base de datos de Analysis Services](move-an-analysis-services-database.md)   
 [Elemento DbStorageLocation](../xmla/xml-elements-properties/dbstoragelocation-element.md)   
 [Crear elemento &#40;XMLA&#41;](../xmla/xml-elements-commands/create-element-xmla.md)   
 [Elemento Attach](../xmla/xml-elements-commands/attach-element.md)   
 [Elemento Synchronize &#40;XMLA&#41;](../xmla/xml-elements-commands/synchronize-element-xmla.md)  
  
  
