---
title: Método Execute (java.lang.String) | Documentos de Microsoft
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
- SQLServerPreparedStatement.execute (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a871917e-d286-46c3-96cf-2e8e8b22111c
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4358b323f2ec6bdbc87609c2dadb0d97cbd104fc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32830580"
---
# <a name="execute-method-javalangstring"></a>Método execute (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ejecuta la instrucción SQL determinada, que puede devolver varios resultados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public final boolean execute(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *sql*  
  
 A **cadena** que contiene una instrucción SQL.  
  
## <a name="return-value"></a>Valor devuelto  
 **True** si la instrucción devuelve un conjunto de resultados. **false** si devuelve un recuento de actualización o ningún resultado.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 Este método de ejecución especificado por el método execute en la interfaz java.sql.Statement.  
  
 Este método invalida el [ejecutar](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md) método que se encuentra en la [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) clase.  
  
 Llamar a este método producirá una excepción porque la instrucción SQL para el objeto SQLServerPreparedStatement no se especifica cuando se crea el objeto.  
  
## <a name="see-also"></a>Vea también  
 [ejecutar el método &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/execute-method-sqlserverpreparedstatement.md)   
 [Miembros de SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Clase SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
