---
title: Ver el historial del proyecto | Documentos de Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- viewing project history
- version control services [SQL Server], project history
- projects [SQL Server Management Studio], historical information
- historical information [SQL Server], projects
ms.assetid: be0ea2ac-4a35-429c-9c9e-4001ea9035a4
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d99c3a27a74d41efc895489a8690d735dadd3b4f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36199505"
---
# <a name="view-project-history"></a>Ver el historial del proyecto
  El historial de un proyecto de [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe (VSS) incluye una lista de todas las acciones realizadas en cada uno de los archivos de ese proyecto, incluida la creación, la adición, la eliminación y la recuperación de un archivo.  
  
> [!NOTE]  
>  Normalmente, se suele hacer referencia a un proyecto de Visual SourceSafe como la carpeta del servidor de control de código fuente, la ubicación en la que la versión del servidor de un archivo controlado por código fuente está almacenada en el servidor.  
  
 Puede utilizar [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] para examinar el historial del proyecto de Visual SourceSafe al que pertenece la solución cargada. Según la información mostrada como parte del historial de un proyecto, puede recuperar copias locales de las versiones del archivo, restaurar versiones eliminadas o compartir una versión entre proyectos.  
  
### <a name="to-view-the-history-of-a-vss-project"></a>Para ver el historial de un proyecto de VSS  
  
1.  En el Explorador de soluciones, seleccione el proyecto.  
  
2.  En el **archivo** menú, elija **Control de código fuente** y haga clic en **Ver historial**.  
  
3.  En el **historial de** \<proyecto > diálogo cuadro, realice cualquiera de las siguientes acciones:  
  
    -   Ver la copia del sistema de control de código fuente de un archivo seleccionado.  
  
    -   Ver información detallada acerca de un archivo seleccionado.  
  
    -   Recuperar un archivo seleccionado en el disco local.  
  
    -   Desproteger un archivo seleccionado.  
  
    -   Compartir un archivo seleccionado entre dos proyectos de control de código fuente.  
  
    -   Exportar el informe de historial a una impresora, a un archivo o al Portapapeles.  
  
## <a name="see-also"></a>Vea también  
 [Establecer y recuperar información de versión](../../2014/database-engine/set-and-retrieve-version-information.md)   
 [Ver el estado de archivo](../../2014/database-engine/view-file-status.md)   
 [Recuperar archivos](../../2014/database-engine/retrieve-files.md)   
 [Comparar archivos](../../2014/database-engine/compare-files.md)  
  
  