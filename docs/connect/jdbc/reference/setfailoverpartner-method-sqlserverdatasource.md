---
title: "Método setFailoverPartner (SQLServerDataSource) | Documentos de Microsoft"
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
apiname: SQLServerDataSource.setFailoverPartner
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 5310b7c2-9d10-474f-ad3a-218fe5da694b
caps.latest.revision: "17"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7aa59563e6980ef29f3e53e19519b83bcac8d721
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2017
---
# <a name="setfailoverpartner-method-sqlserverdatasource"></a>Método setFailoverPartner (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Establece el nombre del servidor de conmutación por error que se utiliza en una configuración de creación de reflejo de la base de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public void setFailoverPartner(java.lang.String serverName)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *serverName*  
  
 A **cadena** que contiene el nombre del servidor de conmutación por error.  
  
## <a name="remarks"></a>Comentarios  
 El valor que establece este método se utiliza en caso de que se produzca un error en la conexión inicial con el servidor principal; una vez se haya establecido la conexión inicial, se ignora el valor. El [setDatabaseName](../../../connect/jdbc/reference/setdatabasename-method-sqlserverdatasource.md) método también debe utilizarse junto con este método o se producirá una excepción.  
  
 El controlador no admite especificar el número de puerto del servidor de conmutación por error cuando se establece el nombre de servidor de conmutación por error. Sin embargo, al llamar a la [setServerName](../../../connect/jdbc/reference/setservername-method-sqlserverdatasource.md) método y [setInstanceName](../../../connect/jdbc/reference/setinstancename-method-sqlserverdatasource.md) método con el [setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md) método es compatible.  
  
## <a name="see-also"></a>Vea también  
 [Miembros SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Clase SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
