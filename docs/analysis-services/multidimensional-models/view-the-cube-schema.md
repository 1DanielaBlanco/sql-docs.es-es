---
title: Ver el esquema del cubo | Documentos de Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82fc715c-e08e-447d-8fc8-9c9005f145f0
caps.latest.revision: "8"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3a7d0c9790f0e8f624179eda86c9062d03b78887
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="view-the-cube-schema"></a>Ver el esquema del cubo
  El panel **Vista del origen de datos** de la pestaña **Estructura de cubo** del **Diseñador de cubos** muestra el esquema del cubo. El esquema es el conjunto de tablas de las que se derivan las medidas y las dimensiones de un cubo. Cada esquema de cubo se compone de una o varias tablas de hechos y una o varias tablas de dimensiones en las que se basan las medidas y las dimensiones del cubo.  
  
 El panel **Vista del origen de datos** de la pestaña **Estructura de cubo** muestra un diagrama de la vista del origen de datos en la que se basa el cubo. Este diagrama es un subconjunto del diagrama principal de la vista del origen de datos. Puede ocultar y mostrar tablas en el panel **Vista del origen de datos** y ver los diagramas existentes. Sin embargo, no puede realizar cambios (como agregar nuevas relaciones o consultas con nombre) al esquema subyacente. Para realizar cambios en el esquema, use el Diseñador de vistas del origen de datos.  
  
 Al crear un cubo, el diagrama que se muestra en el panel **Vista del origen de datos** de la pestaña **Estructura de cubo** es inicialmente el mismo que el diagrama **Mostrar todas las tablas** de la vista del origen de datos para el proyecto o la base de datos. Puede reemplazar este diagrama por cualquier diagrama existente en la vista del origen de datos y realizar ajustes en el panel **Vista del origen de datos** .  
  
 Cuando se trabaja con el diagrama en el **Diseñador de cubos**, los comandos que actúan sobre la pestaña o sobre cualquier objeto seleccionado en la pestaña están disponibles en el menú **Vista del origen de datos** . También puede hacer clic con el botón secundario en el fondo del diagrama o en cualquier objeto del diagrama para usar comandos que actúan sobre el diagrama o el objeto seleccionado. Puede hacer lo siguiente:  
  
-   Cambiar entre el formato de diagrama y el de árbol.  
  
-   Organizar, buscar, mostrar y ocultar tablas.  
  
-   Mostrar nombres descriptivos.  
  
-   Cambiar de diseño.  
  
-   Cambiar la ampliación (zoom).  
  
-   Ver las propiedades.  
  
 Además, puede realizar las acciones que se muestran en la tabla siguiente:  
  
|Para|Haga esto|  
|--------|-------------|  
|Usar un diagrama desde la vista del origen de datos del cubo|En el menú **Vista del origen de datos** , seleccione **Copiar diagrama desde**y, a continuación, haga clic en el diagrama de la vista del origen de datos que desea usar.<br /><br /> O bien<br /><br /> Haga clic con el botón derecho en el fondo del panel **Vista del origen de datos** , seleccione **Copiar diagrama desde**y, después, haga clic en el diagrama de la vista del origen de datos que prefiera. Este método crea una copia independiente del diagrama, de modo que los cambios que realice en la pestaña **Generador de cubos** no aparecen en el diagrama original.|  
|Mostrar solo las tablas usadas en el cubo|En el menú **Vista del origen de datos** , haga clic en **Mostrar solo tablas usadas**.<br /><br /> O bien<br /><br /> Haga clic con el botón derecho en el fondo del panel **Vista del origen de datos** y, después, haga clic en **Mostrar solo tablas usadas**.|  
|Editar el esquema de la vista del origen de datos|En el menú **Vista del origen de datos** , haga clic en **Editar vista del origen de datos**.<br /><br /> O bien<br /><br /> Haga clic con el botón derecho en el fondo del panel **Vista del origen de datos** y, después, haga clic en **Editar vista del origen de datos**.|  
  
  
