---
title: "Cambiar las propiedades de un modelo de minería de datos | Documentos de Microsoft"
ms.custom: 
ms.date: 03/01/2017
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
- mining models [Analysis Services], properties
- properties [data mining]
ms.assetid: aefaeb7f-d174-48d1-a188-0987a3b1196b
caps.latest.revision: "38"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 84259428c78b013577d50b6f48818bb2cd0dc554
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="change-the-properties-of-a-mining-model"></a>Cambiar las propiedades de un modelo de minería de datos
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Algunas propiedades del modelo de minería de datos se aplican al modelo como un todo, y otras propiedades del modelo que se aplican a columnas individuales. Ejemplos de propiedades que se aplican a todo el modelo son las propiedades **Drillthrough** , que especifica si los datos de los casos deben estar disponibles para las consultas, y **Description** . Entre las propiedades que se aplican a la columna se incluyen **Usage** y **ModelingFlags**, que controlan cómo se utilizan los datos en la columna dentro del modelo.  
  
 Las propiedades del modelo siguientes disponen de editores avanzados que se pueden utilizar para crear expresiones o configurar propiedades complejas del modelo. Las propiedades siguientes proporcionan:  
  
-   Propiedad **Filter**: abre el [cuadro de diálogo Filtro de conjunto de datos o Filtro del modelo](http://msdn.microsoft.com/library/a9602174-b7e2-4e16-8ded-dfd8eb9264d7).  
  
-   Propiedad **AlgorithmParameters**: abre el [cuadro de diálogo Parámetros de algoritmo &#40;vista Modelos de minería de datos&#41;](http://msdn.microsoft.com/library/57f9f6f8-8ca4-4a6e-8f18-85f0571b7060).  
  
 Para obtener información sobre cómo configurar las propiedades de un modelo de minería de datos, vea [Columnas del modelo de minería de datos](../../analysis-services/data-mining/mining-model-columns.md).  
  
### <a name="to-change-the-properties-of-a-mining-model"></a>Para cambiar las propiedades de un modelo de minería de datos  
  
1.  En la pestaña **Modelos de minería de datos** del Diseñador de minería de datos, haga clic con el botón derecho en el encabezado de columna que contiene el nombre del modelo de minería de datos o en la fila de la cuadrícula que contiene el nombre del algoritmo de minería de datos y, después, seleccione **Propiedades**.  
  
2.  En la ventana **Propiedades** situada en el lado derecho de la pantalla, resalte el valor correspondiente a la propiedad que desee cambiar y, a continuación, escriba el nuevo valor.  
  
     El nuevo valor tendrá efecto cuando se seleccione otro elemento diferente en el diseñador.  
  
### <a name="to-change-the-properties-of-a-mining-model-column"></a>Para cambiar las propiedades de una columna del modelo de minería de datos  
  
1.  En la pestaña **Modelos de minería de datos** del Diseñador de minería de datos, haga clic con el botón derecho en la celda de cuadrícula situada en la intersección de la columna de la estructura de minería de datos con el modelo de minería de datos y, después, seleccione **Propiedades**.  
  
2.  En la ventana **Propiedades** situada en el lado derecho de la pantalla, resalte el valor correspondiente a la propiedad que desee cambiar y, a continuación, escriba el nuevo valor.  
  
    > [!NOTE]  
    >  Si el uso de la columna está establecido en **Ignore**, la ventana **Propiedades** para la columna estará en blanco.  
  
     El nuevo valor tendrá efecto cuando se seleccione otro elemento diferente en el diseñador.  
  
## <a name="see-also"></a>Vea también  
 [Tareas y procedimientos de los modelos de minería de datos](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  
