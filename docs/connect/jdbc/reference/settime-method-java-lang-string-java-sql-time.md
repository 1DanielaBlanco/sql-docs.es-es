---
title: setTime (método) al valor de hora | Documentos de Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.setTime (java.lang.String, java.lang.Time)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 49301bec-6cf2-43fb-9d4e-e3986164a208
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8b753628708655b026bfe4bf297862873d36569c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32853430"
---
# <a name="settime-method-javalangstring-javasqltime"></a>Método setTime (java.lang.String, java.sql.Time)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Establece el parámetro designado para el valor de hora determinado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public void setTime(java.lang.String sCol,  
                    java.sql.Time t)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *sCol*  
  
 A **cadena** que contiene el nombre del parámetro.  
  
 *T*  
  
 Un objeto de tiempo.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 Este método setTime es especificado por el método setTime en la interfaz java.sql.CallableStatement.  
  
 A partir de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] controlador JDBC 3.0, el comportamiento de este método es modificado por la **sendTimeAsDatetime** propiedad de conexión ([estableciendo las propiedades de conexión](../../../connect/jdbc/setting-the-connection-properties.md)) y [ SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md).  
  
 Para obtener más información, consulte [java.sql.Time cómo configurar los valores se envían al servidor](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>Vea también  
 [Método setTime &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/settime-method-sqlservercallablestatement.md)   
 [Miembros de SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Clase SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
