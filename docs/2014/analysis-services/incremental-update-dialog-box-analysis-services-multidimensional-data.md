---
title: Cuadro de diálogo actualización incremental (Analysis Services - datos multidimensionales) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.process.incrementalupdate.f1
ms.assetid: d5a5ae27-44e7-4179-b9e2-efbf21d6c5f5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 354ec6968698dc5b6a7bbca8ffcd33a34db4389d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2018
ms.locfileid: "48066285"
---
# <a name="incremental-update-dialog-box-analysis-services---multidimensional-data"></a>Cuadro de diálogo Actualización incremental (Analysis Services - Datos multidimensionales)
  Use el cuadro de diálogo **Actualización incremental** en [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] y [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] para definir la configuración que se utiliza cuando los grupos de medidas y particiones se actualizan de forma incremental. Se puede mostrar el cuadro de diálogo **Actualización incremental** haciendo clic en **Configurar** en la columna **Configuración** de la cuadrícula **Lista de objetos** del cuadro de diálogo **Procesar** .  
  
## <a name="options"></a>Opciones  
  
|Término|Definición|  
|----------|----------------|  
|**Grupo de medida**|Seleccione el grupo de medida que se va a actualizar incrementalmente.<br /><br /> Nota: Esta opción está habilitada únicamente si se está actualizando incrementalmente un cubo. Si está actualizando incrementalmente una partición o un grupo de medida, esta opción está deshabilitada.|  
|**Partición**|Seleccione la partición que se va a actualizar.<br /><br /> Nota: Esta opción está habilitada únicamente si se está actualizando incrementalmente un cubo. Si está actualizando incrementalmente una partición o un grupo de medida, esta opción está deshabilitada.|  
|**Table**|Haga clic para actualizar el objeto de una tabla.|  
|**Origen de datos o vista**|Seleccione el origen de datos o la vista del origen de datos en la que se encuentra la tabla de origen.<br /><br /> Nota: Esta opción solo está habilitada si se ha seleccionado **Tabla** .|  
|**Nombre y el esquema de tabla**|Seleccione la tabla de origen utilizada para recuperar los datos para actualizar incrementalmente el cubo, grupo de medida o partición.<br /><br /> Nota: Esta opción solo está habilitada si se ha seleccionado **Tabla** .|  
|**Consulta**|Haga clic para actualizar el objeto de una consulta.|  
|**Origen de datos**|Seleccione el origen de datos en los que se encuentran las tablas que se van a consultar.<br /><br /> Nota: Esta opción solo está habilitada si se ha seleccionado **Consulta** .|  
|**Texto de la consulta**|Escriba el texto de la consulta utilizada para recuperar los datos para actualizar incrementalmente el cubo, grupo de medida o partición.<br /><br /> Nota: Esta opción solo está habilitada si se ha seleccionado **Consulta** .|  
  
## <a name="see-also"></a>Vea también  
 [Diseñadores y cuadros de diálogo de Analysis Services &#40;datos multidimensionales&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Cuadro de diálogo procesar &#40;Analysis Services - datos multidimensionales&#41;](process-dialog-box-analysis-services-multidimensional-data.md)  
  
  
