---
title: "Agregar columnas a una estructura de miner&#237;a de datos | Microsoft Docs"
ms.custom: ""
ms.date: "03/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "estructuras de minería de datos [Analysis Services], columnas"
  - "columnas [minería de datos], columnas de estructura de minería de datos"
  - "agregar columnas"
ms.assetid: 3f879344-9f66-4178-851a-e8c5ccccf4cb
caps.latest.revision: 30
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 30
---
# Agregar columnas a una estructura de miner&#237;a de datos
  Utilice el Diseñador de minería de datos de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] para agregar columnas a una estructura de minería de datos después de definirla en el Asistente para minería de datos. Puede agregar cualquier columna existente en la vista de origen que se haya utilizado para definir la estructura de minería de datos.  
  
> [!NOTE]  
>  Puede agregar varias copias de una columna a una estructura de minería de datos; sin embargo, no debería utilizar más de una copia de la columna dentro del mismo modelo para evitar las correlaciones falsas entre la columna de origen y la derivada.  
  
### Para agregar una columna a una estructura de minería de datos  
  
1.  Seleccione la pestaña **Estructura de minería de datos** en el Diseñador de minería de datos.  
  
2.  Haga clic con el botón derecho en la estructura de minería de datos y seleccione **Agregar una columna**.  
  
     Se abrirá el cuadro de diálogo **Seleccionar una columna** .  
  
3.  En **Tabla de origen**, seleccione la tabla de la vista del origen de datos en la que reside la columna.  
  
4.  En **Columna de origen**, seleccione la columna que desee agregar a la estructura de minería de datos.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
> [!NOTE]  
>  Si agrega una columna que ya existe, se incluirá una copia en la estructura con el número "1" adjuntado al nombre. Para cambiar el nombre de la columna copiada a algo más descriptivo, escriba un nuevo nombre en la propiedad **Name** de la columna de la estructura de minería de datos.  
  
## Vea también  
 [Tareas y procedimientos de las estructuras de minería de datos](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  