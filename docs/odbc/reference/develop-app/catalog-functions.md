---
title: "Las funciones de catálogo | Documentos de Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- catalog functions [ODBC], about catalog functions
- data dictionary [ODBC]
- catalog functions [ODBC]
- functions [ODBC], catalog functions
ms.assetid: 81ba9453-c085-47c0-b411-90ca6a5ee428
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 497676e6b87b6603d4bc6cb1615bb1b133c7acd4
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="catalog-functions"></a>Funciones de catálogo
Todas las bases de datos tienen una estructura que describe cómo se almacenarán los datos en la base de datos. Por ejemplo, una base de datos de pedidos de ventas simple podría tener la estructura que se muestra en la ilustración siguiente, en el que se utilizan las columnas de identificador para vincular las tablas.  
  
 ![Muestra la estructura de una base de datos simple](../../../odbc/reference/develop-app/media/pr19.gif "pr19")  
  
 Esta estructura, junto con otra información como los privilegios, se almacena en un conjunto de tablas del sistema llamado a la base de datos *catálogo,* también conocido como un *diccionario de datos*.  
  
 Una aplicación puede detectar esta estructura a través de llamadas a la *las funciones de catálogo*. Las funciones de catálogo devuelven información en conjuntos de resultados y se implementa normalmente a través de **seleccione** las instrucciones en las tablas en el catálogo. Por ejemplo, una aplicación puede solicitar un conjunto de resultados que contenga información sobre todas las tablas del sistema o todas las columnas de una tabla determinada.  
  
 Esta sección contiene los temas siguientes.  
  
-   [Usos de los datos del catálogo](../../../odbc/reference/develop-app/uses-of-catalog-data.md)  
  
-   [Funciones de catálogo de ODBC](../../../odbc/reference/develop-app/catalog-functions-in-odbc.md)

