---
title: getEnablePrepareOnFirstPreparedStatementCall (método) (SQLServerConnection) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerConnection.getEnablePrepareOnFirstPreparedStatementCall
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
caps.latest.revision: 1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7839e70a612a59cbf08b82e3453d53cc84abe9a5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32834560"
---
# <a name="getenableprepareonfirstpreparedstatementcall-method-sqlserverconnection"></a>getEnablePrepareOnFirstPreparedStatementCall (método) (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Devuelve el valor de **enablePrepareOnFirstPreparedStatementCall** propiedad de conexión. Si es false, la primera ejecución llamará sp_executesql y no preparar una instrucción, una vez que la segunda ejecución sucede lo llamaremos sp_prepexec y configurar realmente un identificador de instrucción preparada. Después de las ejecuciones llamará a sp_execute. Esto evita la necesidad de sp_unprepare en la instrucción preparada cierre si la instrucción solo se ejecuta una vez. El valor predeterminado de esta opción se puede cambiar por setDefaultEnablePrepareOnFirstPreparedStatementCall() que realiza la llamada.

## <a name="syntax"></a>Sintaxis  
  
```  
  
public boolean getEnablePrepareOnFirstPreparedStatementCall()  
```  

## <a name="return-value"></a>Valor devuelto
 A **booleano** que contiene el valor de **enablePrepareOnFirstPreparedStatementCall** propiedad de conexión.

## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Comentarios  
 Este método está disponible desde la versión del controlador JDBC 6.4 y hacia delante.
 
## <a name="see-also"></a>Vea también  
 [Miembros de SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Clase SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
