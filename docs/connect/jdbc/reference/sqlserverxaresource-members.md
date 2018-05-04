---
title: Los miembros de SQLServerXAResource | Documentos de Microsoft
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
ms.assetid: a069bf2c-1b70-4817-b084-a508445de799
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 042e159030fde83ce41eb9aef8804f02c9d2ee8e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="sqlserverxaresource-members"></a>Miembros de SQLServerXAResource
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Las tablas siguientes enumeran los miembros expuestos por el [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) clase.  
  
## <a name="constructors"></a>Constructores  
 Ninguno.  
  
## <a name="fields"></a>Campos  
  
|Nombre|Description|  
|----------|-----------------|  
|[SSTRANSTIGHTLYCPLD](../../../connect/jdbc/reference/sstranstightlycpld-field-sqlserverxaresource.md)|Se utiliza para permitir transacciones XA estrechamente acopladas, las cuales tienen identificadores de rama de transacción XA diferentes (XID), pero tienen el mismo identificador de transacción global (GTRID).|  
  
## <a name="inherited-fields"></a>Campos heredados  
  
|Clase heredada de:|Métodos|  
|---------------------------|-------------|  
|javax.transaction.xa.XAResource|TMENDRSCAN, TMFAIL, TMJOIN, TMNOFLAGS, TMONEPHASE, TMRESUME, TMSTARTRSCAN, TMSUCCESS, TMSUSPEND, XA_OK, XA_RDONLY|  
  
## <a name="methods"></a>Métodos  
  
|Nombre|Description|  
|----------|-----------------|  
|[Confirmación](../../../connect/jdbc/reference/commit-method-sqlserverxaresource.md)|Confirma la transacción global especificada por el objeto Xid determinado.|  
|[Final](../../../connect/jdbc/reference/end-method-sqlserverxaresource.md)|Finaliza el trabajo realizado en nombre de una bifurcación de transacción.|  
|[olvidar](../../../connect/jdbc/reference/forget-method-sqlserverxaresource.md)|Indica al administrador de recursos que se olvide de una bifurcación de transacción completada heurísticamente.|  
|[getTransactionTimeout](../../../connect/jdbc/reference/gettransactiontimeout-method-sqlserverxaresource.md)|Obtiene el valor de tiempo de espera de transacción actual establecido para este [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) objeto.|  
|[isSameRM](../../../connect/jdbc/reference/issamerm-method-sqlserverxaresource.md)|Determina si la instancia del Administrador de recursos representada por el objeto de destino es igual a la instancia del Administrador de recursos representada por el objeto de XAResource determinado.|  
|[Preparar](../../../connect/jdbc/reference/prepare-method-sqlserverxaresource.md)|Solicitudes que prepara el Administrador de recursos para una confirmación de transacción de la transacción especificada por el objeto Xid dado.|  
|[recuperar](../../../connect/jdbc/reference/recover-method-sqlserverxaresource.md)|Obtiene una lista de bifurcaciones de transacción preparadas de un administrador de recursos.|  
|[Reversión](../../../connect/jdbc/reference/rollback-method-sqlserverxaresource.md)|Solicita que el administrador de recursos revierta el trabajo realizado en nombre de una bifurcación de transacción.|  
|[setTransactionTimeout](../../../connect/jdbc/reference/settransactiontimeout-method-sqlserverxaresource.md)|Establece el valor de tiempo de espera de la transacción actual de este [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) objeto.|  
|[start](../../../connect/jdbc/reference/start-method-sqlserverxaresource.md)|Comienza a funcionar en nombre de una bifurcación de transacción especificada en el objeto Xid.|  
  
## <a name="inherited-methods"></a>Métodos heredados  
  
|Clase heredada de:|Métodos|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
  
## <a name="see-also"></a>Vea también  
 [Clase SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
