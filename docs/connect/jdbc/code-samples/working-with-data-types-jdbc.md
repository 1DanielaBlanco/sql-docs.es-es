---
title: Trabajar con tipos de datos (JDBC) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b39f44d0-3710-4bc6-880c-35bd8c10a734
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 49bc94f966bae9ae92e101789aa072f2ce398601
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="working-with-data-types-jdbc"></a>Trabajar con tipos de datos (JDBC)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  La función principal de la [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] consiste en permitir a los desarrolladores de Java tener acceso a datos contenidos en [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] bases de datos. Para lograr esto, el controlador JDBC realiza la conversión entre [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] tipos de datos y tipos del lenguaje Java y objetos.  
  
> [!NOTE]  
>  Para obtener una explicación detallada de la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] y tipos de datos del controlador JDBC, incluidas sus diferencias y cómo se convierten en tipos de datos de lenguaje de Java, consulte [descripción de los tipos de datos del controlador JDBC](../../../connect/jdbc/understanding-the-jdbc-driver-data-types.md).  
  
 Para trabajar con tipos de datos de SQL Server, el controlador JDBC proporciona get\<tipo > y establezca\<tipo > métodos para la [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) y [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md) clases y proporciona get\<tipo > y actualizar\<tipo > métodos para la [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) clase. El método usado depende del tipo de datos con que se trabaja y del uso de conjuntos de resultados o consultas.  
  
 Los temas de esta sección describen cómo utilizar los tipos de datos del controlador JDBC para tener acceso a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] datos en las aplicaciones de Java.  
  
## <a name="in-this-section"></a>En esta sección  
  
|Tema|Description|  
|-----------|-----------------|  
|[Ejemplo de tipos de datos básicos](../../../connect/jdbc/basic-data-types-sample.md)|Describe cómo utilizar métodos de captador del conjunto de resultados para recuperar básica [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] valores y cómo usar los métodos de actualización del conjunto de resultados para actualizar dichos valores de tipo de datos.|  
|[Ejemplos de tipos de datos SQLXML](../../../connect/jdbc/sqlxml-data-type-sample.md)|Describe cómo almacenar datos XML en una base de datos relacional, cómo recuperar datos XML desde una base de datos y cómo analizar datos XML con la **SQLXML** tipo de datos de Java.|  
  
## <a name="see-also"></a>Vea también  
 [Aplicaciones del controlador JDBC de ejemplo](../../../connect/jdbc/sample-jdbc-driver-applications.md)  
  
  
