---
title: Las instrucciones de DDL | Documentos de Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], DDL statements
- DDL statements [ODBC]
ms.assetid: 96ac9859-5976-4b06-ae1f-2fec3231e266
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 12ad45516f14b33dcd9ae506bbf4e86c71c9a8cd
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2017
---
# <a name="ddl-statements"></a>Instrucciones DDL
Las instrucciones de lenguaje de definición (DDL) de datos varían enormemente entre DBMS. SQL de ODBC define las instrucciones para las operaciones más habituales de definición de datos: crear y quitar tablas, índices y vistas; modificar tablas; conceder y revocar privilegios. Todas las demás instrucciones de DDL son específicos del origen de datos. Por lo tanto, las aplicaciones interoperables no pueden realizar algunas operaciones de definición de datos. En general, esto no supone un problema, porque estas operaciones tienden a ser muy específica de los DBMS y son más adecuadas izquierda para el software de administración de base de datos propietaria incluidos con la mayoría de los DBMS o el programa de instalación que se incluye con el controlador.  
  
 Otro problema de definición de datos es ese tipo de datos nombres varían enormemente entre DBMS. En lugar de definir nombres de tipo de datos estándar y forzar controladores para convertirlos en nombres específicos de DBMS, **SQLGetTypeInfo** proporciona una manera para que las aplicaciones detectar los nombres de tipo de datos específicos del DBMS. Aplicaciones interoperables deben usar estos nombres de instrucciones SQL para crear y modificar las tablas; los nombres que aparecen en [Apéndice C: SQL gramática](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md), y [tipos de datos de apéndice D:](../../../odbc/reference/appendixes/appendix-d-data-types.md), son sólo ejemplos.
