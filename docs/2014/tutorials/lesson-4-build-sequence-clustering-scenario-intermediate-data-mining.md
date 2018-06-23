---
title: 'Lección 4: Generar una secuencia de agrupación en clústeres escenario (Tutorial de minería de datos intermedios) | Documentos de Microsoft'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data mining [Analysis Services], tutorials
- sequence clustering algorithms [Analysis Services]
- tutorials [Data Mining]
ms.assetid: 63436bbd-0f73-4012-b6f1-358c81e4d92a
caps.latest.revision: 29
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 7bfa4dd3a739e81b5a7f10cda0b17452fe48c4d0
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/21/2018
ms.locfileid: "36311883"
---
# <a name="lesson-4-building-a-sequence-clustering-scenario-intermediate-data-mining-tutorial"></a>Lección 4: Generar un escenario de agrupación en clústeres de secuencia (Tutorial intermedio de minería de datos)
  El departamento de marketing de [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] desea saber cómo los clientes se mueven a través de la [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] sitio Web. La empresa cree que existe un patrón según el cual los clientes incluyen productos en las cestas de la compra. Desean analizar el orden de secuencias de compra para obtener información sobre el modo en que los clientes agregan los elementos relacionados a la cesta de la compra. Posteriormente, esta información se puede utilizar para mejorar el flujo del sitio web y propiciar que los clientes adquieran productos adicionales.  
  
 Después de completar las tareas de esta lección, habrá creado un modelo de minería de datos que use el algoritmo de clústeres de secuencia de [!INCLUDE[msCoName](../includes/msconame-md.md)] para predecir cuál será el siguiente artículo que los clientes incluirán en la cesta de la compra. Experimentará con dos versiones del modelo: una que analiza solo el orden de productos en la cesta y otra que contiene datos demográficos adicionales del cliente para la agrupación en clústeres. Finalmente, utilizará los modelos para crear predicciones que puede utilizar para recomendar productos a los clientes.  
  
 Para completar las tareas en la lección, utilizará la estructura de minería de datos market basket que creó en [lección 3: generar un escenario de cesta &#40;Tutorial intermedio de minería de datos&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md). Esta lección contiene las siguientes tareas:  
  
-   [Crear una estructura del modelo de minería de datos de clústeres de secuencia &#40;intermedio de Tutorial de minería de datos&#41;](../../2014/tutorials/create-sequence-clustering-mining-model-intermediate-data-mining.md)  
  
-   [Procesar el modelo de agrupación en clústeres de secuencia](../../2014/tutorials/processing-the-sequence-clustering-model.md)  
  
-   [Explorar el modelo de agrupación en clústeres de secuencia &#40;intermedio de Tutorial de minería de datos&#41;](../../2014/tutorials/exploring-the-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
-   [Crear un modelo de agrupación en clústeres de secuencia relacionado &#40;intermedio de Tutorial de minería de datos&#41;](../../2014/tutorials/creating-a-related-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
-   [Crear predicciones en una modelo de clústeres de secuencia &#40;intermedio de Tutorial de minería de datos&#41;](../../2014/tutorials/create-predictions-on-model-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>Siguiente tarea de la lección  
 [Crear una estructura del modelo de minería de datos de clústeres de secuencia &#40;intermedio de Tutorial de minería de datos&#41;](../../2014/tutorials/create-sequence-clustering-mining-model-intermediate-data-mining.md)  
  
## <a name="all-lessons"></a>Todas las lecciones  
 [Lección 1: Crear la solución de minería de datos intermedia &#40;intermedio de Tutorial de minería de datos&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 [Lección 2: Generar un escenario de previsión &#40;intermedio de Tutorial de minería de datos&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
 [Lección 3: Generar un escenario de cesta &#40;intermedio de Tutorial de minería de datos&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 Lección 4: Escenario de agrupación en clústeres de secuencia (tutorial intermedio de minería de datos)  
  
 [Lección 5: Generar modelos de regresión logística y Red neuronal &#40;intermedio de Tutorial de minería de datos&#41;](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Vea también  
 [Tutorial de minería de datos básicos](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Intermedio de Tutorial de minería de datos &#40;Analysis Services: minería de datos&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
  