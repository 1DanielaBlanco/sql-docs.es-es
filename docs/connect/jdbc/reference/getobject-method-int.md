---
title: "Método getObject (int) | Documentos de Microsoft"
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
apiname: SQLServerCallableStatement.getObject (jnt)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: c4b8366b-c065-48e1-b712-19e2d9834228
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c68b20ad1ee124a1244d67fecce2ebc82b9cfbb5
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2017
---
# <a name="getobject-method-int"></a>Método getObject (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera el valor del parámetro designado como un objeto en el lenguaje de programación Java según el índice del parámetro.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public java.lang.Object getObject(int index)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *índice*  
  
 Un **int** que indica el índice del parámetro.  
  
## <a name="return-value"></a>Valor devuelto  
 Un **objeto** valor.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 Este método getObject es especificado por el método getObject en la interfaz java.sql.CallableStatement.  
  
 Este método devolverá el valor de la columna determinada como un objeto de Java. El tipo del objeto de Java será el tipo de objeto de Java predeterminado que corresponde al tipo SQL de la columna, tras la asignación para los tipos integrados que se indica en las especificaciones de JDBC. Si el valor es NULL de SQL, el controlador devuelve un NULL de Java.  
  
 Este método también se puede utilizar para leer los tipos de datos abstractos específicos de la base de datos. En JDBC 2.0, el comportamiento del método getObject se extiende para materializar datos de tipos definidos por el usuario SQL. Cuando una columna contiene un valor estructurado o distinto, el comportamiento de este método es como si fuera una llamada a `getObject(columnIndex, this.getStatement().getConnection().getTypeMap())`.  
  
 A partir de la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] del controlador JDBC 3.0:  
  
-   Un valor de tipo **fecha** se devolverá como un objeto java.sql.Date.  
  
-   Un valor de tipo **tiempo** se devolverá como un objeto java.sql.Time.  
  
-   Un valor de tipo **datetime2** se devolverá como un objeto java.sql.Timestamp.  
  
-   Un valor de tipo **datetimeoffset** se devolverá como un objeto microsoft.sql.DateTimeOffset.  
  
## <a name="see-also"></a>Vea también  
 [Método getObject &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getobject-method-sqlservercallablestatement.md)   
 [Miembros de SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Clase SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
