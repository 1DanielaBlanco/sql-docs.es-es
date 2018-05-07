---
title: Funciones del sistema | Documentos de Microsoft
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
- system functions [ODBC]
- functions [ODBC], system functions
ms.assetid: 36614b4c-e037-43ef-8692-67f4861b144d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d5bfd40b587956595bfc8c35b4bb030543253cd9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="system-functions"></a>Funciones del sistema
En la tabla siguiente enumera las funciones de sistema que se incluyen en el conjunto de funciones escalares de ODBC. Mediante una llamada a **SQLGetInfo** con una *tipo de información* de SQL_SYSTEM_FUNCTIONS, una aplicación puede determinar qué funciones del sistema son compatibles con un controlador.  
  
 Argumentos que se denotan *exp* puede ser el nombre de una columna, el resultado de otra función escalar o un literal, donde el tipo de datos subyacente podría representar como SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL _BIGINT SQL_FLOAT, SQL_REAL, SQL_DOUBLE, SQL_TYPE_DATE, SQL_TYPE_TIME y SQL_TYPE_TIMESTAMP.  
  
 Argumentos que se denotan *valor* puede ser una constante literal, donde se puede representar el tipo de datos subyacente como SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_FLOAT, SQL_REAL, SQL_DOUBLE, SQL_ TYPE_DATE, SQL_TYPE_TIME y SQL_TYPE_TIMESTAMP.  
  
 Valores devueltos se representan como tipos de datos ODBC.  
  
|Función|Description|  
|--------------|-----------------|  
|**() DE LA BASE DE DATOS** (ODBC 1.0)|Devuelve el nombre de la base de datos correspondiente al identificador de conexión. (El nombre de la base de datos también está disponible mediante una llamada a **SQLGetConnectOption** con la opción de conexión SQL_CURRENT_QUALIFIER.)|  
|**IFNULL (** *exp*,*valor ***)** (ODBC 1.0)|Si *exp* es null, *valor* se devuelve. Si *exp* no es null, *exp* se devuelve. El tipo de datos o tipos de *valor* debe ser compatible con el tipo de datos de *exp*.|  
|**USUARIO ()** (ODBC 1.0)|Devuelve el nombre de usuario en el DBMS. (El nombre de usuario también está disponible por medio de **SQLGetInfo** especificando el tipo de información: SQL_USER_NAME.) Esto puede ser distinto del nombre de inicio de sesión.|
