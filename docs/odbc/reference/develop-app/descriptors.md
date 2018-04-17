---
title: Descriptores | Documentos de Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- descriptors [ODBC]
- descriptors [ODBC], about descriptors
- descriptor handles [ODBC]
- handles [ODBC], descriptor
ms.assetid: ef2cbb93-cd00-40f8-b1d2-5f5723a991aa
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8362a8dd210579ebca0d303ca29661a3774ea4cd
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="descriptors"></a>Descriptores de
Un identificador de descriptor hace referencia a una estructura de datos que contiene información sobre las columnas o parámetros dinámicos.  
  
 Funciones ODBC que operan sobre datos de parámetro y columna implícitamente establecerán y recuperar los campos de descriptor. Por ejemplo, cuando **SQLBindCol** se llama para enlazar datos de la columna, Establece los campos de descriptor que describen completamente el enlace. Cuando **SQLColAttribute** se llama para describir los datos de la columna, devuelve los datos almacenados en campos de descriptor.  
  
 Una aplicación que llama a funciones ODBC no necesita preocuparse por descriptores. No hay ninguna operación de base de datos requiere que la aplicación tenga acceso directo a descriptores. Sin embargo, en algunas aplicaciones, acceder directamente a descriptores simplifica muchas operaciones. Por ejemplo, dirigir el acceso a los descriptores de proporciona una manera de cambiar el enlace de datos de columna, que pueden ser más eficaces que llamar a **SQLBindCol** nuevo.  
  
> [!NOTE]  
>  No se define la representación física del descriptor. Las aplicaciones tenga acceso directo a un descriptor solo mediante la manipulación de sus campos mediante una llamada a funciones ODBC con el identificador de descriptor.  
  
 Esta sección contiene los temas siguientes.  
  
-   [Tipos de descriptores de](../../../odbc/reference/develop-app/types-of-descriptors.md)  
  
-   [Campos de descriptor](../../../odbc/reference/develop-app/descriptor-fields.md)  
  
-   [Asignar y liberar los descriptores](../../../odbc/reference/develop-app/allocating-and-freeing-descriptors.md)  
  
-   [Obtener y establecer los campos de Descriptor](../../../odbc/reference/develop-app/getting-and-setting-descriptor-fields.md)
