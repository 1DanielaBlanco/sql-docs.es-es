---
title: Ventana Resultados espaciales | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2d5a477-6496-4d01-adee-7322ebdfadf3
caps.latest.revision: 8
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 66e1a9e14b4a786e6ca45a9ab0e761975563c415
ms.contentlocale: es-es
ms.lasthandoff: 04/11/2017

---
# <a name="spatial-results-window"></a>Ventana Resultados espaciales
  La ventana **Resultados espaciales** proporciona herramientas de asignación visual para ver los datos espaciales. Para ver los resultados espaciales, los resultados de la consulta deben incluir una columna espacial con datos de geometría o de geografía.  
  
> [!NOTE]  
>  La ventana **Resultados espaciales** solo está disponible si los resultados se devuelven a una cuadrícula en la ventana **Resultados** . Si especifica que los resultados se deben devolver como texto, esta ventana no está disponible.  
  
## <a name="options"></a>Opciones  
 **Seleccionar columna espacial**  
 Especifique la columna espacial que desea ver en las columnas espaciales de los resultados de la consulta. Solo puede seleccionarse una columna cada vez.  
  
 **Seleccionar columna de etiqueta**  
 Especifique la columna no espacial en las columnas devueltas en los resultados de la consulta para etiquetar los datos espaciales. Solo puede seleccionarse una columna cada vez.  
  
 Esta opción no está disponible si solo se devuelven instancias de punto en una consulta.  
  
 **Seleccionar proyección**  
 Muestre los datos de geografía en una de estas cuatro proyecciones: Equirectangular, Mercator, Robinson o Bonne.  
  
 Esta opción no está disponible para los datos de geometría.  
  
 **Zoom**  
 Ajuste la presentación del mapa en una escala exponencial.  
  
 **Mostrar líneas de cuadrícula**  
 Activa o desactiva las líneas de cuadrícula de coordenadas.  
  
 En las formas de polígono, la etiqueta solo se muestra cuando la forma es lo suficientemente grande como para contener el texto del rótulo. Si desea mostrar las etiquetas para las formas pequeñas, ajuste el zoom.  
  
> [!NOTE]  
>  Las instancias de punto no se pueden etiquetar.  
  
## <a name="see-also"></a>Vea también  
 [Ver datos espaciales en el Explorador de objetos](../../relational-databases/scripting/view-spatial-data-in-object-explorer.md)   
 [Datos espaciales &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)   
 [Editor de consultas del motor de base de datos &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)   
 [Editores de consultas y texto &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)  
  
  
