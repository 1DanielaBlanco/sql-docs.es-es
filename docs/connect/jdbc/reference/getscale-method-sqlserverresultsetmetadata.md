---
title: Método getScale (SQLServerResultSetMetaData) | Documentos de Microsoft
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
- SQLServerResultSetMetaData.getScale
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: fe29aa5f-4cc5-413f-8bbd-a58064993d87
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c232439723b1fbeccd81a9a35ddb0cd8d7602642
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="getscale-method-sqlserverresultsetmetadata"></a>Método getScale (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Obtiene el número de dígitos que se encuentran a la derecha del separador decimal para la columna designada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public int getScale(int column)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *column*  
  
 Un **int** que indica el índice de columna.  
  
## <a name="return-value"></a>Valor devuelto  
 Un **int** que indica la escala de la columna.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 Este método getScale especificado por el método getScale en la interfaz java.sql.ResultSetMetaData.  
  
 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Controlador JDBC 3.0 de incorpora cambios de comportamiento en la columna DECIMAL_DIGITS. Vea [SQLServerDatabaseMetaData.getColumns](../../../connect/jdbc/reference/getcolumns-method-sqlserverdatabasemetadata.md) para obtener más información.  
  
## <a name="see-also"></a>Vea también  
 [Miembros de SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [Clase SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
