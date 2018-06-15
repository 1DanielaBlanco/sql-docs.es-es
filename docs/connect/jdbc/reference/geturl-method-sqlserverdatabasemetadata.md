---
title: Método getURL (SQLServerDatabaseMetaData) | Documentos de Microsoft
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
- SQLServerDatabaseMetaData.getURL
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: fcb66851-db5f-4ae8-b728-d129480b6f42
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2a247a542516c9579a31be0e8a0ad8e3401f36e8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32840520"
---
# <a name="geturl-method-sqlserverdatabasemetadata"></a>Método getURL (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera la dirección URL para esta base de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public java.lang.String getURL()  
```  
  
## <a name="return-value"></a>Valor devuelto  
 A **cadena** que contiene la dirección URL.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 Este método getURL especificado por el método getURL en la interfaz java.sql.DatabaseMetaData.  
  
 Cuando se usa el [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] con un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] la base de datos, este método devuelve un **cadena** valor que contiene la información siguiente:  
  
-   Un valor URL de "jdbc:sqlserver://"  
  
-   Propiedades de conexión opcionales, como **serverName**, **nombreDeInstancia**, y **númeroDePuerto**  
  
-   Otras propiedades de conexión establecen por el usuario y todas las conexiones propiedades con el controlador no está vacío o no null valores predeterminados excepto **nombre de usuario**, **contraseña**, y **integratedSecurity**.  
  
## <a name="see-also"></a>Vea también  
 [Métodos SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Miembros de SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Clase SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
