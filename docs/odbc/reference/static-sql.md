---
title: "SQL estático | Documentos de Microsoft"
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
- static SQL [ODBC]
- SQL [ODBC], embedded SQL
- SQL statements [ODBC], embedded SQL
- SQL statements [ODBC], static SQL
- embedded SQL [ODBC]
- SQL [ODBC], static SQL
ms.assetid: 667d92ec-fed9-4028-81d4-bb9ba867356a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1675f70b67f5c600aada546f8caf8eb8b99df99a
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="static-sql"></a>SQL estático
El SQL incrustado se muestra en [ejemplo SQL incrustado](../../odbc/reference/embedded-sql-example.md) se conoce como SQL estático. Se denomina SQL estático porque las instrucciones SQL en el programa son estáticas; es decir, no cambie cada vez que se ejecuta el programa. Como se describe en la sección anterior, estas instrucciones se compilan cuando se compila el resto del programa.  
  
 SQL estático funciona bien en muchas situaciones y puede utilizarse en cualquier aplicación para el que se puede determinar el acceso a datos en tiempo de diseño de programa. Por ejemplo, un programa de entrada de pedidos siempre utiliza la misma instrucción para insertar un nuevo pedido y un sistema de reserva airline siempre utiliza la misma instrucción para cambiar el estado de un puesto de disponible a reservado. Cada una de estas instrucciones se generalizarse mediante el uso de variables de host; se pueden insertar valores diferentes en un pedido de venta y se pueden reservar puestos diferentes. Dado que estas instrucciones pueden ser codificados de forma rígida en el programa, dichos programas tienen la ventaja de que las instrucciones deben analizar, validar y con optimización para una sola vez, en tiempo de compilación. Esto da como resultado un código relativamente rápido.

