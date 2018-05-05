---
title: Clase SQLServerXADataSource | Documentos de Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 95fc7b07-2498-4a7e-8f7f-ee0d86b598b4
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b69edd13e84599e4e3e11ba56a3a1c34ee1d36ae
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="sqlserverxadatasource-class"></a>Clase SQLServerXADataSource
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Representa un generador para [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md) objetos que se usa internamente.  
  
 **Paquete:** com.microsoft.sqlserver.jdbc  
  
 **Extiende:** [SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)  
  
 **Implementa:** javax.sql.XADataSource  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public class SQLServerXADataSource  
```  
  
## <a name="remarks"></a>Comentarios  
 Un objeto que implementa la interfaz SQLServerXADataSource se registra normalmente con un servicio de nomenclatura que utiliza Java Naming and Directory Interface (JNDI).  
  
 La clase SQLServerXADataSource proporciona conexiones de base de datos para su uso en transacciones distribuidas (XA). La clase SQLServerXADataSource también admite la agrupación de conexiones físicas. Implementan las interfaces SQLServerXADataSource y SQLServerXAConnection, que se definen en el paquete javax.sql, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].  
  
 Un objeto SQLServerXAConnection es una conexión agrupada que puede participar en una transacción distribuida. Más concretamente, SQLServerXAConnection extiende la interfaz de SQLServerPooledConnection, agrega el método [getXAResource](../../../connect/jdbc/reference/getxaresource-method-sqlserverxaconnection.md). Este método genera una [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) objeto que puede utilizarse por un administrador de transacciones para coordinar el trabajo realizado en esta conexión con el resto de participantes en la transacción distribuida. Dado que extienden la interfaz SQLServerPooledConnection, objetos SQLServerXAConnection admiten todos los métodos de objetos de SQLServerPooledConnection. Se trata de conexiones físicas reutilizables a un origen de datos subyacente y generan controladores de conexión lógicos que se pueden devolver a una aplicación JDBC.  
  
 Objetos SQLServerXAConnection son generados por un objeto SQLServerXADataSource. Objetos de SQLServerConnectionPoolDataSource y SQLServerXADataSource son similares porque ambos se implementan bajo un nivel de origen de datos que es visible para la aplicación JDBC. Esta arquitectura permite [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] admite transacciones distribuidas de manera transparente a la aplicación. SQLServerXADataSource se puede configurar para integrarse con [!INCLUDE[msCoName](../../../includes/msconame_md.md)] Coordinador de transacciones distribuidas (DTC) para proporcionar true, distribuye el procesamiento de transacciones.  
  
## <a name="see-also"></a>Vea también  
 [Miembros de SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-members.md)   
 [Referencia de API del controlador JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
