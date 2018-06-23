---
title: SQLDriverConnect | Documentos de Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLDriverConnect function
ms.assetid: a1e38e2c-3a97-42d1-9c45-a0ca3282ffd1
caps.latest.revision: 60
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2e83f19e8834004ebfe0a92f3471645a149332c2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36202104"
---
# <a name="sqldriverconnect"></a>SQLDriverConnect
  El controlador ODBC de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client define atributos de conexión que o reemplazan o mejoran las palabras clave de cadena de conexión. Algunas palabras clave de cadena de conexión tienen valores predeterminados que especifica el controlador ODBC de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
 Para obtener una lista de las palabras clave disponibles en la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] controlador ODBC de Native Client, vea [Using Connection String Keywords with SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Para obtener más información acerca de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] atributos de conexión y comportamientos predeterminados del controlador, vea [SQLSetConnectAttr](sqlsetconnectattr.md).  
  
 Para obtener una descripción de palabras clave de cadena de conexión que son válidos para [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, vea [Using Connection String Keywords with SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Cuando el `SQLDriverConnect` *DriverCompletion* valor del parámetro es SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE o SQL_DRIVER_COMPLETE_REQUIRED, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] controlador ODBC Native Client recupera los valores de palabra clave de la cuadro de diálogo mostrado. Si el valor de palabra clave se pasa en la cadena de conexión y el usuario no modifica el valor de la palabra clave en el cuadro de diálogo, el controlador ODBC de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client utiliza el valor de la cadena de conexión. Si el valor no está establecido en la cadena de conexión y el usuario no realiza ninguna asignación en el cuadro de diálogo, el controlador utiliza el valor predeterminado.  
  
 `SQLDriverConnect` debe proporcionarse un válido *WindowHandle* cuando se da alguna *DriverCompletion* valor requiere (o podrían requerir) la presentación del cuadro de diálogo de conexión del controlador. Un identificador no válido devuelve SQL_ERROR.  
  
 Especifique las palabras clave DRIVER o DSN. Si se indican ambas, ODBC especifica que un controlador utiliza la palabra clave del extremo izquierdo y omite la otra. Si el controlador se especifica o es el extremo izquierdo de los dos y el `SQLDriverConnect` *DriverCompletion* el valor del parámetro es SQL_DRIVER_NOPROMPT, la palabra clave SERVER y tiene un valor adecuado.  
  
 Cuando se especifica SQL_DRIVER_NOPROMPT, las palabras clave de autenticación de usuario deben estar presentes con valores. El controlador garantiza que la cadena "Trusted_Connection=yes" o que las palabras clave UID y PWD están presentes.  
  
 Si el *DriverCompletion* el valor del parámetro es SQL_DRIVER_NOPROMPT o SQL_DRIVER_COMPLETE_REQUIRED y el idioma o la base de datos procede de la cadena de conexión y no son válidos, `SQLDriverConnect` devuelve SQL_ERROR.  
  
 Si el *DriverCompletion* el valor del parámetro es SQL_DRIVER_NOPROMPT o SQL_DRIVER_COMPLETE_REQUIRED y el idioma o la base de datos procede de las definiciones de origen de datos ODBC y no son válidos, `SQLDriverConnect` utiliza el valor predeterminado idioma o base de datos para el Id. de usuario especificado y devuelve SQL_SUCCESS_WITH_INFO.  
  
 Si el *DriverCompletion* valor del parámetro es SQL_DRIVER_COMPLETE o SQL_DRIVER_PROMPT y si el idioma o la base de datos no es válida, `SQLDriverConnect` vuelve a mostrar el cuadro de diálogo.  
  
## <a name="sqldriverconnect-support-for-high-availability-disaster-recovery"></a>Compatibilidad de SQLDriverConnect para la alta disponibilidad con recuperación de desastres  
 Para obtener más información sobre el uso de `SQLDriverConnect` para conectarse a un [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] de clúster, consulte [SQL Server Native Client Support for High Availability, Disaster Recovery](../native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).  
  
## <a name="sqldriverconnect-support-for-service-principal-names-spns"></a>Compatibilidad de SQLDriverConnect con los Nombres principales de servicio (SPN)  
 SQLDDriverConnect utilizará el inicio de sesión de ODBC diálogo si están habilitados. Esto permite escribir SPN tanto para el servidor principal como para su asociado de conmutación por error.  
  
 SQLDriverConnect aceptará las nuevas palabras clave de cadena de conexión `ServerSPN` y `FailoverPartnerSPN`y reconocerá los nuevos atributos de conexión SQL_COPT_SS_SERVER_SPN y SQL_COPT_SS_FAILOVER_PARTNER_SPN.  
  
 Cuando un valor de atributo de conexión se especifica más de una vez, el valor que se establece mediante programación tiene prioridad sobre el valor de un DSN y el valor de una cadena de conexión. El valor de un DSN tiene prioridad sobre el valor de una cadena de conexión.  
  
 Cuando se abre una conexión, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client establece SQL_COPT_SS_MUTUALLY_AUTHENTICATED y SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD en el método de autenticación que se utiliza para abrir la conexión.  
  
 Para obtener más información acerca de los SPN, vea [nombres principales de servicio &#40;SPN&#41; en las conexiones de cliente &#40;ODBC&#41;](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).  
  
## <a name="examples"></a>Ejemplos  
 La llamada siguiente muestra la menor cantidad de datos necesarios para `SQLDriverConnect`:  
  
```  
SQLDriverConnect(hdbc, hwnd,  
    (SQLTCHAR*) TEXT("DRIVER={SQL Server Native Client 10};"), SQL_NTS, szOutConn,  
    MAX_CONN_OUT, &cbOutConn, SQL_DRIVER_COMPLETE);  
```  
  
 Las siguientes cadenas de conexión muestran los datos mínimos necesarios cuando el *DriverCompletion* el valor del parámetro es SQL_DRIVER_NOPROMPT:  
  
```  
"DSN=Human Resources;Trusted_Connection=yes"  
  
"FILEDSN=HR_FDSN;Trusted_Connection=yes"  
  
"DRIVER={SQL Server Native Client 10};SERVER=(local);Trusted_Connection=yes"  
```  
  
## <a name="see-also"></a>Vea también  
 [SQLDriverConnect, función](http://go.microsoft.com/fwlink/?LinkId=59340)   
 [Detalles de implementación de API de ODBC](odbc-api-implementation-details.md)   
 [SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql)   
 [SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql)   
 [SET ANSI_WARNINGS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-warnings-transact-sql)  
  
  
