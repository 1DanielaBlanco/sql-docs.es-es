---
title: "Lecci&#243;n 13: Analizar en Excel | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: ce717071-193b-4c99-9654-c7a613e16327
caps.latest.revision: 22
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Lecci&#243;n 13: Analizar en Excel
En esta lección, usará la característica Analizar en Excel de [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] para abrir Microsoft Excel, crear automáticamente una conexión de origen de datos al área de trabajo del modelo y agregará automáticamente una tabla dinámica a la hoja de cálculo. La característica Analizar en Excel se ha diseñado para proporcionar una manera rápida y sencilla de probar la eficacia del diseño de su modelo antes de implementarlo. No realizará ningún análisis de datos en esta lección. El propósito de esta lección es familiarizar al autor de modelos con las herramientas que puede usar para probar el diseño de sus modelos. Los usuarios finales no utilizarán la característica Analizar de Excel, que está destinada a los autores de modelos, sino que usarán aplicaciones de informes de cliente como Excel o [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] para conectarse a los datos del modelo implementados y explorarlos.  
  
Para completar esta lección, Excel se debe instalar en el mismo equipo que [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]. Para obtener más información, consulte [Analizar en Excel &#40;SSAS tabular&#41;](../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md).  
  
Tiempo estimado para completar esta lección: **20 minutos**  
  
## Requisitos previos  
Este tema es parte de un tutorial de creación de modelos tabulares, que se debe completar en orden. Antes de realizar las tareas de esta lección, debe haber completado la lección anterior: [Lección 11: Crear particiones](../analysis-services/lesson-11-create-partitions.md).  
  
## Examinar utilizando las perspectivas Predeterminada y Venta por Internet  
En estas primeras tareas, examinará su modelo con la perspectiva predeterminada, que incluye todos los objetos del modelo, y también con la perspectiva Venta por Internet que creó en la lección 8: Crear perspectivas. La perspectiva Venta por Internet excluye el objeto de tabla Cliente.  
  
#### Para examinar con la perspectiva predeterminada  
  
1.  En [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], haga clic en el menú **Modelo** y después en **Analizar en Excel**.  
  
2.  En el cuadro de diálogo **Analizar en Excel**, haga clic en **Aceptar**.  
  
    Excel se abrirá con un libro nuevo. Se crea una conexión de origen de datos con la cuenta de usuario actual y se utiliza la perspectiva predeterminada para definir los campos visibles. Se agrega automáticamente una tabla dinámica a la hoja de cálculo.  
  
3.  En Excel, en **Lista de campos de tabla dinámica**, observe que aparecen los grupos de medida **Fecha** y **Venta por Internet**, así como las tablas **Cliente**, **Fecha**, **Geografía**, **Producto**, **Categoría del producto**, **Subcategoría del producto** y **Venta por Internet** con todas sus columnas respectivas.  
  
4.  Cierre Excel sin guardar el libro.  
  
#### Para examinar con la perspectiva Venta por Internet  
  
1.  En [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], haga clic en el menú **Modelo** y después en **Analizar en Excel**.  
  
2.  En el cuadro de diálogo **Analizar en Excel**, mantenga seleccionado **Usuario de Windows actual** y, después, en el cuadro de lista desplegable **Perspectiva**, seleccione **Venta por Internet** y haga clic en **Aceptar**. Se abre Excel.  
  
3.  En Excel, en la **Lista de campos de tabla dinámica**, observe que la tabla Cliente se ha excluido de la lista de campos.  
  
4.  Cierre Excel sin guardar el libro.  
  
## Examinar con roles  
Los roles son una parte integral de cualquier modelo tabular. Sin al menos un rol, al que se agregan usuarios en calidad de miembros, los usuarios no podrán tener acceso a los datos ni analizarlos con el modelo. La característica Analizar de Excel proporciona una manera de probar los roles que ha definido.  
  
#### Para examinar con el rol de usuario Administrador de ventas por Internet  
  
1.  En [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], haga clic en el menú **Modelo** y después en **Analizar en Excel**.  
  
2.  En el cuadro de diálogo **Analizar en Excel**, en **Especifique el nombre de usuario o rol que se va a usar al conectarse al modelo**, seleccione **Rol** y, después, en el cuadro de lista desplegable, seleccione **Administrador de ventas por Internet** y haga clic en **Aceptar**.  
  
    Excel se abrirá con un libro nuevo. Se crea automáticamente una tabla dinámica. La lista de campos de tabla dinámica incluye todos los campos de datos disponibles en su nuevo modelo.  
      
3.  Cierre Excel sin guardar el libro.  
  
## Pasos siguientes  
Para continuar este tutorial, vaya a la lección siguiente: [Lección 14: Implementar](../analysis-services/lesson-14-deploy.md).  
  
  
  
