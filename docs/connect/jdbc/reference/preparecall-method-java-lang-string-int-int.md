---
title: Método prepareCall (java.lang.String, int, int) | Documentos de Microsoft
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
- SQLServerConnection.prepareCall (java.lang.String, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 04d36a25-7f95-4675-9690-4462671b3d67
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9b3eb39174f6164d76c4e60eada168987871abc9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32842170"
---
# <a name="preparecall-method-javalangstring-int-int"></a>Método prepareCall (java.lang.String, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crea un [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md) objeto que genera [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objetos con el tipo y simultaneidad especificados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public java.sql.CallableStatement prepareCall(java.lang.String sql,  
                                              int resultSetType,  
                                              int resultSetConcurrency)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *sql*  
  
 A **cadena** que contiene una instrucción SQL.  
  
 *resultSetType*  
  
 Un **int** que indica el tipo de conjunto de lo resultados.  
  
 *resultSetConcurrency*  
  
 Un **int** que indica el tipo de simultaneidad del conjunto de lo resultados.  
  
## <a name="return-value"></a>Valor devuelto  
 Un objeto CallableStatement.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 Este método prepareCall especificado por el método prepareCall de la interfaz java.sql.Connection.  
  
## <a name="see-also"></a>Vea también  
 [Método prepareCall &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md)   
 [Miembros de SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Clase SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
