---
title: Creación de la dirección URL de conexión | Documentos de Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 44996746-d373-4f59-9863-a8a20bb8024a
caps.latest.revision: 53
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c36793a50692a122dbd045dba9deae03d35014a8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="building-the-connection-url"></a>Generar URL de conexión
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  El formato general de la URL de conexión es  
  
 `jdbc:sqlserver://[serverName[\instanceName][:portNumber]][;property=value[;property=value]]`  
  
 donde:  
  
-   **SQLServer: / /** (obligatorio) se conoce como el subprotocolo y es constante.  
  
-   **serverName** (opcional) es la dirección del servidor al que conectarse. Puede ser un DNS o una dirección IP o bien un host local o 127.0.0.1 para el equipo local. Si no se especifica en la URL de conexión, es necesario especificar el nombre del servidor en la colección de propiedades.  
  
-   **instanceName** (opcional) es la instancia para la conexión con serverName. Si no se especifica, se establece una conexión con la instancia predeterminada.  
  
-   **portNumber** (opcional) es el puerto de conexión con serverName. El valor predeterminado es 1433. Si usa el valor predeterminado, no es necesario especificar el puerto ni el signo ":" precedente en la dirección URL.  
  
    > [!NOTE]  
    >  Para obtener un rendimiento óptimo de la conexión, debe establecer portNumber al conectar con una instancia con nombre. De este modo se evita un ciclo de ida y vuelta en el servidor para determinar el número de puerto. Si se usan portNumber e instanceName, portNumber tiene prioridad e instanceName se omite.  
  
-   **propiedad** (opcional) es una o más propiedades de conexión de opción. Para obtener más información, consulte [estableciendo las propiedades de conexión](../../connect/jdbc/setting-the-connection-properties.md). Se puede especificar cualquier propiedad de la lista. Las propiedades solo se pueden delimitar mediante punto y coma (";") y no se pueden duplicar.  
  
> [!CAUTION]  
>  Por motivos de seguridad, debe evitar la generación de direcciones URL de conexión basadas en la entrada del usuario. Debe especificar solo el nombre del servidor y el controlador de la URL. Para los valores de nombre y contraseña, utilice las colecciones de propiedades de conexión. Para obtener más información acerca de la seguridad en las aplicaciones JDBC, consulte [proteger aplicaciones del controlador JDBC](../../connect/jdbc/securing-jdbc-driver-applications.md).  
  
## <a name="connection-examples"></a>Ejemplos de conexión  
 Conexión a la base de datos predeterminada del equipo local con un nombre de usuario y una contraseña:  
  
 `jdbc:sqlserver://localhost;user=MyUserName;password=*****;`  
  
> [!NOTE]  
>  Aunque en el ejemplo anterior se usan un nombre de usuario y una contraseña en la cadena de conexión, debe usar la seguridad integrada dado que resulta más seguro. Para obtener más información, consulte el [conectarse con la autenticación integrada](#Connectingintegrated) sección más adelante en este tema.  
  
 La cadena de conexión siguiente muestra un ejemplo de cómo conectarse a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] base de datos mediante la autenticación integrada y Kerberos desde una aplicación que se ejecuta en cualquier sistema operativo compatible con la [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]:  
  
```  
jdbc:sqlserver://;servername=server_name;integratedSecurity=true;authenticationScheme=JavaKerberos  
```  
  
 Conexión con la base de datos predeterminada del equipo local con autenticación integrada:  
  
 `jdbc:sqlserver://localhost;integratedSecurity=true;`  
  
 Conexión a la base de datos con nombre de un servidor remoto:  
  
 `jdbc:sqlserver://localhost;databaseName=AdventureWorks;integratedSecurity=true;`  
  
 Conexión en el puerto predeterminado con el servidor remoto:  
  
 `jdbc:sqlserver://localhost:1433;databaseName=AdventureWorks;integratedSecurity=true;`  
  
 Conectar mediante la especificación de un nombre de aplicación personalizada:  
  
 `jdbc:sqlserver://localhost;databaseName=AdventureWorks;integratedSecurity=true;applicationName=MyApp;`  
  
## <a name="named-and-multiple-sql-server-instances"></a>Instancias de SQL Server múltiples y con nombre  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] permite la instalación de varias instancias de base de datos por servidor. Cada instancia se identifica con un nombre concreto. Para conectarse a una instancia con nombre de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], puede especificar el número de puerto de la instancia con nombre (opción preferida) o puede especificar el nombre de instancia como una propiedad de dirección URL de JDBC o **datasource** propiedad. Si no se especifica ningún nombre de instancia o propiedad de número de puerto, se crea una conexión a la instancia predeterminada. Vea los ejemplos siguientes:  
  
 Para usar un número de puerto, haga lo siguiente:  
  
 `jdbc:sqlserver://localhost:1433;integratedSecurity=true;<more properties as required>;`  
  
 Para usar una propiedad URL de JDBC, haga lo siguiente:  
  
 `jdbc:sqlserver://localhost;instanceName=instance1;integratedSecurity=true;<more properties as required>;`  
  
## <a name="escaping-values-in-the-connection-url"></a>Escape de valores en la URL de conexión  
 Puede que tenga que aplicar un escape a determinadas partes de los valores URL de conexión debido a la inclusión de caracteres especiales como espacios, puntos y comas, y comillas. El controlador JDBC admite el escape de estos caracteres si se incluyen entre llaves. Por ejemplo, {;} aplica el escape al punto y coma.  
  
 Los valores de escape pueden contener caracteres especiales (sobre todo "=", ";", "[]'" y espacio), pero no pueden contener llaves. Los valores a los que se debe aplicar el escape y contengan llaves se deben agregar a la colección de propiedades.  
  
> [!NOTE]  
>  El espacio en blanco dentro de las llaves es literal y no se reduce.  
  
##  <a name="Connectingintegrated"></a> Conectar con la autenticación integrada en Windows  
 El controlador JDBC admite el uso de la autenticación integrada de tipo 2 en los sistemas operativos Windows mediante la propiedad de cadena de conexión integratedSecurity. Para usar la autenticación integrada, copie el archivo sqljdbc_auth.dll en un directorio de la ruta del sistema de Windows en que esté instalado el controlador JDBC.  
  
 Los archivos sqljdbc_auth.dll se instalan en la siguiente ubicación:  
  
 \<*directorio de instalación de*> \sqljdbc_\<*versión*>\\<*lenguaje*> \auth\  
  
 Para cualquier sistema operativo compatible con la [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], consulte [utilizando la autenticación integrada Kerberos para conectarse a SQL Server](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md) para obtener una descripción de una característica agregada en [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] que permite que una aplicación para conectarse a un base de datos mediante la autenticación integrada con Kerberos de tipo 4.  
  
> [!NOTE]  
>  Si está ejecutando una máquina virtual Java de (JVM, Java Virtual Machine) 32 bits, utilice el archivo sqljdbc_auth.dll en la carpeta x86, aun cuando la versión del sistema operativo sea la x64. Si está ejecutando una JVM de 64 bits en un procesador x64, utilice el archivo sqljdbc_auth.dll de la carpeta x64.  
  
 Alternativamente, puede especificar la propiedad del sistema java.libary.path para especificar el directorio de sqljdbc_auth.dll. Por ejemplo, si el controlador JDBC está instalado en el directorio predeterminado, puede especificar la ubicación de la DLL con el siguiente argumento de máquina virtual (VM) si la aplicación de Java se ha iniciado:  
  
 `-Djava.library.path=C:\Microsoft JDBC Driver 6.4 for SQL Server\sqljdbc_<version>\enu\auth\x86`  
  
## <a name="connecting-with-ipv6-addresses"></a>Conectar con direcciones IPv6  
 El controlador JDBC admite el uso de direcciones IPv6 con la colección de propiedades de conexión y con la propiedad de cadena de conexión serverName. El valor serverName inicial, como jdbc:*sqlserver*://*serverName*, no se admite para las direcciones IPv6 en las cadenas de conexión. Use un nombre para *serverName* en lugar de un IPv6 sin formato dirección funcionará en todos los casos en la conexión. En los siguientes ejemplos se proporciona más información.  
  
 **Para usar la propiedad serverName**  
  
 `jdbc:sqlserver://;serverName=3ffe:8311:eeee:f70f:0:5eae:10.203.31.9\\instance1;integratedSecurity=true;`  
  
 **Utilice la colección de propiedades**  
  
 `Properties pro = new Properties();`  
  
 `pro.setProperty("serverName", "serverName=3ffe:8311:eeee:f70f:0:5eae:10.203.31.9\\instance1");`  
  
 `Connection con = DriverManager.getConnection("jdbc:sqlserver://;integratedSecurity=true;", pro);`  
  
## <a name="see-also"></a>Vea también  
 [Conexión a SQL Server con el controlador JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  
