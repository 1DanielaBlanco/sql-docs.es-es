---
title: "Operadores unarios en dimensiones de elementos primarios y secundarios | Microsoft Docs"
ms.custom: ""
ms.date: "03/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "UnaryOperatorColumn, propiedad"
  - "atributos [Analysis Services], operadores unarios"
  - "operadores unarios"
ms.assetid: b8ef549c-5458-458a-bf1a-fd743a1417fd
caps.latest.revision: 29
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Operadores unarios en dimensiones de elementos primarios y secundarios
  En una dimensión que contiene una relación de elementos primarios y secundarios en [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], se especifica una columna de operador unario (o de resumen personalizado) que determina el resumen personalizado para todos los miembros no calculados del atributo primario. El operador unario se aplica a los miembros siempre que los valores de los miembros primarios se evalúan. El elemento **UnaryOperatorColumn** en un atributo primario (**Uso** = Primario) especifica la columna de una tabla en la vista del origen de datos que contiene operadores unarios. Los valores para los operadores de resumen personalizado que se almacenan en esta columna se aplican a cada miembro del atributo.  
  
 Puede crear y especificar un cálculo con nombre en una tabla de dimensiones de la vista del origen de datos como una columna de operador unario. La expresión más simple, como '+', devuelve el mismo operador para todos los miembros. Pero se puede usar cualquier expresión siempre que devuelva un operador para cada miembro.  
  
 Puede cambiar el valor de la propiedad **UnaryOperatorColumn** de forma manual en un atributo primario o usar la mejora para definir agregaciones personalizadas del Asistente de Business Intelligence para reemplazar la agregación predeterminada asociada a los miembros de una dimensión. Para más información sobre el uso del Asistente de Business Intelligence para ejecutar esta configuración, vea [Agregar una agregación personalizada a una dimensión](../../analysis-services/multidimensional-models/add-a-custom-aggregation-to-a-dimension.md).  
  
 El valor predeterminado de la propiedad **UnaryOperatorColumn** en un atributo primario es (ninguno), que deshabilita los operadores de resumen personalizados. En la tabla siguiente se enumeran los operadores unarios disponibles y se describe su comportamiento cuando se aplican a un nivel.  
  
|Operador unario|Description|  
|--------------------|-----------------|  
|+ (signo más)|El valor del miembro se agrega al valor de agregado de los miembros iguales que ocurren antes del miembro. Éste es el operador predeterminado si no se define una columna de operador unario para un atributo.|  
|– (signo menos)|El valor del miembro se sustrae al valor de agregado de los miembros iguales que ocurren antes del miembro.|  
|* (asterisco)|El valor del miembro se multiplica por el valor de agregado de los miembros iguales que ocurren antes del miembro.|  
|/ (barra diagonal)|El valor del miembro se divide por el valor de agregado de los miembros iguales que ocurren antes del miembro.|  
|~ (tilde)|El valor del miembro se omite.|  
  
 Los valores en blanco y cualquier otro valor que no se encuentre en la tabla se tratan como el operador unario del signo más (+). Los operadores no tienen prioridad, de manera que el orden de los miembros tal como se almacenan en la columna de operadores unarios determina el orden de evaluación. Para cambiar el orden de evaluación, cree un nuevo atributo, establezca su propiedad **Type** en **Sequence**y asigne números de secuencia que correspondan al orden de evaluación en su propiedad **Source Column** . También debe ordenar miembros del atributo de acuerdo con este atributo. Para más información sobre la forma de usar el Asistente de Business Intelligence para ordenar miembros de un atributo, vea [Definir la ordenación en una dimensión](../../analysis-services/multidimensional-models/define-the-ordering-for-a-dimension.md).  
  
 Puede usar la propiedad **UnaryOperatorColumn** para especificar un cálculo con nombre que devuelve un operador unario como un carácter literal para todos los miembros del atributo. Esto puede ser algo tan sencillo como escribir un carácter literal como `'*'` en el cálculo con nombre. Esto reemplaza el operador predeterminado, el signo más (+), con el operador de multiplicación, el asterisco (*), para todos los miembros del atributo. Para más información, vea [Definir cálculos con nombre en una vista del origen de datos &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md).  
  
 En la pestaña **Explorador** del Diseñador de dimensiones, se pueden ver los operadores unarios junto a cada miembro en una jerarquía. También puede cambiar los operadores unarios al trabajar con una dimensión habilitada para escritura. Si la dimensión no está habilitada para escritura, debe usar una herramienta para modificar directamente el origen de datos.  
  
## Vea también  
 [Referencia de las propiedades de los atributos de dimensión](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)   
 [Operadores de resúmenes personalizados en dimensiones de elementos primarios y secundarios](../../analysis-services/multidimensional-models/custom-rollup-operators-in-parent-child-dimensions.md)   
 [Iniciar el Asistente de Business Intelligence en el Diseñador de dimensiones](../../analysis-services/multidimensional-models/start-the-business-intelligence-wizard-in-dimension-designer.md)  
  
  