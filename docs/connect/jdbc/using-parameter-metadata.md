---
title: "Uso de los metadatos de parámetro | Documentos de Microsoft"
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
ms.assetid: db2c1957-91c6-4989-a07b-9f8be6d2033a
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d50af4d0d22d6042230fed2ee6b989fb7c53408d
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="using-parameter-metadata"></a>Usar metadatos de parámetros
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Para consultar un [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) o un [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) objeto acerca de los parámetros que contienen, el [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] implementa el [ SQLServerParameterMetaData](../../connect/jdbc/reference/sqlserverparametermetadata-class.md) clase. Esta clase contiene numerosos campos y métodos que devuelven información en forma de un solo valor.  
  
 Para crear un objeto SQLServerParameterMetaData, puede usar el [getParameterMetaData](../../connect/jdbc/reference/getparametermetadata-method-sqlserverpreparedstatement.md) métodos de las clases SQLServerPreparedStatement y SQLServerCallableStatement.  
  
 En el ejemplo siguiente, una conexión abierta a la [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] base de datos de ejemplo se pasa a la función, se usa el método getParameterMetaData de la clase SQLServerCallableStatement para devolver un objeto SQLServerParameterMetaData y, a continuación, varios métodos del objeto SQLServerParameterMetaData se usan para mostrar información sobre el tipo y el modo de los parámetros que se encuentran dentro del procedimiento almacenado HumanResources.uspUpdateEmployeeHireInfo.  
  
 [!code[JDBC#UsingParamMetaData1](../../connect/jdbc/codesnippet/Java/using-parameter-metadata_1.java)]  
    
> [!NOTE]  
Existen algunas limitaciones cuando se usa la clase SQLServerParameterMetaData con instrucciones preparadas. 
**Microsoft JDBC Driver 6.0 (o superior) para SQL Server**: al usar SQL Server 2008 o 2008 R2, el controlador JDBC admite instrucciones SELECT, DELETE, INSERT y UPDATE siempre y cuando estas instrucciones no contengan subconsultas o combinaciones. Las consultas de combinación también no se admiten para la clase SQLServerParameterMetaData al usar SQL Server 2008 o 2008 R2. Para SQL Server 2012 y versiones superiores, se admiten metadatos de parámetros con consultas complejas. No se admite la recuperación de metadatos de parámetros para las columnas cifradas. **Con Microsoft JDBC Driver 4.0, 4.1 o 4.2 para SQL Server**: el controlador es compatible con las instrucciones SELECT, DELETE, INSERT y UPDATE siempre y cuando estas instrucciones no contengan subconsultas o combinaciones. También, las consultas de combinación no se admiten para la clase SQLServerParameterMetaData.  

## <a name="see-also"></a>Vea también  
 [Controlar metadatos con el controlador JDBC](../../connect/jdbc/handling-metadata-with-the-jdbc-driver.md)  
  
  

