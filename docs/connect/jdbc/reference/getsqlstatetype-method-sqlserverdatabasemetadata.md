---
title: "Método getSQLStateType (SQLServerDatabaseMetaData) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDatabaseMetaData.getSQLStateType
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ee4d6751-68a3-4d04-831c-e6d704c59e63
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6395cf4f457983cb7ac2540522deea5da93d9b78
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="getsqlstatetype-method-sqlserverdatabasemetadata"></a>Método getSQLStateType (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indica si SQLSTATE, que devolvió el método SQLException.getSQLState, es X/Open (ahora se denomina Open Group), SQL CLI, SQL99 (JDBC 3.0) o SQL:2003 (JDBC 4.0).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public int getSQLStateType()  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Un **int** que indica el tipo de SQLSTATE, que puede ser uno de los siguientes valores:  
  
-   Para la versión 5.0 de Java Runtime Environment: si la **xopenStates** propiedad de conexión se establece en **true**, este método devuelve DatabaseMetaData.sqlStateXOpen. En caso contrario, DatabaseMetaData.sqlStateSQL99.  
  
-   Para la versión 6.0 de Java Runtime Environment: si la **xopenStates** propiedad de conexión se establece en **true**, este método devuelve DatabaseMetaData.sqlStateXOpen. En caso contrario, DatabaseMetaData.sqlStateSQL.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 Este método getSQLStateType especificado por el método getSQLStateType en la interfaz java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>Vea también  
 [Métodos SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Miembros de SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Clase SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
