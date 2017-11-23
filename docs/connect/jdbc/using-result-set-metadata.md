---
title: Metadatos del conjunto de resultado de usar | Documentos de Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e37529a-30db-48c8-b90a-ae9657d0f6b0
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d0753963363939c4ae5447d57859bc1d96fcb367
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2017
---
# <a name="using-result-set-metadata"></a>Usar metadatos del conjunto de resultados
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Para consultar un conjunto de resultados para obtener información acerca de las columnas que contiene, el [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] implementa la [SQLServerResultSetMetaData](../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md) clase. Esta clase contiene varios métodos que devuelven información como un solo valor.  
  
 Para crear un objeto SQLServerResultSetMetaData, puede usar el [getMetaData](../../connect/jdbc/reference/getmetadata-method-sqlserverresultset.md) método de la [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) clase.  
  
 En el ejemplo siguiente, una conexión abierta a la [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] base de datos de ejemplo se pasa a la función, se usa el método getMetaData de la clase SQLServerResultSet para devolver un objeto SQLServerResultSetMetaData y, a continuación, varios métodos de la Objeto SQLServerResultSetMetaData se usan para mostrar información sobre el nombre y tipo de datos de las columnas contenidas en el conjunto de resultados.  
  
 [!code[JDBC#UsingResultSetMetaData1](../../connect/jdbc/codesnippet/Java/using-result-set-metadata_1.java)]  
  
## <a name="see-also"></a>Vea también  
 [Controlar metadatos con el controlador JDBC](../../connect/jdbc/handling-metadata-with-the-jdbc-driver.md)  
  
  
