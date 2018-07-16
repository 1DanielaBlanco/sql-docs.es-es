---
title: 'Paso 5: Agregar y configurar el origen de archivo plano | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 5c95ce51-e0fe-4fc5-95eb-2945929f2b13
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0428ffb21563c214c362d88801f79ecb5c7ed5de
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37328015"
---
# <a name="step-5-adding-and-configuring-the-flat-file-source"></a>Paso 5: Agregar y configurar el origen de archivo plano
  En esta tarea, agregará un origen de archivo plano al paquete y configurará dicho origen. Un origen de archivo plano es un componente de flujo de datos que utiliza metadatos definidos por un administrador de conexiones de archivo plano para especificar el formato y la estructura de los datos que deben extraerse del archivo plano mediante un proceso de transformación. El origen de archivo plano puede configurarse para extraer datos de un único archivo plano utilizando la definición de formato de archivo proporcionada por el administrador de conexiones de archivo plano.  
  
 Para este tutorial, configurará el origen de archivo sin formato para utilizar el `Sample Flat File Source Data` Administrador de conexiones que creó anteriormente.  
  
### <a name="to-add-a-flat-file-source-component"></a>Para agregar un componente de origen de archivo plano  
  
1.  Abra el **flujo de datos** diseñador, haciendo doble clic en el `Extract Sample Currency Data` tarea flujo de datos o haga clic en el **pestaña flujo de datos**.  
  
2.  En el **cuadro de herramientas de SSIS**, expanda **Otros orígenes**y, después, arrastre un **Origen de archivo plano** a la superficie de diseño de la pestaña **Flujo de datos** .  
  
3.  En el **de flujo de datos** superficie de diseño, haga clic en la recién agregada **Flat File Source**, haga clic en **cambiar el nombre de**y cambie el nombre a `Extract Sample Currency Data`.  
  
4.  Haga doble clic en el origen del archivo plano para abrir el cuadro de diálogo Editor de origen de archivos planos.  
  
5.  En el **Administrador de conexiones de archivos planos** cuadro, seleccione `Sample Flat File Source Data`.  
  
6.  Haga clic en **Columnas** y compruebe que los nombres de las columnas son correctos.  
  
7.  Haga clic en **Aceptar**.  
  
8.  Haga clic con el botón derecho en el origen del archivo plano y haga clic en **Propiedades**.  
  
9. En la ventana Propiedades, compruebe que la `LocaleID` propiedad está establecida en **inglés (Estados Unidos)**.  
  
## <a name="next-task-in-lesson"></a>Siguiente tarea de la lección  
 [Paso 6: Agregar y configurar transformaciones de búsqueda](lesson-1-6-adding-and-configuring-the-lookup-transformations.md)  
  
## <a name="see-also"></a>Vea también  
 [Origen de archivo plano](data-flow/flat-file-source.md)   
 [Editor del administrador de conexiones de archivos planos &#40;página General&#41;](general-page-of-integration-services-designers-options.md)  
  
  
