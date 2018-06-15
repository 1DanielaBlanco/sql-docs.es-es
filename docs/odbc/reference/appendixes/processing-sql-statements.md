---
title: Procesamiento de instrucciones SQL | Documentos de Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], statement processing
- SQL statements [ODBC], cursor library
- cursor library [ODBC], statement processing
ms.assetid: 54dad6a3-e86c-477b-ba7c-4e95e0385ec1
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 603cb680e2986d484074a43d14f56de210da0b4a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32909540"
---
# <a name="processing-sql-statements"></a>Procesamiento de instrucciones SQL
> [!IMPORTANT]  
>  Esta característica se quitará en una versión futura de Windows. Evite utilizar esta característica en nuevos trabajos de desarrollo y piense en modificar las aplicaciones que actualmente utilizan esta característica. Microsoft recomienda usar la funcionalidad del controlador cursor.  
  
 La biblioteca de cursores ODBC pasa todas las instrucciones SQL directamente en el controlador de excepción de los siguientes:  
  
-   Actualización por posición y eliminar instrucciones  
  
-   **SELECT FOR UPDATE** instrucciones  
  
-   Instrucciones SQL por lotes  
  
 Para ejecutar la actualización posicionada y eliminar las instrucciones y para colocar el cursor en una fila para llamar a **SQLGetData** crea una instrucción de búsqueda que identifica la fila para esa fila, la biblioteca de cursores.  
  
 Esta sección contiene los temas siguientes.  
  
-   [Procesamiento de instrucciones posicionadas Update y Delete](../../../odbc/reference/appendixes/processing-positioned-update-and-delete-statements.md)  
  
-   [Procesamiento de instrucciones SELECT FOR UPDATE](../../../odbc/reference/appendixes/processing-select-for-update-statements.md)  
  
-   [Procesamiento de lotes de instrucciones SQL](../../../odbc/reference/appendixes/processing-batches-of-sql-statements.md)  
  
-   [Construcción de instrucciones Searched](../../../odbc/reference/appendixes/constructing-searched-statements.md)
