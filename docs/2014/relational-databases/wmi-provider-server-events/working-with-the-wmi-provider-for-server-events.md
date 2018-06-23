---
title: Trabajar con el proveedor WMI para eventos de servidor | Documentos de Microsoft
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
helpviewer_keywords:
- event notifications [WMI]
- permissions [WMI]
- connection strings [WMI]
- security [WMI]
- Service Broker [WMI]
- WMI Provider for Server Events, connection strings
- WMI Provider for Server Events, Service Broker
- notifications [WMI]
- WMI Provider for Server Events, security
ms.assetid: cd974b3b-2309-4a20-b9be-7cfc93fc4389
caps.latest.revision: 33
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3ec2d4c6fa276c3938de0dc15062d026fe91dc80
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36106290"
---
# <a name="working-with-the-wmi-provider-for-server-events"></a>Trabajar con el proveedor WMI para eventos de servidor
  En este tema se proporcionan instrucciones que deben tenerse en cuenta antes de programar con el proveedor WMI para eventos del servidor.  
  
## <a name="enabling-service-broker"></a>Habilitar Service Broker  
 El proveedor WMI para eventos del servidor funciona traduciendo las consultas WQL para los eventos en notificaciones de eventos en la base de datos de destino. Entender la forma en que funcionan las notificaciones de eventos puede resultar de gran utilidad a la hora de programar con el proveedor. Para obtener más información, vea [Conceptos del proveedor WMI para eventos de servidor](http://technet.microsoft.com/library/ms180560.aspx).  
  
 En concreto, debido a que las notificaciones de eventos creadas por el proveedor WMI usan [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para enviar mensajes sobre eventos del servidor, este servicio debe estar habilitado dondequiera que se generen los eventos. Si un programa consulta los eventos en una instancia del servidor, el [!INCLUDE[ssSB](../../includes/sssb-md.md)] debe habilitarse en la base de datos msdb de dicha instancia, porque esa es la ubicación del servicio [!INCLUDE[ssSB](../../includes/sssb-md.md)] de destino (denominado SQL/Notifications/ProcessWMIEventProviderNotification/v1.0) creado por el proveedor. Si su programa consulta eventos en una base de datos o en un objeto de base de datos determinado, [!INCLUDE[ssSB](../../includes/sssb-md.md)] debe habilitarse en dicha base de datos de destino. Si el [!INCLUDE[ssSB](../../includes/sssb-md.md)] correspondiente no está habilitado una vez implementada la aplicación, los eventos generados por la notificación de eventos subyacentes se envían a la cola del servicio usada por la notificación de eventos, pero no se devuelven a la aplicación de administración WMI hasta que se habilita [!INCLUDE[ssSB](../../includes/sssb-md.md)].  
  
 La consulta siguiente determina qué Service Broker está habilitado en una instancia del servidor y el GUID de la instancia del Service Broker:  
  
```  
SELECT name, is_broker_enabled, service_broker_guid FROM sys.databases;  
```  
  
 El GUID de Service Broker de msdb tiene un interés particular porque es la ubicación del servicio de destino del proveedor.  
  
 Para habilitar [!INCLUDE[ssSB](../../includes/sssb-md.md)] en una base de datos, utilice la opción ENABLE_BROKER SET de la [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) instrucción.  
  
## <a name="specifying-a-connection-string"></a>Especificar una cadena de conexión  
 Las aplicaciones dirigen el proveedor WMI para eventos del servidor a una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mediante la conexión a un espacio de nombres WMI definido por el proveedor. El servicio WMI de Windows asigna este espacio de nombres al archivo DLL del proveedor, Sqlwep.dll, y lo carga en memoria. Cada instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tiene su propio espacio de nombres WMI, cuyo valor predeterminado es: \\ \\.\\ *raíz*\Microsoft\SqlServer\ServerEvents\\*instance_name*. *instance_name* el valor predeterminado es MSSQLSERVER en una instalación predeterminada de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="permissions-and-server-authentication"></a>Permisos y autenticación del servidor  
 Para obtener acceso al proveedor WMI para eventos del servidor, el cliente donde se origina una aplicación de administración WMI debe corresponderse con el grupo o el inicio de sesión autenticado de Windows de la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] especificada en la cadena de conexión de la aplicación.  
  
## <a name="permissions-and-event-notification-scope"></a>Permisos y ámbito de las notificaciones de eventos  
 El proveedor WMI para eventos del servidor traduce las consultas WQL en notificaciones de eventos en la base de datos de destino. Por ello, la aplicación que realiza la llamada no solo debe disponer de los permisos mínimos necesarios para obtener acceso al proveedor, sino que también debe disponer de los permisos correctos en la base de datos para crear las notificaciones de eventos necesarias. A continuación se indican los permisos necesarios:  
  
-   Para crear una notificación de eventos en el ámbito de la base de datos se requiere, como mínimo, el permiso CREATE DATABASE DDL EVENT NOTIFICATION en la base de datos actual.  
  
-   Para crear una notificación de eventos en una instrucción DDL incluida en el ámbito del servidor se requiere, como mínimo, el permiso CREATE DDL EVENT NOTIFICATION en el servidor.  
  
-   Para crear una notificación de eventos en un evento de seguimiento se requiere, como mínimo, el permiso CREATE TRACE EVENT NOTIFICATION en el servidor.  
  
-   Para crear una notificación de eventos en el ámbito de una cola se requiere, como mínimo, el permiso ALTER en la cola.  
  
 Para obtener información acerca del ámbito de las consultas WQL, vea [Usar WQL con el proveedor WMI para eventos de servidor](http://technet.microsoft.com/library/ms180524\(v=sql.105\).aspx).  
  
 Como ejemplo del ámbito, considere una aplicación del proveedor WMI que incluya la siguiente consulta WQL:  
  
```  
SELECT * FROM ALTER_TABLE  
WHERE DatabaseName = "AdventureWorks2012"   
    AND SchemaName = "Person"  
    AND ObjectName = "Person"  
    AND ObjectType = "TABLE";  
```  
  
 El proveedor WMI traduce esta consulta en una notificación de eventos que se crea en la base de datos [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Esto significa que el autor de la llamada debe tener los permisos necesarios para crear este tipo de notificación de eventos, concretamente el permiso CREATE DATABASE DDL EVENT NOTIFICATION en la base de datos [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
 Si una consulta WQL especifica una notificación de eventos que pertenece al nivel del servidor, por ejemplo, emitiendo la consulta SELECT * FROM ALTER_TABLE, la aplicación que realiza la llamada debe tener el permiso CREATE DDL EVENT NOTIFICATION del nivel de servidor. Tenga en cuenta que las notificaciones de eventos con ámbito en el servidor se almacenan en la base de datos maestra. Puede usar el [sys.server_event_notifications](/sql/relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql) vista para ver los metadatos de catálogo.  
  
> [!NOTE]  
>  El ámbito de la notificación de eventos creada por el proveedor WMI (servidor, base de datos u objeto) depende en última instancia del resultado del proceso de comprobación de permisos utilizado por el proveedor WMI. Esto último se ve afectado por el conjunto de permisos del usuario que está llamando al proveedor y por la comprobación de la base de datos que se está consultando.  
>   
>  En el ejemplo anterior, el proveedor intenta crear primero una notificación de eventos limitada al ámbito de la base de datos (`ON DATABASE`). Si el proveedor comprueba que la base de datos existe y que el autor de la llamada dispone de los permisos necesarios para crear una notificación de eventos en la misma, el registro se realizará correctamente. En caso contrario, el proveedor intentará crear una notificación de eventos en el servidor (`ON SERVER`). Suponiendo que este intento sea correcto, todos los eventos `ALTER_TABLE` que se producen en el servidor se envían desde el proceso de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hasta el proceso del servicio WMI. Sin embargo, el proveedor filtra cualquier evento que no se aplique a la base de datos `AdventureWorks` . Aunque este proceso puede aumentar la cantidad de tráfico de red necesaria para el ámbito del evento, este proceso también ofrece la flexibilidad de registrar consultas WQL en las bases de datos antes de que se creen y, a continuación, recibir los datos de eventos una vez creada la base de datos e iniciada la actividad DDL en la misma.  
  
## <a name="permissions-and-message-verification"></a>Permisos y comprobación de mensajes  
 El proveedor WMI no envía mensajes para las notificaciones de eventos si se cumplen las dos condiciones siguientes:  
  
-   El usuario que creó la notificación de eventos a través del proveedor WMI ya no existe en la base de datos o ya no dispone del permiso necesario para crear una notificación de eventos similar.  
  
-   Las notificaciones de eventos se crean en los eventos siguientes:  
  
    -   DROP_LOGIN  
  
    -   ALTER_LOGIN  
  
    -   DROP_USER  
  
    -   ALTER_USER  
  
    -   ADD_ROLE_MEMBER  
  
    -   DROP_ROLE_MEMBER  
  
    -   ADD_SERVER_ROLE_MEMBER  
  
    -   DROP_SERVER_ROLE_MEMBER  
  
    -   DENY o REVOKE (solo se aplica a los permisos ALTER DATABASE, ALTER ANY DATABASE EVENT NOTIFICATION, CREATE DATABASE DDL EVENT NOTIFICATION, CONTROL SERVER, ALTER ANY EVENT NOTIFICATION, CREATE DDL EVENT NOTIFICATION o CREATE TRACE EVENT NOTIFICATION).  
  
## <a name="working-with-event-data-on-the-client-side"></a>Trabajar con datos de eventos en el cliente  
 Una vez que el proveedor WMI para eventos de servidor crea la notificación de eventos necesaria en la base de datos de destino, la notificación de eventos envía datos de eventos para el servicio de destino en msdb denominado **notificaciones/SQL/ProcessWMIEventProviderNotification /V1.0**. El servicio de destino coloca el evento en una cola de `msdb` que se denomina **WMIEventProviderNotificationQueue**. (El proveedor crea dinámicamente tanto el servicio como la cola cuando se conecta por primera vez a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].) A continuación, el proveedor lee los datos de eventos XML de la cola y los convierte al formato de objetos administrados (MOF, Managed Object Format) antes de devolvérselos a la aplicación cliente. Los datos MOF se componen de las propiedades del evento solicitado por la consulta WQL como una definición de clase del Modelo de información común (CIM). Cada propiedad tiene un tipo CIM correspondiente. Por ejemplo, la propiedad `SPID` se devuelve como un tipo CIM `Sint32`. Los tipos CIM de cada propiedad se muestran debajo de cada clase de evento en [proveedor WMI de clases de eventos de servidor y propiedades](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-classes-and-properties.md).  
  
## <a name="see-also"></a>Vea también  
 [Conceptos del proveedor WMI para eventos de servidor](http://technet.microsoft.com/library/ms180560.aspx)  
  
  
