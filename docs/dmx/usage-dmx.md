---
title: Uso (DMX) | Documentos de Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- column usage [DMX]
- Data Mining Extensions [Analysis Services], column usage types
- DMX [Analysis Services], column usage types
ms.assetid: 6d7ae72a-f5b5-4744-a3a2-46ccd6432c1a
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2acfde9b8d7c9d13fc626b006116e9b3760fd432
ms.contentlocale: es-es
ms.lasthandoff: 08/02/2017

---
# <a name="usage-dmx"></a>Uso (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cuando usa extensiones de minería de datos (DMX) para definir un nuevo modelo de minería de datos en [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], debe especificar cómo el algoritmo de minería de datos que genera el modelo usará cada columna. Puede especificar los siguientes tipos para una columna:  
  
-   **Key**  
  
-   **Secuencia de teclas**  
  
-   **Clave temporal**  
  
-   **Predecir**  
  
-   **PredictOnly**  
  
 Las columnas cuyo tipo no se especifique en DMX se tratan como columnas de entrada.  
  
 Para procesar correctamente un modelo, el algoritmo debe conocer la columna de clave que identifica cada fila de manera única, la columna de destino para crear predicciones si se va a crear un modelo de predicción y las columnas que deben usarse como columnas de entrada para crear las relaciones que predicen la columna de destino.  
  
 Las columnas que se especifican como el **Predict** tipo se utilizan como columnas de entrada y salida. Las columnas que se especifican como **PredictOnly** sólo se utilizan como columnas de salida. Algunos algoritmos pueden tratar las columnas Predict de forma distinta.  
  
 Para obtener más información acerca de la columna de tipos de uso que [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] admite, consulte [columnas del modelo de minería de datos](../analysis-services/data-mining/mining-model-columns.md).  
  
## <a name="see-also"></a>Vea también  
 [Algoritmos de minería de datos &#40; Analysis Services: minería de datos &#41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Extensiones de minería de datos &#40; DMX &#41; Referencia](../dmx/data-mining-extensions-dmx-reference.md)   
 [Extensiones de minería de datos &#40; DMX &#41; Elementos de sintaxis](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Extensiones de minería de datos &#40; DMX &#41; Referencia de funciones](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Extensiones de minería de datos &#40; DMX &#41; Referencia de operadores](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Extensiones de minería de datos &#40; DMX &#41; Referencia de instrucciones](../dmx/data-mining-extensions-dmx-statements.md)   
 [Extensiones de minería de datos &#40; DMX &#41; Convenciones de sintaxis](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Funciones de predicción generales &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)   
 [Estructura y el uso de consultas de predicción DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Descripción de la instrucción Select de DMX](../dmx/understanding-the-dmx-select-statement.md)  
  
  

