---
title: Método getBigDecimal (java.lang.String, int) (SQLServerResultSet) | Documentos de Microsoft
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
apiname:
- SQLServerResultSet.getBigDecimal (java.lang.String, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 572a1799-c232-400f-b8d8-37a5719a8d5e
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b48bbf317da6f9f343a0a418d8dc29b0bb10fdc8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="getbigdecimal-method-javalangstring-int-sqlserverresultset"></a>Método getBigDecimal (java.lang.String, int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera el valor del nombre de columna designado en la fila actual de este [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objeto mediante la escala especificada.  
  
> [!NOTE]  
>  Este método se ha dejado de incluir en las especificaciones de JDBC. En su lugar, debe utilizar el [getBigDecimal (java.lang.String)](../../../connect/jdbc/reference/getbigdecimal-method-java-lang-string-sqlserverresultset.md) método.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public java.math.BigDecimal getBigDecimal(java.lang.String columnName,  
                                          int scale)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *columnName*  
  
 A **cadena** que contiene el nombre de columna.  
  
 *escala*  
  
 Un **int** que indica el número de dígitos a la derecha del separador decimal.  
  
## <a name="return-value"></a>Valor devuelto  
 Un objeto BigDecimal.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 Este método getBigDecimal especificado por el método getBigDecimal en la interfaz java.sql.ResultSet.  
  
## <a name="see-also"></a>Vea también  
 [Método getBigDecimal &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getbigdecimal-method-sqlserverresultset.md)   
 [Miembros de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Clase SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
