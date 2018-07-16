---
title: Agregar el Editor de transformación (pestaña Avanzadas) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.aggregationtransformation.advanced.f1
helpviewer_keywords:
- Aggregate Transformation Editor
ms.assetid: 186a9736-2554-40a0-9cb2-877a8db5fde8
caps.latest.revision: 26
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 398ec0597f0240548d6aba15ac2f29b218f4089a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37254577"
---
# <a name="aggregate-transformation-editor-advanced-tab"></a>Editor de transformación Agregado (pestaña Avanzadas)
  Utilice la pestaña **Avanzadas** del cuadro de diálogo **Editor de transformación Agregado** para establecer las propiedades del componente, especificar agregaciones y establecer las propiedades de las columnas de entrada y salida.  
  
> [!NOTE]  
>  Las opciones para el recuento de claves, la escala de claves, la clave Count Distinct y la escala de claves distintas estarán disponibles en el componente si se especifican en la pestaña **Avanzadas** , en la salida si se especifican en la pantalla avanzada de la pestaña **Agregaciones** y en la columna si se especifican en la lista de columnas en la parte inferior de la pestaña **Agregaciones** .  
>   
>  En la transformación Agregado, **Claves** y **Escala de claves** hacen referencia al número de grupos que se esperan como resultado de una operación **Agrupar por** . **Claves Count Distinct** y **Escala Count Distinct** hacen referencia al número de valores distintos que se esperan como resultado de una operación **Recuento distinto** .  
  
 Para obtener más información acerca de la transformación Agregado, vea [Aggregate Transformation](data-flow/transformations/aggregate-transformation.md).  
  
## <a name="options"></a>Opciones  
 **Escala de claves**  
 Si lo desea, especifique el número aproximado de claves que espera la agregación. La transformación utiliza esta información para optimizar el tamaño de caché inicial. De forma predeterminada, el valor de esta opción es **No especificado**. Si se especifica tanto **Escala de claves** como **Número de claves** , prevalece la opción **Número de claves** .  
  
|Valor|Descripción|  
|-----------|-----------------|  
|No especificado|No se utiliza la propiedad **Escala de claves** .|  
|Baja|La agregación podrá escribir aproximadamente 500 000 claves.|  
|Media|La agregación podrá escribir aproximadamente 5.000.000 claves.|  
|Alta|La agregación podrá escribir más de 25.000.000 claves.|  
  
 **Número de claves**  
 Si lo desea, especifique el número exacto de claves que espera la agregación. La transformación utiliza esta información para optimizar el tamaño de caché inicial. Si se especifica tanto **Escala de claves** como **Número de claves** , prevalece la opción **Número de claves** .  
  
 **Escala Count Distinct**  
 Opcionalmente, puede especificar el número aproximado de valores DISTINCT que podrá escribir la agregación. De forma predeterminada, el valor de esta opción es **No especificado**. Si se especifica tanto **Escala Count Distinct** como **Claves Count Distinct** , prevalece la opción **Claves Count Distinct** .  
  
|Valor|Descripción|  
|-----------|-----------------|  
|No especificado|No se utiliza la propiedad CountDistinctScale.|  
|Baja|La agregación podrá escribir aproximadamente 500.000 valores DISTINCT.|  
|Media|La agregación podrá escribir aproximadamente 5 000 000 valores DISTINCT.|  
|Alta|La agregación podrá escribir más de 25.000.000 valores DISTINCT.|  
  
 **Claves Count Distinct**  
 Opcionalmente, puede especificar el número exacto de valores DISTINCT que podrá escribir la agregación. Si se especifica tanto **Escala Count Distinct** como **Claves Count Distinct** , prevalece la opción **Claves Count Distinct** .  
  
 **Factor de ampliación automática**  
 Utilice un valor comprendido entre 1 y 100 para especificar el porcentaje en el que se puede ampliar la memoria durante la agregación. De forma predeterminada, el valor de esta opción es **25%**.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de mensajes y Error de Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor de transformación de agregado &#40;pestaña agregaciones&#41;](../../2014/integration-services/aggregate-transformation-editor-aggregations-tab.md)   
 [Incorporación de valores en un conjunto de datos con la transformación Agregado](data-flow/transformations/aggregate-values-in-a-dataset-by-using-the-aggregate-transformation.md)  
  
  
