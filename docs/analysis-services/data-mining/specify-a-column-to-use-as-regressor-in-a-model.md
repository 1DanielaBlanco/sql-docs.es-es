---
title: Especificar una columna que se utilizan como regresor en un modelo | Documentos de Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8e0cb8e-302a-4166-9ed0-e2d9e2919b0a
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 25b142831c6b4cb1dd1afaa25734f0b0435de18c
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="specify-a-column-to-use-as-regressor-in-a-model"></a>Especificar una columna para utilizar como regresor en un modelo
  Un modelo de regresión lineal representa el valor del atributo de predicción como resultado de una fórmula que combina las entradas de manera que los datos se ajusten lo más posible a una línea de regresión estimada. El algoritmo acepta solamente valores numéricos como entradas y detecta automáticamente las entradas que proporcionan el ajuste óptimo.  
  
 Sin embargo, se puede especificar que una columna se incluya como regresor agregando el parámetro FORCE_REGRESSOR al modelo y especificando los regresores que se han de usar. Esto se puede realizar en los casos en que el atributo es significativo aunque el efecto sea demasiado bajo para ser detectado por el modelo, o cuando se desee asegurarse de que el atributo se incluya en la fórmula.  
  
 El procedimiento siguiente describe cómo crear un modelo de regresión lineal simple, utilizando los mismos datos de ejemplo que se utilizan para el [tutorial de redes neuronales](http://msdn.microsoft.com/library/42c3701a-1fd2-44ff-b7de-377345bbbd6b). El modelo no es necesariamente robusto, pero muestra cómo se usa el Diseñador de minería de datos para personalizar un modelo de regresión lineal.  
  
### <a name="how-to-create-a-simple-linear-regression-model"></a>Cómo se crea un modelo de regresión lineal simple  
  
1.  En [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], en el **Explorador de soluciones**, expanda **Estructuras de minería de datos**.  
  
2.  Haga doble clic en Call Center.dmm para abrirlo en el diseñador.  
  
3.  En el menú **Modelo de minería de datos** , seleccione **Nuevo modelo de minería de datos**.  
  
4.  Para el algoritmo, seleccione **Regresión lineal de Microsoft**. Para el nombre, escriba **Call Center Regression**.  
  
5.  En la pestaña **Modelos de minería de datos** , cambie el uso de columnas como se indica a continuación. Todas las columnas que no estén en la lista siguiente deben establecerse en **Ignore**, si no lo están.  
  
     FactCallCenterID**Key**  
  
     ServiceGrade**PredictOnly**  
  
     Total Operators**Input**  
  
     AverageTimePerIssue**Input**  
  
6.  En el menú **Modelo de minería de datos** , seleccione **Establecer parámetros de algoritmo**.  
  
7.  Para el parámetro, FORCE_REGRESSOR, en la columna **Valor** , escriba los nombres de columna ente corchetes y separados por una coma, como se indica abajo:  
  
    ```  
    [Average Time Per Issue],[Total Operators]  
    ```  
  
    > [!NOTE]  
    >  El algoritmo detectará automáticamente qué columnas son los regresores óptimos. Tan solo es necesario forzar los regresores cuando se desee asegurarse de que una columna esté incluida en la fórmula final.  
  
8.  En el menú **Modelo de minería de datos** , seleccione **Procesar modelo**.  
  
     En el visor, el modelo se representa en un solo nodo que contiene la fórmula de regresión. Se puede ver la fórmula en la **Leyenda de minería de datos**o se pueden extraer los coeficientes para la fórmula mediante el uso de consultas.  
  
## <a name="see-also"></a>Vea también  
 [Algoritmo de regresión lineal de Microsoft](../../analysis-services/data-mining/microsoft-linear-regression-algorithm.md)   
 [Consultas de minería de datos](../../analysis-services/data-mining/data-mining-queries.md)   
 [Referencia técnica del algoritmo de regresión lineal de Microsoft](../../analysis-services/data-mining/microsoft-linear-regression-algorithm-technical-reference.md)   
 [Contenido del modelo de minería de datos para los modelos de regresión lineal &#40;Analysis Services - Minería de datos&#41;](../../analysis-services/data-mining/mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)  
  
  

