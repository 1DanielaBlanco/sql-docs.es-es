---
title: "Transformaci&#243;n Mapa de caracteres | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.charactertrans.f1"
helpviewer_keywords: 
  - "mutuamente exclusiva, asignación [Integration Services]"
  - "asignar datos [Integration Services]"
  - "funciones de cadena"
  - "Mapa de caracteres, transformación [Integration Services]"
ms.assetid: e0f50eb6-b893-400f-bb8c-fb3072cc2620
caps.latest.revision: 42
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 42
---
# Transformaci&#243;n Mapa de caracteres
  La transformación Mapa de caracteres se aplica a funciones de cadena que operan sobre datos de caracteres, como la conversión de minúsculas a mayúsculas. Esta transformación solo opera en datos de columnas con un tipo de datos de cadena.  
  
 La transformación Mapa de caracteres puede convertir datos de columna in situ o agregar una columna a la salida de transformación y colocar los datos convertidos en la nueva columna. Puede aplicar distintos conjuntos de operaciones de asignación a la misma columna de entrada y colocar los resultados en columnas diferentes. Por ejemplo, puede convertir la misma columna a mayúsculas y minúsculas, y almacenar el resultado en dos columnas diferentes.  
  
 En algunas situaciones, la asignación puede provocar un truncamiento de datos. Por ejemplo, se puede producir un truncamiento cuando se asignan caracteres de un byte a caracteres representados con varios bytes. La transformación Mapa de caracteres incluye una salida de error que se puede usar para dirigir los datos truncados a otra salida distinta. Para más información, vea [Control de errores en los datos](../../../integration-services/data-flow/error-handling-in-data.md).  
  
 Esta transformación tiene una entrada, una salida y una salida de error.  
  
## Operaciones de asignación  
 En la siguiente tabla se describen las operaciones de asignación admitidas por la transformación Mapa de caracteres.  
  
|Operación|Description|  
|---------------|-----------------|  
|Inversión de byte|Invierte el orden de los bytes.|  
|Formato completo|Asigna caracteres de formato medio a caracteres de formato completo.|  
|Formato medio|Asigna caracteres de formato completo a caracteres de formato medio.|  
|Hiragana|Asigna caracteres katakana a caracteres hiragana.|  
|Katakana|Asigna caracteres hiragana a caracteres katakana.|  
|Utilización lingüística de mayúsculas y minúsculas|Aplica la utilización lingüística de mayúsculas y minúsculas en lugar de las reglas del sistema. La utilización lingüística de mayúsculas y minúsculas se refiere a la funcionalidad ofrecida por la API de Win32 para la asignación de caracteres Unicode simples del turco y otras configuraciones regionales.|  
|Minúsculas|Conversión de caracteres a minúsculas.|  
|Chino simplificado|Asigna caracteres de chino tradicional a caracteres de chino simplificado.|  
|Chino tradicional|Asigna caracteres de chino simplificado a caracteres de chino tradicional.|  
|Mayúsculas|Conversión de caracteres a mayúsculas.|  
  
## Operaciones de asignación mutuamente exclusivas  
 En una transformación pueden realizarse varias operaciones. Sin embargo, algunas operaciones son mutuamente exclusivas. La siguiente tabla enumera las restricciones que se aplican al usar varias operaciones sobre la misma columna. Las operaciones sobre las columnas Operación A y Operación B son mutuamente exclusivas.  
  
|Operación A|Operación B|  
|-----------------|-----------------|  
|Minúsculas|Mayúsculas|  
|Hiragana|Katakana|  
|Formato medio|Formato completo|  
|Chino tradicional|Chino simplificado|  
|Minúsculas|Hiragana, katakana, formato medio, formato completo|  
|Mayúsculas|Hiragana, katakana, formato medio, formato completo|  
  
## Configuración de la transformación Mapa de caracteres  
 Puede configurar la transformación Mapa de caracteres de las maneras siguientes:  
  
-   Especificar las columnas que desea convertir.  
  
-   Especificar las operaciones que desea aplicar a cada columna.  
  
 Puede establecer propiedades a través del Diseñador de [!INCLUDE[ssIS](../../../includes/ssis-md.md)] o mediante programación.  
  
 Para obtener más información acerca de las propiedades que puede establecer en el cuadro de diálogo **Editor de transformación Mapa de caracteres** , vea [Character Map Transformation Editor](../../../integration-services/data-flow/transformations/character-map-transformation-editor.md).  
  
 El cuadro de diálogo **Editor avanzado** indica las propiedades que se pueden establecer mediante programación. Para obtener más información acerca de las propiedades que puede establecer a través del cuadro de diálogo **Editor avanzado** o mediante programación, haga clic en uno de los temas siguientes:  
  
-   [Propiedades comunes](../Topic/Common%20Properties.md)  
  
-   [Propiedades personalizadas de transformación](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
 Para obtener más información sobre cómo establecer valores de propiedades, haga clic en uno de los temas siguientes:  
  
-   [Establecer las propiedades de un componente de flujo de datos](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
-   [Ordenar datos para las transformaciones Mezclar y Combinación de mezcla](../../../integration-services/data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)  
  
  