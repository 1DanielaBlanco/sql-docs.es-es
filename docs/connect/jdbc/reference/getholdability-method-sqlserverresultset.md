---
title: "Método getHoldability (SQLServerResultSet) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4508d90f-c3c4-4eac-8001-fb0b93b66734
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ae5a5d40381cd6b7939e7e67b5950e3d0e3644d3
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="getholdability-method-sqlserverresultset"></a>Método getHoldability (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera la capacidad de alojamiento de este [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public int getHoldability()  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Un **int** valor que contiene uno de los siguientes niveles de capacidad de alojamiento:  
  
 HOLD_CURSORS_OVER_COMMIT  
  
 CLOSE_CURSORS_AT_COMMIT  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 Este método getHoldability especificado por el método getHoldability en la interfaz java.sql.ResultSet.  
  
 Para establecer la capacidad de alojamiento del conjunto de resultados, las aplicaciones pueden utilizar el [setHoldability](../../../connect/jdbc/reference/setholdability-method-sqlserverconnection.md) método de la [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) clase. Después de la [setHoldability](../../../connect/jdbc/reference/setholdability-method-sqlserverconnection.md) se llama al método y el objeto de instrucción y su objeto de conjunto de resultados se crean y se ejecuta la instrucción, la aplicación que tenga que volver a cambiar la capacidad de alojamiento.  
  
 Para los cursores de servidor, cuando están conectados a SQL Server 2005 o posteriores, la configuración de la capacidad de alojamiento solamente afecta a la de los nuevos conjuntos de resultados que todavía han de ser creados en esa conexión. Con SQL Server 2000, sin embargo, configurar la capacidad de alojamiento afecta a la capacidad de alojamiento de los resultados existentes como a la de los nuevos conjuntos de resultados que todavía han de ser creados en esa conexión.  
  
 Cuando se restablece la capacidad de alojamiento y se llama al método getHoldability en el resultado creado previamente el objeto de conjunto, el valor devuelto por este método puede ser diferente del valor de capacidad de alojamiento devuelto por los métodos siguientes: Statement.getResultSetHoldability , Connection.getHoldability o DatabaseMetaData.getResultSetHoldability.  
  
## <a name="see-also"></a>Vea también  
 [Miembros de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Clase SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

