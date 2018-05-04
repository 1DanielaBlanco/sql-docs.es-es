---
title: Interoperabilidad de instrucciones SQL | Documentos de Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC]
- interoperability of SQL statements [ODBC], about interoperability
ms.assetid: 3b24c499-829c-4e65-90cf-a3a0f6d0a186
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bb9f4ec6fbc2e6aecff8d78ff562f35f9a546405
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="interoperability-of-sql-statements"></a>Interoperabilidad de instrucciones SQL
Al igual que el resto de una aplicación, las instrucciones SQL pueden ser interoperable o específicos del DBMS. Y como el resto de la aplicación, tiene la opción de forma interoperables instrucciones SQL que depende del tipo de aplicación. Las aplicaciones personalizadas están menos probables que utiliza instrucciones SQL que interoperable porque normalmente están diseñadas para aprovechar las capacidades del DBMS de uno o dos posiblemente. Aplicaciones genéricas usar instrucciones SQL interoperables porque están diseñados para trabajar con una variedad de DBMS. Y las aplicaciones verticales suelen clasificarse en algún lugar entre, exigir un cierto nivel de funcionalidad, pero en caso contrario, use interoperables instrucciones SQL.  
  
 Esta sección contiene los temas siguientes.  
  
-   [Elegir una gramática SQL](../../../odbc/reference/develop-app/choosing-an-sql-grammar.md)  
  
-   [Crear instrucciones SQL Interoperable](../../../odbc/reference/develop-app/constructing-interoperable-sql-statements.md)
