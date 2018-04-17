---
title: Vistas de esquema | Documentos de Microsoft
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
- schema views [ODBC]
- functions [ODBC], catalog functions
- catalog functions [ODBC], schema views
ms.assetid: f1dfb3e8-a7bd-46c3-92b6-c19531e8409d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7b8e3ca94b82f74c8ba067faef9485359ff99aee
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="schema-views"></a>Vistas de esquema
Una aplicación puede recuperar información de metadatos de lo DBMS mediante una llamada a funciones de catálogo ODBC o mediante el uso de las vistas INFORMATION_SCHEMA. Las vistas se definen mediante el estándar ANSI SQL-92.  
  
 Si admite el controlador y el DBMS, las vistas INFORMATION_SCHEMA proporcionan un medio más eficaz y completa de recuperación de metadatos que proporcionan las funciones de catálogo ODBC. Una aplicación puede ejecutar su propio personalizado **seleccione** instrucción con una de estas vistas, puede unir las vistas, o puede realizar una unión en las vistas. Al tiempo que ofrece una gama más amplia de metadatos y de mayor utilidad, vistas INFORMATION_SCHEMA no se admiten con frecuencia el DBMS. Esto podría cambiar como más DBMS y controladores de lograr el cumplimiento de SQL-92.  
  
 Para determinar qué vistas se admiten, llama a una aplicación **SQLGetInfo** con la opción SQL_INFO_SCHEMA_VIEWS. Para recuperar los metadatos de una vista compatible, la aplicación ejecuta un **seleccione** instrucción que especifica la información de esquema necesaria.
