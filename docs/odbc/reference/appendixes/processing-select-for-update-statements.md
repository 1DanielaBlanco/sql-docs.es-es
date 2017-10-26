---
title: Procesamiento SELECT para las instrucciones UPDATE | Documentos de Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC cursor library [ODBC], statement processing
- SQL statements [ODBC], select for update statements
- select for update [ODBC]
- SQL statements [ODBC], cursor library
- cursor library [ODBC], select for update statements
- ODBC cursor library [ODBC], select for update statements
- cursor library [ODBC], statement processing
ms.assetid: 8d2e79a4-5daf-458e-a536-d8b6e588753e
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ada17f95371246e3b43e1e9482ab9595f85a8db1
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="processing-select-for-update-statements"></a>Seleccione para instrucciones UPDATE de procesamiento
> [!IMPORTANT]  
>  Esta característica se quitará en una versión futura de Windows. Evite utilizar esta característica en nuevos trabajos de desarrollo y piense en modificar las aplicaciones que actualmente utilizan esta característica. Microsoft recomienda usar la funcionalidad del controlador cursor.  
  
 Para obtener una interoperabilidad máxima, las aplicaciones deben generar conjuntos de resultados que se actualiza con una instrucción update posicionadas mediante la ejecución de un **seleccione para actualizar** instrucción. Aunque la biblioteca de cursores no requiere esto, es necesario por la mayoría de los orígenes de datos que admiten las instrucciones update posicionadas.  
  
 La biblioteca de cursores pasa por alto las columnas de la **FOR UPDATE** cláusula de una **SELECT FOR UPDATE** instrucción; esta cláusula quita antes de pasar la instrucción del controlador. En la biblioteca de cursores, el atributo de instrucción SQL_ATTR_CONCURRENCY, junto con las restricciones mencionadas en la sección anterior, controles si las columnas en un resultado de conjunto se pueden actualizar.

