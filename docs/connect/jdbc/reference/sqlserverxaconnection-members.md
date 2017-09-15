---
title: Los miembros de SQLServerXAConnection | Documentos de Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4b61dabd-369b-460c-8450-9fe424f76541
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0303bdf87283f2a7fba87b58991239f5d92a10d7
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverxaconnection-members"></a>Miembros de SQLServerXAConnection
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Las siguientes tablas enumeran los miembros expuestos por el [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md) clase.  
  
## <a name="constructors"></a>Constructores  
 Ninguno.  
  
## <a name="fields"></a>Campos  
 Ninguno.  
  
## <a name="inherited-fields"></a>Campos heredados  
 Ninguno.  
  
## <a name="methods"></a>Métodos  
  
|Nombre|Description|  
|----------|-----------------|  
|[addConnectionEventListener](../../../connect/jdbc/reference/addconnectioneventlistener-method-sqlserverpooledconnection.md)|(Se hereda de [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)) registra el agente de escucha de evento determinado para que se notificará cuando se produce un evento en este objeto de conexión.|  
|[Cerrar](../../../connect/jdbc/reference/close-method-sqlserverpooledconnection.md)|(Se hereda de [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)) se cierra la conexión física que representa este objeto de conexión.|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverpooledconnection.md)|(Se hereda de [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)) crea un identificador de objeto para la conexión física que representa este objeto de conexión.|  
|[getXAResource](../../../connect/jdbc/reference/getxaresource-method-sqlserverxaconnection.md)|Recupera un [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) objeto que el Administrador de transacciones se empleará para administrar la participación de este [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md) objeto en una transacción distribuida.|  
|[removeConnectionEventListener](../../../connect/jdbc/reference/removeconnectioneventlistener-method-sqlserverpooledconnection.md)|(Se hereda de [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)) quita el agente de escucha de eventos especificado.|  
  
## <a name="inherited-methods"></a>Métodos heredados  
  
|Clase heredada de:|Métodos|  
|---------------------------|-------------|  
|com.microsoft.sqlserver.jdbc.SQLServerPooledConnection|addConnectionEventListener, close, getConnection, removeConnectionEventListener|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|javax.sql.PooledConnection|addConnectionEventListener, close, getConnection, removeConnectionEventListener|  
  
## <a name="see-also"></a>Vea también  
 [Clase SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md)  
  
  
