---
title: Método setDateTimeOffset (SQLServerCallableStatement) | Documentos de Microsoft
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
ms.topic: article
ms.assetid: 9383e14d-c83e-43c5-980c-50a3e0bedc31
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7cb10e1ad319cb3ea785db25e13bc193f4e972fd
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="setdatetimeoffset-method-sqlservercallablestatement"></a>Método setDateTimeOffset (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Este método se agregó en [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] controlador JDBC 3.0.  
  
 Establece el valor de la columna especificada en el [clase DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) valor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public void setDateTimeOffset(String sCol, microsoft.sql.DateTimeOffset t)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *sCol*  
  
 El nombre de una columna.  
  
 *T*  
  
 El [clase DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) objeto.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 Puede recuperar un [clase DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) valor con [SQLServerCallableStatement.getDateTimeOffset](../../../connect/jdbc/reference/getdatetimeoffset-method-sqlservercallablestatement.md).  
  
 [setDateTimeOffset](../../../connect/jdbc/reference/setdatetimeoffset-method-sqlserverpreparedstatement.md) toma el ordinal de la columna.  
  
## <a name="see-also"></a>Vea también  
 [Miembros de SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Clase SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
