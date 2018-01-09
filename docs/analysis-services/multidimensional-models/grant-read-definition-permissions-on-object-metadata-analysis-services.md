---
title: "Otorgar permisos Leer definición en metatados de objetos (Analysis Services) | Documentos de Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- metadata [Analysis Services]
- permissions [Analysis Services], read metadata
- read metadata permissions
ms.assetid: c857e48e-64b0-4ffe-900d-a0a3ddafcefb
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 24e661c0ba9bd5c143365c69282e2cdae91b174a
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="grant-read-definition-permissions-on-object-metadata-analysis-services"></a>Otorgar permisos Leer definición en metatados de objetos (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Permiso para leer una definición de objeto, o sus metadatos en objetos seleccionados permite a los administradores conceder permiso para ver información sobre los objetos sin conceder también permiso para modificar la definición del objeto, modificar la estructura del objeto o ver los datos reales datos para el objeto. Los permisos de**Leer definición** se pueden conceder en los niveles de base de datos, origen de datos, dimensión, estructura de minería de datos y modelo de minería de datos. Si necesita permisos de **Leer definición** para un cubo, deberá habilitar **Leer definición** para la base de datos. Recuerde que los permisos son acumulativos. Por ejemplo, un rol otorga permisos para leer los metadatos de un cubo, mientras que otro rol otorga al mismo usuario permisos para leer los metadatos de una dimensión. Los permisos de los dos roles diferentes se combinan para conceder al usuario permiso para leer tanto los metadatos para el cubo como los metadatos para la dimensión dentro de la base de datos.  
  
> [!NOTE]  
>  El permiso para leer los metadatos de una base de datos es el mínimo necesario para conectar con una base de datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] mediante [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] o [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Un usuario que tenga permiso para leer los metadatos también puede usar el conjunto de filas del esquema DISCOVER_XML_METADATA para hacer consultas en el objeto y ver sus metadatos. Para obtener más información, vea [Conjunto de filas DISCOVER_XML_METADATA](../../analysis-services/schema-rowsets/xml/discover-xml-metadata-rowset.md).  
  
## <a name="set-read-definition-permissions-on-a-database"></a>Establecer permisos de Leer definición en una base de datos  
 Al otorgar un permiso para leer los metadatos de una base de datos, también se otorga permiso para leer los metadatos de todos los objetos de la base de datos.  
  
 Se recomienda que incluya permisos de **Leer definición** en el nivel de la base de datos cuando configure los roles para el procesamiento dedicado. Si se dispone de permisos de **Leer definición** , los usuarios que no sean administradores podrán ver la jerarquía de los objetos del modelo en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] y navegar hasta objetos individuales para procesarlos posteriormente.  
  
1.  En [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], conéctese a la instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], expanda **Roles** para la base de datos correspondiente en Explorador de objetos y, después, haga clic en un rol de base de datos (o cree un rol de base de datos).  
  
2.  En la pestaña **General** , seleccione la opción **Leer definición** .  
  
3.  En el panel **Pertenencia** , especifique las cuentas de usuario y grupo de Windows que se conectan a Analysis Services con este rol.  
  
4.  Haga clic en **Aceptar** para completar la creación del rol.  
  
## <a name="set-read-definition-permissions-on-individual-objects"></a>Establecer permisos de Leer definición en objetos individuales  
  
1.  En [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], conéctese a la instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], abra la carpeta **Bases de datos** , seleccione una base de datos, expanda **Roles** para la base de datos correspondiente en el Explorador de objetos y, después, haga clic en un rol de base de datos (o cree un rol de base de datos).  
  
2.  En el panel **General** , desactive los permisos de la base de datos para **Read Definition**. Mediante este paso se quita la funcionalidad de heredar permisos para que pueda establecer permisos en objetos individuales.  
  
3.  Seleccione el objeto para el que vaya a especificar propiedades de **Leer definición** :  
  
    -   En el panel **Orígenes de datos** , active la casilla **Leer definición** para el origen de datos. Los miembros del rol podrán ver la cadena de conexión al origen de datos, incluso el nombre del servidor y probablemente el nombre de usuario. Este permiso se encuentra disponible en caso de que quiera proporcionar información sobre la cadena de conexión, sin necesidad, por otra parte, de otorgar permisos para modificar la cadena de conexión o ver las definiciones de alguno de los objetos.  
  
    -   En el panel **Dimensiones** , active la casilla **Leer definición** para esa dimensión. Es posible que nos analistas y desarrolladores con experiencia necesiten ver la definición sin permiso para modificarla o ver las definiciones de otros objetos (como otras dimensiones, objetos de cubo o estructuras y modelos de minería de datos).  
  
    -   En el panel Estructuras de minería de datos, active la casilla **Leer definición** para estructuras o modelos de minería de datos. Es necesario disponer de**Leer definición** para explorar el modelo de datos. Para obtener más información, vea [Otorgar permisos para estructuras y modelos de minería de datos &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-permissions-on-data-mining-structures-and-models-analysis-services.md).  
  
4.  En el panel **Pertenencia** , especifique las cuentas de usuario y grupo de Windows que se conectan a Analysis Services con este rol.  
  
5.  Haga clic en **Aceptar** para completar la creación del rol.  
  
## <a name="see-also"></a>Ver también  
 [Otorgar permisos de base de datos &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-database-permissions-analysis-services.md)   
 [Otorgar permisos de procesamiento &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-process-permissions-analysis-services.md)  
  
  
