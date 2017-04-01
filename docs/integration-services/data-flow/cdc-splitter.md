---
title: "Divisor CDC | Microsoft Docs"
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
  - "sql13.ssis.designer.cdcsplitter.f1"
ms.assetid: 167bc5c6-fa36-439d-987c-b20acd1a77e2
caps.latest.revision: 8
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# Divisor CDC
  El divisor CDC divide un único flujo de filas de un flujo de datos de origen de CDC en varios flujos de datos para las operaciones de inserción, actualización y eliminación. El flujo de datos se divide según la columna obligatoria `__$operation` y sus valores estándar en las tablas de cambios de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
|Valor de la operación|Salida|Description|  
|------------------------|------------|-----------------|  
|1|Delete|Fila eliminada|  
|2|Insert|Fila insertada (no está disponible cuando se usa el modo CDC **Neto con combinación**)|  
|3|Update|Fila antes de la actualización (disponible solo cuando se usa el modo CDC **Todo con los valores antiguos**)|  
|4|Update|Fila después de la actualización (sigue a la de antes de la actualización)|  
|5|Update|Fila de mezcla (solo disponible cuando se usa el modo CDC **Neto con combinación**)|  
|Otro|Error||  
  
 Puede usar el divisor para conectarse a los resultados predefinidos de INSERT, UPDATE, DELETE y UPDATE para un procesamiento posterior.  
  
 La transformación divisor CDC tiene una entrada normal y una salida de error.  
  
## Tratamiento de errores  
 La transformación divisor CDC tiene una salida de error. Las filas de entrada con un valor no válido de la columna $operation se consideran erróneas y se administran según la propiedad **ErrorRowDisposition** de la entrada.  
  
 La salida de error del componente incluye las columnas de salida siguientes:  
  
-   **Código de error**: se establece en 1.  
  
-   **Columna de error**: columna de origen que produce el error (para los errores de conversión).  
  
-   **Columnas de fila de error**: las columnas de entrada de la fila que produjo el error.  
  
## Configuración del divisor CDC  
 No hay propiedades configurables del divisor CDC.  
  
 Para obtener más información sobre cómo usar el divisor CDC, vea Componentes CDC para Microsoft SQL Server Integration Services.  
  
 El cuadro de diálogo **Editor avanzado** contiene las propiedades que se pueden establecer mediante programación.  
  
 Para abrir el cuadro de diálogo **Editor avanzado** :  
  
-   En la pantalla **Flujo de datos** del proyecto de [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] , haga clic con el botón secundario en el divisor CDC y seleccione **Mostrar editor avanzado**.  
  
## Vea también  
 [Dirigir el flujo CDC según el tipo de cambio](../../integration-services/data-flow/direct-the-cdc-stream-according-to-the-type-of-change.md)  
  
  