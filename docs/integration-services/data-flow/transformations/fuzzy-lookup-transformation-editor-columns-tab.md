---
title: "Editor de transformación Búsqueda aproximada (pestaña columnas) | Documentos de Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.fuzzylookuptransformation.columns.f1
helpviewer_keywords:
- Fuzzy Lookup Transformation Editor
ms.assetid: aaf45327-79e9-4760-9b4d-546ace91b5b4
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 487c138e91e1e0d3097432cf1c856fe2cdbcd609
ms.contentlocale: es-es
ms.lasthandoff: 08/03/2017

---
# <a name="fuzzy-lookup-transformation-editor-columns-tab"></a>Editor de transformación Búsqueda aproximada (pestaña Columnas)
  Use la pestaña **Columnas** del cuadro de diálogo **Editor de transformación Búsqueda aproximada** para especificar las propiedades de las columnas de entrada y salida.  
  
 Para obtener más información acerca de la transformación Búsqueda aproximada, vea [Fuzzy Lookup Transformation](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation.md).  
  
## <a name="options"></a>Opciones  
 **Columnas de entrada disponibles**  
 Arrastre las columnas de entrada para conectarlas a las columnas de búsqueda disponibles. Las columnas deben poseer tipos de datos coincidentes y compatibles. Seleccione una línea de asignación y haga clic con el botón derecho para editar las asignaciones en el cuadro de diálogo [Crear relaciones](../../../integration-services/data-flow/transformations/create-relationships.md) .  
  
 **Nombre**  
 Muestra los nombres de las columnas de entrada disponibles.  
  
 **Paso a través**  
 Especifique si desea incluir las columnas de entrada en la salida de transformación.  
  
 **Columnas de búsqueda disponibles**  
 Use las casillas para seleccionar las columnas en las que se realizarán operaciones de búsqueda aproximada.  
  
 **columna de búsqueda**  
 Seleccione las columnas de búsqueda en la lista de columnas de tabla de referencia disponibles. Sus selecciones se reflejan en las casillas en la tabla **Columnas de búsqueda disponibles** . Seleccione una columna en la tabla **Columnas de búsqueda disponibles** para crear una columna de salida que contenga el valor de la columna de la tabla de referencia para cada fila coincidente devuelta.  
  
 **Alias de salida**  
 Escriba un alias para la salida de cada columna de búsqueda. El nombre predeterminado es el de la columna de búsqueda con un valor de índice numérico anexado, pero puede elegir cualquier nombre descriptivo único.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de mensajes y Error de Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor de transformación Búsqueda aproximada &#40; Pestaña tabla de referencia &#41;](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation-editor-reference-table-tab.md)   
 [Editor de transformación Búsqueda aproximada &#40; Ficha Opciones avanzadas &#41;](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation-editor-advanced-tab.md)  
  
  
