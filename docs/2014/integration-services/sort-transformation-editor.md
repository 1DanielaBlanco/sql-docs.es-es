---
title: Editor de transformación Ordenar | Microsoft Docs
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
- sql12.dts.designer.sorttransformation.f1
helpviewer_keywords:
- Sort Transformation Editor
ms.assetid: 8ae23970-49a9-4d6d-9f15-c7074783347c
caps.latest.revision: 24
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 818625c2d43080560fee3fc87879f96acad20c0e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37240947"
---
# <a name="sort-transformation-editor"></a>Editor de transformación Ordenar
  Use el cuadro de diálogo **Editor de transformación Ordenar** para seleccionar las columnas que desea ordenar, establecer el orden y especificar si deben quitarse los duplicados.  
  
 Para obtener más información acerca de la transformación Ordenar, vea [Sort Transformation](data-flow/transformations/sort-transformation.md).  
  
## <a name="options"></a>Opciones  
 **Columnas de entrada disponibles**  
 Active las casillas de las columnas que desea ordenar.  
  
 **Nombre**  
 Muestra el nombre de todas las columnas de entrada disponibles.  
  
 **Paso a través**  
 Permite indicar si la columna debe incluirse en la salida ordenada.  
  
 **Columna de entrada**  
 Seleccione de la lista de entradas disponibles las columnas para cada fila. Las selecciones se reflejan en las casillas activadas en la tabla **Columnas de entrada disponibles** .  
  
 **Alias de salida**  
 Escriba un alias para cada columna de salida. El nombre predeterminado es el de la columna de entrada, pero puede elegir cualquier nombre descriptivo único.  
  
 **Tipo de orden**  
 Permite indicar si la ordenación seguirá un orden ascendente o descendente.  
  
 **Criterio de ordenación**  
 Permite indicar el orden en que deben ordenarse las columnas. Esta característica debe establecerse manualmente para cada columna.  
  
 **Marcas de comparación**  
 Para obtener más información sobre las opciones de comparación de cadenas, vea [Comparar datos de cadena](data-flow/comparing-string-data.md).  
  
 **Quitar filas con valores de ordenación duplicados**  
 Permite indicar si la transformación copia filas duplicadas en la salida o crea una única entrada para todos los duplicados utilizando las opciones de comparación de cadenas especificadas.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de errores y mensajes de Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
