---
title: Trabajar con tipos de datos (JDBC) | Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b39f44d0-3710-4bc6-880c-35bd8c10a734
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 857f05430f963e085d47fad633d0039e2bbd7fb2
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39453099"
---
# <a name="working-with-data-types-jdbc"></a>Trabajar con tipos de datos (JDBC)

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

La función principal del [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] es permitir a los desarrolladores de Java el acceso a datos contenidos en bases de datos de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]. Para ello, el controlador JDBC realiza la conversión entre los tipos de datos de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] y los tipos y objetos en lenguaje Java.  
  
> [!NOTE]  
> Para obtener una descripción detallada de los tipos de datos de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] y el controlador JDBC, incluidas sus diferencias y el modo de conversión a los tipos de datos en lenguaje Java, vea [Describir los tipos de datos del controlador JDBC](../../../connect/jdbc/understanding-the-jdbc-driver-data-types.md).  
  
Para trabajar con los tipos de datos de SQL Server, el controlador JDBC proporciona los métodos get\<Type> y set\<Type> para las clases [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) y [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md), y proporciona los métodos get\<Type> y update\<Type> para la clase [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md). El método usado depende del tipo de datos con que se trabaja y del uso de conjuntos de resultados o consultas.  
  
En los temas de esta sección se describe cómo usar los tipos de datos del controlador JDBC para obtener acceso a los datos de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] en las aplicaciones de Java.  
  
## <a name="in-this-section"></a>En esta sección  
  
| Tema                                                                         | Descripción                                                                                                                                                                                                                                                  |
| ----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [Ejemplo de tipos de datos básicos](../../../connect/jdbc/code-samples/basic-data-types-sample.md)   | Describe cómo usar los métodos captadores del conjunto de resultados para recuperar valores de tipos de datos básicos de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] y cómo usar los métodos de actualización del conjunto de resultados para actualizar dichos valores.                                             |
| [Ejemplos de tipos de datos SQLXML](../../../connect/jdbc/code-samples/sqlxml-data-type-sample.md)   | Describe cómo almacenar datos XML en una base de datos relacional, cómo recuperar datos XML desde una base de datos y cómo analizar datos XML con el tipo de datos Java de **SQLXML**.                                                                                   |
| [Ejemplo de tipos de datos espaciales](../../../connect/jdbc/code-samples/spatial-data-types-sample.md) | Describe cómo almacenar los tipos de datos espaciales en SQL Server y cómo recuperar estos tipos desde SQL Server. También se explica cómo usar las clases recién definidas **geometría** y **Geography** desde el controlador, para administrar la referencia de Java de estos tipos de datos. |
  
## <a name="see-also"></a>Ver también

[Aplicaciones del controlador JDBC de ejemplo](../../../connect/jdbc/code-samples/sample-jdbc-driver-applications.md)  
