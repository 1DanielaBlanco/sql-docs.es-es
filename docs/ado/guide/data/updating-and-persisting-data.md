---
title: Actualizar y almacenar datos | Documentos de Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- updating data [ADO]
- data updates [ADO]
- ADO, updating data
ms.assetid: 8dc27274-4f96-43d1-913c-4ff7d01b9a27
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1fd0fc64e1727b5e4ba9d2830218f3ddb6e004be
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="updating-and-persisting-data"></a>Actualizar y conservar datos
Los capítulos anteriores han explicado cómo utilizar ADO para obtener datos de un origen de datos, cómo desplazarse por los datos e incluso cómo editar los datos. Por supuesto, si el objetivo de la aplicación es permitir a los usuarios realizar cambios en los datos, debe entender cómo guardar los cambios. O bien puede conservar la **conjunto de registros** cambia a un archivo mediante la **guardar** método, también puede enviar los cambios de vuelta al origen de datos de almacenamiento con el **actualización** o  **UpdateBatch** métodos.  
  
 En los capítulos anteriores, se ha cambiado los datos en varias filas de la **conjunto de registros**. ADO admite dos nociones básicas relacionadas con la adición, eliminación y modificación de filas de datos.  
  
 La primera noción es que no se realizan inmediatamente los cambios en el **Recordset**; en su lugar, se realizan una interno *búfer de copia*. Si decide que no desea que los cambios, se descartan las modificaciones en el búfer de copia. Si decide conservar los cambios, se aplican los cambios en el búfer de copia para la **conjunto de registros**.  
  
 La segunda noción es que los cambios o bien se propagan al origen de datos en cuanto se declara el trabajo en una fila completa (es decir, *inmediata* modo), o todos los cambios en un conjunto de filas se recopilan hasta que se declara el trabajo para el conjunto completo (es decir, *lote* modo). El **LockType** propiedad determina cuándo se realizan los cambios al origen de datos subyacente. **adLockOptimistic** o **adLockPessimistic** especifican el modo inmediato, mientras que **adLockBatchOptimistic** especifica el modo por lotes. El **CursorLocation** propiedad puede afectar a la que **LockType** opciones están disponibles. Por ejemplo, el **adLockPessimistic** configuración no se admite si el **CursorLocation** propiedad está establecida en **adUseClient**.  
  
 En el modo inmediato, cada invocación de la **actualización** método propaga los cambios al origen de datos. En modo por lotes, cada invocación de **actualización** o movimiento de la posición actual de fila guarda los cambios en el búfer de copia, pero sólo el **UpdateBatch** método propaga los cambios al origen de datos.  
  
 Esta sección contiene los temas siguientes.  
  
-   [Actualización de datos](../../../ado/guide/data/updating-data.md)  
  
-   [Conservar los datos](../../../ado/guide/data/persisting-data.md)
