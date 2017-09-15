---
title: "Método getObject (int) (SQLServerResultSet) | Documentos de Microsoft"
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
- SQLServerResultSet.getObject (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 94e59366-ca34-4cd5-a6ec-ae32d475ef36
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ec9e7c35152eafd09841994955fc0bd86f84ec01
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="getobject-method-int-sqlserverresultset"></a>Método getObject (int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Obtiene el valor de índice de columna designado en la fila actual de este [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objeto como un objeto en el lenguaje de programación Java.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public java.lang.Object getObject(int columnIndex)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *columnIndex*  
  
 Un **int** que indica el índice de columna.  
  
## <a name="return-value"></a>Valor devuelto  
 Un **objeto** valor.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 Este método getObject es especificado por el método getObject en la interfaz java.sql.ResultSet.  
  
 Este método devolverá el valor de la columna determinada como un objeto de Java. El tipo del objeto de Java será el tipo de objeto de Java predeterminado que corresponde al tipo SQL de la columna, tras la asignación para los tipos integrados que se indica en las especificaciones de JDBC. Si el valor es NULL de SQL, el controlador devuelve un NULL de Java.  
  
 Este método también se puede utilizar para leer los tipos de datos abstractos específicos de la base de datos. En la API de JDBC 2.0, el comportamiento del método getObject se extiende para materializar datos de tipos definidos por el usuario SQL. Cuando una columna contiene un valor estructurado o distinto, el comportamiento de este método es como si fuera una llamada a `getObject(columnIndex, this.getStatement().getConnection().getTypeMap())`.  
  
 A partir de la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] del controlador JDBC 3.0:  
  
-   Un valor de tipo date se devolverá como un objeto java.sql.Date.  
  
-   Un valor de tipo time se devolverá como un objeto java.sql.Time.  
  
-   Un valor de tipo datetime2 se devolverá como un objeto java.sql.Timestamp.  
  
-   Un valor de tipo datetimeoffset se devolverá como un objeto microsoft.sql.DateTimeOffset.  
  
## <a name="see-also"></a>Vea también  
 [Método getObject &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/getobject-method-sqlserverresultset.md)   
 [Miembros de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Clase SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
