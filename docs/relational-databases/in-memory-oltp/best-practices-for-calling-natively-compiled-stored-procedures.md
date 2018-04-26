---
title: Procedimientos recomendados para llamar a procedimientos almacenados compilados de forma nativa | Microsoft Docs
ms.custom: ''
ms.date: 03/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: in-memory-oltp
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f39fc1c7-cfec-4a95-97f6-6b95954694bb
caps.latest.revision: 8
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 4fbb6f7d3b467d2cba5af8eab6e00025508977f2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="best-practices-for-calling-natively-compiled-stored-procedures"></a>Prácticas recomendadas para llamar a un procedimiento almacenado compilado de forma nativa
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Los procedimientos almacenados compilados de forma nativa:  
  
-   Se suelen usar en componentes esenciales para el rendimiento de una aplicación.  
  
-   Se ejecutan con frecuencia.  
  
-   Se espera que sean muy rápidos.  
  
 La ventaja de rendimiento que supone emplear un procedimiento almacenado compilado de forma nativa aumenta con el número de filas y la cantidad de lógica que procesa el procedimiento. Por ejemplo, un procedimiento almacenado compilado de forma nativa tendrá mejor rendimiento si usa uno o varios de los elementos siguientes:  
  
-   Agregación.  
  
-   Combinaciones de bucles anidados.  
  
-   Operaciones de inserción, actualización y eliminación de varias instrucciones.  
  
-   Expresiones complejas.  
  
-   Lógica de procedimientos, como instrucciones condicionales y bucles.  
  
 Si solo necesita procesar una única fila, el uso de un procedimiento almacenado compilado de forma nativa quizás no proporcione ventajas de rendimiento.  
  
 Para evitar que el servidor tenga que asignar nombres de parámetro y convertir tipos:  
  
-   Haga corresponder los tipos de parámetros pasados al procedimiento con los tipos de la definición del procedimiento.  
  
-   Use parámetros ordinales (anónimos) cuando llame a procedimientos almacenados compilados de forma nativa. Para que la ejecución sea más eficaz, no utilice parámetros con nombre.  
  
 Se pueden detectar deficiencias en parámetros con procedimientos almacenados compilados de forma nativa mediante XEvent **natively_compiled_proc_slow_parameter_passing**:
 - Tipos no coincidentes: **reason=parameter_conversion**
 - Parámetros con nombre: **reason=named_parameters**
 - Valores predeterminados: **reason=default** 
  
## <a name="see-also"></a>Ver también  
 [Procedimientos almacenados compilados de forma nativa](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)  
