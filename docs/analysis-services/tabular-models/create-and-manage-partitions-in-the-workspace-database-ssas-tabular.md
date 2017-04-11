---
title: "Crear y administrar particiones en la base de datos del &#225;rea de trabajo (SSAS tabular) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.asvs.bidtoolset.partitionmgr.f1"
ms.assetid: 0b3027d6-652b-4eb3-a197-58b25df65218
caps.latest.revision: 15
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 15
---
# Crear y administrar particiones en la base de datos del &#225;rea de trabajo (SSAS tabular)
  Las particiones dividen una tabla en partes lógicas. A continuación, cada partición se puede procesar (actualizar) de forma independiente o en paralelo con otras particiones. Las particiones pueden mejorar la escalabilidad y facilitar el uso de bases de datos grandes. De forma predeterminada, cada tabla tiene una partición que incluye todas las columnas. Las tareas de este tema explican cómo crear y administrar particiones en la base de datos del área de trabajo del modelo mediante el cuadro de diálogo **Administrador de particiones** de [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]  
  
 Una vez implementado un modelo en otra instancia de Analysis Services, los administradores de bases de datos pueden crear y administrar las particiones del modelo (implementado) mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Para más información, vea [Crear y administrar particiones de modelos tabulares &#40;SSAS tabular&#41;](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md).  
  
 En este tema se incluyen las tareas siguientes:  
  
-   [Para crear una partición](#bkmk_create_new)  
  
-   [Para copiar una partición](#bkmk_copy)  
  
-   [Para eliminar una partición](#bkmk_delete)  
  
> [!NOTE]  
>  No es posible mezclar particiones en la base de datos del área de trabajo del modelo usando el cuadro de diálogo Administrador de particiones. Solamente se pueden mezclar particiones en un modelo implementado mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## Tareas  
 Para crear y administrar particiones, deberá usar el cuadro de diálogo **Administrador de particiones** . Para ver el cuadro de diálogo **Administrador de particiones** , en [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], haga clic en el menú **Tabla** y en **Particiones**.  
  
###  <a name="bkmk_create_new"></a> Para crear una partición  
  
1.  En el diseñador de modelos, seleccione la tabla en la que desea definir una partición.  
  
2.  Haga clic en el menú **Tabla** y en **Particiones**.  
  
3.  En **Administrador de particiones**, en el cuadro de lista **Tabla** , compruebe o seleccione la tabla en la que desea crear particiones y, a continuación, haga clic en **Nuevo**.  
  
4.  En **Nombre de partición**, escriba un nombre para la partición. De forma predeterminada, el nombre de la partición predeterminada se incrementará numéricamente para cada nueva partición.  
  
5.  Puede seleccionar las filas y las columnas que se incluirán en la partición mediante el modo de vista previa de tabla o mediante una consulta SQL creada con el Editor de consultas.  
  
     Para usar el modo de vista previa de tabla (valor predeterminado), haga clic en el botón **Vista previa de tabla** cerca de la esquina superior derecha de la ventana de vista previa. Seleccione las columnas que desea incluir en la partición activando la casilla situada junto al nombre de cada columna. Para filtrar las filas, haga clic con el botón secundario en un valor de celda y, a continuación, haga clic en **Filtrar por valor de celda seleccionado**.  
  
     Para usar una instrucción SQL, haga clic en el botón **Editor de consultas** cerca de la esquina superior derecha de la ventana de vista previa y, después, escriba o pegue una instrucción de consulta SQL en la ventana de consulta. Para validar la instrucción, haga clic **Validar**. Haga clic en **Diseño**para abrir el Diseñador de consultas.  
  
###  <a name="bkmk_copy"></a> Para copiar una partición  
  
1.  En **Administrador de particiones**, en el cuadro de lista **Tabla** , compruebe o seleccione la tabla que contiene la partición que desea copiar.  
  
2.  En la lista **Particiones** , seleccione la partición que desea copiar y haga clic en **Copiar**.  
  
3.  En **Nombre de partición**, escriba un nuevo nombre para la partición.  
  
###  <a name="bkmk_delete"></a> Para eliminar una partición  
  
1.  En **Administrador de particiones**, en el cuadro de lista **Tabla** , compruebe o seleccione la tabla que contiene la partición que desea eliminar.  
  
2.  En la lista **Particiones** , seleccione la partición que desea eliminar y haga clic en **Eliminar**.  
  
## Vea también  
 [Particiones &#40;SSAS tabular&#41;](../../analysis-services/tabular-models/partitions-ssas-tabular.md)   
 [Procesar particiones en la base de datos del área de trabajo &#40;SSAS tabular&#41;](../../analysis-services/tabular-models/process-partitions-in-the-workspace-databse-ssas-tabular.md)  
  
  