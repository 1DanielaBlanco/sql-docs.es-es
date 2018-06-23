---
title: Crear una secuencia de agrupación en clústeres de la estructura del modelo de minería de datos (Tutorial de minería de datos intermedios) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e9339227-6c2e-4c4b-8be2-8c1960bc4a8d
caps.latest.revision: 40
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 09aaac50873d6c4c63b46fdf37dd7ee854000886
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312703"
---
# <a name="creating-a-sequence-clustering-mining-model-structure-intermediate-data-mining-tutorial"></a>Crear una estructura del modelo de minería de datos de agrupación en clústeres de secuencia (Tutorial intermedio de minería de datos)
  El primer paso para crear un modelo de minería de datos de agrupación en clústeres de secuencia es utilizar el Asistente para minería de datos con el objeto de crear una nueva estructura de minería de datos y un modelo de minería basados en el algoritmo de clústeres de secuencia de [!INCLUDE[msCoName](../includes/msconame-md.md)].  
  
 Utilizará la misma vista del origen de datos que utilizó para el análisis de la cesta de la compra, pero agregará una columna que contenga el identificador `sequence`. En este escenario, la secuencia significa el orden en el que el cliente agregó los elementos a la cesta de la compra.  
  
 También agregará algunas columnas que se utilizan en uno de los modelos para agrupar los clientes por datos demográficos.  
  
### <a name="to-create-a-sequence-clustering-structure-and-model"></a>Para crear un modelo y una estructura de agrupación en clústeres de secuencia  
  
1.  En el Explorador de soluciones en [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], haga clic en **estructuras de minería de datos** y seleccione **nueva estructura de minería de datos**.  
  
2.  En la página de inicio del **Asistente para minería de datos** , haga clic en **Siguiente**.  
  
3.  En el **seleccionar el método de definición** , comprueba que **de almacén de datos o base de datos relacional existente** está seleccionada y, a continuación, haga clic en **siguiente**.  
  
4.  En el **crear la estructura de minería de datos** , comprueba que la opción **crear la estructura de minería de datos con un modelo de minería de datos** está seleccionada. A continuación, haga clic en la lista desplegable para la opción **¿qué técnica de minería de datos que desea usar?** y seleccione **Microsoft Sequence Clustering**. Haga clic en **Siguiente**.  
  
     El **seleccionar vista del origen de datos** aparecerá la página. En **vistas del origen de datos disponibles**, seleccione `Orders`.  
  
     Orders es la misma vista del origen de datos que utilizó para el escenario de la cesta de la compra. Si no ha creado esta vista del origen de datos, vea [agregar una vista del origen de datos con tablas anidadas &#40;Tutorial intermedio de minería de datos&#41;](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md).  
  
5.  Haga clic en **Siguiente**.  
  
6.  En el **especificar tipos de tablas** página, seleccione la **caso** casilla de verificación junto a la **vAssocSeqOrders** de tabla y seleccione la **Nested** casilla de verificación junto a la **vAssocSeqLineItems** tabla. Haga clic en **Siguiente**.  
  
    > [!NOTE]  
    >  Si se produce un error cuando se selecciona el **caso** o **Nested** casillas de verificación, es posible que la combinación en la vista del origen de datos no es correcta. La tabla anidada, **vAssocSeqLineItems**, debe estar conectado a la tabla de casos, **vAssocSeqOrders,** por una combinación de varios a uno. Puede modificar la relación haciendo clic con el botón secundario en la línea de combinación e invirtiendo entonces la dirección de la unión. Para obtener más información, consulte [crear o editar el cuadro de diálogo de relación &#40;Analysis Services - datos multidimensionales&#41;](../../2014/analysis-services/create-or-edit-relationship-dialog-box-analysis-services-multidimensional-data.md).  
  
7.  En el **especificar los datos de entrenamiento** página, elija las columnas para su uso en el modelo activando una casilla de verificación como se indica a continuación:  
  
    -   **IncomeGroup** seleccione la **entrada** casilla de verificación.  
  
         Esta columna contiene información interesante sobre los clientes que puede utilizar para la agrupación en clústeres. La utilizará en el primer modelo y, a continuación, la omitirá en el segundo.  
  
    -   **OrderNumber** seleccione la `Key` casilla de verificación.  
  
         Este campo se utilizará como identificador para la tabla de casos o `Key`. En general, nunca debería utilizar el campo clave de la tabla de casos como una entrada, porque la clave contiene valores únicos que no son útiles para la agrupación en clústeres.  
  
    -   **Región** seleccione la **entrada** casilla de verificación.  
  
         Esta columna contiene información interesante sobre los clientes que puede utilizar para la agrupación en clústeres. La utilizará en el primer modelo y, a continuación, la omitirá en el segundo.  
  
    -   **LineNumber** seleccione la `Key` y **entrada** casillas de verificación.  
  
         El **LineNumber** campo se utilizará como el identificador de la tabla anidada, o `Sequence Key`. La clave para una tabla anidada siempre se debe utilizar para la entrada.  
  
    -   **Modelo** seleccione la **entrada** y **Predictable** casillas de verificación.  
  
     Compruebe que las selecciones sean correctas y, a continuación, haga clic en **siguiente**.  
  
8.  En el **contenido y el tipo de datos de columnas Especifique** página, compruebe que la cuadrícula contiene las columnas, tipos de contenido y los tipos de datos se muestra en la tabla siguiente y, a continuación, haga clic en **siguiente**.  
  
    |Tablas y columnas|Tipo de contenido|Tipo de datos|  
    |---------------------|------------------|---------------|  
    |IncomeGroup|Discrete|Texto|  
    |OrderNumber|Key|Texto|  
    |Region|Discrete|Texto|  
    |vAssocSeqLineItems|||  
    |Line Number|Key Sequence|Long|  
    |Modelo|Discrete|Texto|  
  
9. En el **crear conjunto de pruebas** página, cambie la **porcentaje de datos de prueba** a 20 y, a continuación, haga clic en **siguiente**.  
  
10. En el **finalización del Asistente para** página, para la **nombre de la estructura de minería de datos**, tipo `Sequence Clustering with Region`.  
  
11. Para el **nombre del modelo de minería de datos**, tipo `Sequence Clustering with Region`.  
  
12. Compruebe el **permitir obtención de detalles** cuadro y, a continuación, haga clic en **finalizar**.  
  
## <a name="next-task-in-lesson"></a>Siguiente tarea de la lección  
 [Procesar el modelo de agrupación en clústeres de secuencia](../../2014/tutorials/processing-the-sequence-clustering-model.md)  
  
## <a name="see-also"></a>Vea también  
 [Diseñador de minería de datos](../../2014/analysis-services/data-mining/data-mining-designer.md)   
 [Algoritmo de clústeres de secuencia de Microsoft](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md)  
  
  