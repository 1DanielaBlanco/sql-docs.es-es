---
title: "Método setSendTimeAsDatetime (SQLServerDataSource) | Documentos de Microsoft"
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
ms.assetid: 705a0494-b5e2-43db-940a-1b8cec550cdb
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 15c5d74916499297596a0a22676c8e8fd5465b74
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2017
---
# <a name="setsendtimeasdatetime-method-sqlserverdatasource"></a>Método setSendTimeAsDatetime (SQLServerDataSource) 
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Este método se agregó en [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] controlador JDBC 3.0.  
  
 Modifica la configuración de la **sendTimeAsDatetime** propiedad de conexión.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public void setSendTimeAsDatetime(boolean sendTimeAsDateTime)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *sendTimeAsDateTime*  
  
 Valor booleano. Cuando sea true, produce valores java.sql.Time que se envían al servidor como [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] **datetime** tipos. Cuando sea false, produce valores java.sql.Time que se envían al servidor como [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] **tiempo** tipos.  
  
## <a name="remarks"></a>Comentarios  
 [SQLServerDataSource.getSendTimeAsDatetime](../../../connect/jdbc/reference/getsendtimeasdatetime-method-sqlserverdatasource.md) devuelve el valor de la **sendTimeAsDatetime** propiedad de conexión.  
  
 Para obtener más información sobre la **sendTimeAsDatetime** propiedad de conexión, consulte [estableciendo las propiedades de conexión](../../../connect/jdbc/setting-the-connection-properties.md).  
  
 Para obtener más información, consulte [java.sql.Time cómo configurar los valores se envían al servidor](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>Vea también  
 [Miembros SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Clase SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
