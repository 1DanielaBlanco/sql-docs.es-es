---
title: "Método getSchemaTerm (SQLServerDatabaseMetaData) | Documentos de Microsoft"
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
apiname: SQLServerDatabaseMetaData.getSchemaTerm
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 3e4a400f-0859-4ac3-983e-c25633b33683
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 50df53f6f7eae8c825a9420aaf24288081e413f5
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2017
---
# <a name="getschematerm-method-sqlserverdatabasemetadata"></a>Método getSchemaTerm (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera el término preferido para "esquema" en esta base de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public java.lang.String getSchemaTerm()  
```  
  
## <a name="return-value"></a>Valor devuelto  
 A **cadena** que contiene el término preferido.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 Este método getSchemaTerm especificado por el método getSchemaTerm en la interfaz java.sql.DatabaseMetaData.  
  
 Cuando se usa el [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] con un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] base de datos, este método devuelve "esquema" como el término preferido.  
  
## <a name="see-also"></a>Vea también  
 [Métodos SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Miembros de SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Clase SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
