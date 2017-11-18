---
title: Uso de los metadatos de base de datos | Documentos de Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b048371-e912-4ed1-afd7-436978f48888
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 421da278e1a4503a73fb4f4f8a8aba0b3cff672f
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="using-database-metadata"></a>Usar metadatos de una base de datos
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Para consultar una base de datos para obtener información sobre compatibilidad, la [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] implementa la [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) clase. Esta clase contiene numerosos métodos que devuelven información en forma de un solo valor o de conjunto de resultados.  
  
 Para crear un objeto SQLServerDatabaseMetaData, puede usar el [getMetaData](../../connect/jdbc/reference/getmetadata-method-sqlserverconnection.md) método de la [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) clase para obtener información acerca de la base de datos que está conectado.  
  
 En el ejemplo siguiente, una conexión abierta a la [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] base de datos de ejemplo se pasa a la función, se usa el método getMetaData de la clase SQLServerConnection para devolver un objeto SQLServerDatabaseMetadata y, a continuación, varios métodos de la Objeto SQLServerDatabaseMetaData se usan para mostrar información sobre el controlador, versión del controlador, el nombre de base de datos y versión de base de datos.  
  
 [!code[JDBC#UsingDBMetaData1](../../connect/jdbc/codesnippet/Java/using-database-metadata_1.java)]  
  
## <a name="see-also"></a>Vea también  
 [Controlar metadatos con el controlador JDBC](../../connect/jdbc/handling-metadata-with-the-jdbc-driver.md)  
  
  

