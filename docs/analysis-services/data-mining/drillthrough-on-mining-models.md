---
title: "Obtenci&#243;n de detalles en modelos de miner&#237;a de datos | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f179a467-7d03-4d61-8e9a-6b5afb5fc2d5
caps.latest.revision: 8
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 8
---
# Obtenci&#243;n de detalles en modelos de miner&#237;a de datos
  La*obtención de detalles* se refiere a la capacidad de consultar un modelo o una estructura de minería de datos y obtener datos detallados que no se exponen en el modelo.  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] proporciona dos opciones diferentes para obtener detalles sobre los datos de los casos. Puede obtener detalles tanto de los casos usados para generar los datos como de los casos de la estructura de minería de datos.  
  
## Obtención de detalles de los casos del modelo frente a obtención de detalles de la estructura  
 La obtención de detalles de los **casos del modelo** resulta útil para buscar detalles adicionales sobre las reglas, los patrones o los clústeres de un modelo. Por ejemplo, no usaría información de contacto de cliente para el análisis en un modelo de clústeres, incluso si los datos estuvieran disponibles, mediante la obtención de detalles podría obtener acceso a la información del modelo.  
  
 En cambio, la **obtención de detalles de los datos de la estructura** pretende proporcionar acceso a la información que no está disponible en el modelo. Por ejemplo, algunas columnas de la estructura se han excluido de un modelo porque el tipo de datos era compatible o los datos no eran útiles para el análisis.  
  
## Habilitar la obtención de detalles en un modelo  
 Para utilizar la obtención de detalles en un modelo de minería de datos, se deben cumplir las condiciones siguientes:  
  
-   Es posible configurar la obtención de detalles solo en los casos de modelos y no en la estructura de minería de datos, pero no al contrario.  Es decir, la obtención de detalles debe estar habilitada en el modelo de minería de datos para permitir la obtención de detalles en la estructura de minería de datos.  
  
-   La obtención de detalles en el modelo y la estructura está deshabilitada de forma predeterminada. Si usa el Asistente para minería de datos, la opción para habilitar la obtención de detalles en los casos del modelo está en la página final del asistente.  
  
-   Puede agregar la capacidad de obtener detalles a un modelo de minería de datos existente pero, si lo hace, hay que volver a procesar el modelo para poder obtener detalles de los datos.  
  
-   La obtención de detalles no funcionará a menos que se haya mantenido la memoria caché creada durante el proceso de entrenamiento. Para más información sobre las propiedades que controlan el almacenamiento en caché, vea [Obtención de detalles en estructuras de minería de datos](../../analysis-services/data-mining/drillthrough-on-mining-structures.md).  
  
## Modelos compatibles con la obtención de detalles  
 Si se ha configurado un modelo de minería de datos para permitir la obtención de detalles y tiene los permisos adecuados, al examinar el modelo puede hacer clic en un nodo en el visor adecuado y recuperar la información detallada sobre los casos de ese nodo concreto.  
  
 No todos los modelos son compatibles con la obtención de detalles; depende del algoritmo utilizado para crear el modelo. En la tabla siguiente se enumeran los tipos de modelos que no son compatibles con la obtención de detalles o que lo son con limitaciones. Si el tipo de modelo no aparece, es compatible con la obtención de detalles.  
  
|**Nombre del algoritmo**|**Es compatible con la obtención de detalles**|  
|------------------------|----------------------------------|  
|Algoritmo Bayes Naïve de Microsoft|No compatible.<br /><br /> Estos algoritmos no asignan casos a nodos específicos del contenido.|  
|Algoritmo de red neuronal de Microsoft|No compatible.<br /><br /> Estos algoritmos no asignan casos a nodos específicos del contenido.|  
|Algoritmo de regresión logística de Microsoft|No compatible.<br /><br /> Estos algoritmos no asignan casos a nodos específicos del contenido.|  
|Algoritmo de regresión lineal de Microsoft|Compatible.<br /><br /> Sin embargo, dado que el modelo crea un único nodo, **All**, la obtención de detalles devuelve todos los casos de entrenamiento para el modelo. Si el conjunto de entrenamiento es grande, la carga de resultados puede tardar mucho tiempo.|  
|Algoritmo de serie temporal de Microsoft|Compatible.<br /><br /> Sin embargo, no puede obtener información de estructuras o casos mediante el **Visor de modelos de minería de datos** en el Diseñador de minería de datos. En su lugar, debe crear una consulta de DMX.<br /><br /> Tampoco puede obtener detalles de nodos específicos, ni escribir una consulta DMX para recuperar casos en nodos específicos de un modelo de serie temporal. Puede recuperar datos de casos del modelo o la estructura usando otros criterios, como valores de fecha o de atributo.<br /><br /> Si quiere ver detalles de los nodos ARTXP y ARIMA creados por el algoritmo de serie temporal de Microsoft, podría ser más fácil usar [Visor de árbol de contenido genérico de Microsoft &#40;Minería de datos&#41;](../Topic/Microsoft%20Generic%20Content%20Tree%20Viewer%20\(Data%20Mining\).md).|  
  
## Tareas relacionadas  
 Vea los temas siguientes para obtener más información sobre el uso de la obtención de detalles con los modelos de minería de datos.  
  
|Tareas|Vínculos|  
|-----------|-----------|  
|Usar la obtención de detalles en los visores de modelos de minería de datos|[Usar la obtención de detalles desde los visores de modelos](../../analysis-services/data-mining/use-drillthrough-from-the-model-viewers.md)|  
|Recuperar los datos de casos para un modelo mediante la obtención de detalles|[Obtener detalles de datos de caso a partir de un modelo de minería de datos](../../analysis-services/data-mining/drill-through-to-case-data-from-a-mining-model.md)|  
|Habilitar la obtención de detalles en un modelo de minería de datos existente|[Habilitar la obtención de detalles para un modelo de minería](../../analysis-services/data-mining/enable-drillthrough-for-a-mining-model.md)|  
|Ver ejemplos de consultas de obtención de detalles para tipos de modelos concretos.|[Consultas de minería de datos](../../analysis-services/data-mining/data-mining-queries.md)|  
|Habilitar la obtención de detalles en el Asistente para modelo de minería de datos|[Finalización del asistente &#40;Asistente para minería de datos&#41;](../Topic/Completing%20the%20Wizard%20\(Data%20Mining%20Wizard\).md).|  
  
## Vea también  
 [Obtención de detalles en estructuras de minería de datos](../../analysis-services/data-mining/drillthrough-on-mining-structures.md)  
  
  