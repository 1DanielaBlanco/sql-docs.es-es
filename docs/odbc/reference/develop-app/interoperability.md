---
title: Interoperabilidad | Documentos de Microsoft
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
- interoperability [ODBC]
- interoperability [ODBC], about interoperability
ms.assetid: 43b7c849-9d59-4002-9977-9e2c8730b859
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a96949b4ca739e382a547769f496576bf13db8b7
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="interoperability"></a>Interoperabilidad
*Interoperabilidad* es la capacidad de una sola aplicación para que funcione con muchos DBMS diferentes. La necesidad de escribir aplicaciones e interoperables, genéricas fue uno de los principales factores que conducen al desarrollo de ODBC. Sin embargo, interoperabilidad no es una ruta de acceso simple seguido de "no es interoperable" a "completamente interoperable". La ruta de acceso tiene muchas bifurcaciones y cada una requiere equilibrar el tiempo de desarrollo, velocidad, la complejidad del código y características.  
  
 El proceso de escribir una aplicación interoperable sigue varios pasos:  
  
1.  Decidir si la aplicación utiliza ODBC.  
  
2.  Elegir un nivel de interoperabilidad y decidir qué ventajas e inconvenientes son necesarios para alcanzar ese nivel.  
  
3.  Escribir código interoperable y probarlo más completa posible.  
  
 Debe tenerse en cuenta que la interoperabilidad es principalmente el dominio de la escritura de la aplicación. Controladores están diseñados para trabajar con un DBMS único y, por definición, no son interoperables. Desempeñan un papel de interoperabilidad implementando correctamente y exposición ODBC a través de un DBMS único.  
  
 Esta sección contiene los temas siguientes.  
  
-   [¿Es la respuesta ODBC?](../../../odbc/reference/develop-app/is-odbc-the-answer.md)  
  
-   [Elección de un nivel de interoperabilidad](../../../odbc/reference/develop-app/choosing-a-level-of-interoperability.md)  
  
-   [Determinar el DBMS de destino y los controladores](../../../odbc/reference/develop-app/determining-the-target-dbmss-and-drivers.md)  
  
-   [Teniendo en cuenta las características de base de datos que se utilizan](../../../odbc/reference/develop-app/considering-database-features-to-use.md)  
  
-   [Longitud del ciclo del producto](../../../odbc/reference/develop-app/length-of-the-product-cycle.md)  
  
-   [Escribir una aplicación Interoperable](../../../odbc/reference/develop-app/writing-an-interoperable-application.md)  
  
-   [Probar aplicaciones interoperables](../../../odbc/reference/develop-app/testing-interoperable-applications.md)
