---
title: "isClosed (método) (SQLServerConnection) | Documentos de Microsoft"
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
apiname: SQLServerConnection.isClosed
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 3560ab18-4350-4d02-9716-439f0c2f7142
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2f8c264171a4e91c4dd449f1ea8fa19830fb4ca1
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2017
---
# <a name="isclosed-method-sqlserverconnection"></a>isClosed (método) (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indica si este [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) objeto se ha cerrado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public boolean isClosed()  
```  
  
## <a name="return-value"></a>Valor devuelto  
 **True** si la conexión está cerrada, **false** si no lo está.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 Este método isClosed es especificado por el método isClosed en la interfaz java.sql.Connection.  
  
 Comprueba el estado del objeto SQLServerConnection que se llama. Se cierra una conexión si la [cerrar](../../../connect/jdbc/reference/close-method-sqlserverconnection.md) método se ha llamado en ella, o si se han producido ciertos errores irrecuperables. Este método devolverá **true** sólo cuando se llama después de haber llamado al método close.  
  
## <a name="see-also"></a>Vea también  
 [Miembros de SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Clase SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
