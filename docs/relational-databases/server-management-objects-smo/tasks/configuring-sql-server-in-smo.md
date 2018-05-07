---
title: Configurar SQL Server en SMO | Documentos de Microsoft
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: smo
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server, configuring
- configuration options [SMO]
ms.assetid: 0a372643-15cb-45a7-8665-04f1215df8ed
caps.latest.revision: 42
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: ba4bdac08ce71e5acba76821daf8551c66535c2b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="configuring-sql-server-in-smo"></a>Configurar SQL Server en SMO
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  En SMO, el <xref:Microsoft.SqlServer.Management.Smo.Information> objeto, el <xref:Microsoft.SqlServer.Management.Smo.Settings> objeto, el <xref:Microsoft.SqlServer.Management.Smo.UserOptions> objeto y el <xref:Microsoft.SqlServer.Management.Smo.Configuration> objeto contienen valores y la información de la instancia de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tiene numerosas propiedades que describen el comportamiento de la instancia instalada. Las propiedades describen las opciones de inicio, los valores predeterminados, archivos y directorios del servidor, la información del procesador y del sistema, el producto y las versiones, la información de conexión, las opciones de memoria, la selección del idioma y de intercalación y el modo de autenticación.  
  
## <a name="sql-server-configuration"></a>Configurar SQL Server  
 El <xref:Microsoft.SqlServer.Management.Smo.Information> propiedades de los objetos contienen información acerca de la instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], por ejemplo, el procesador y la plataforma.  
  
 El <xref:Microsoft.SqlServer.Management.Smo.Settings> propiedades de los objetos contienen información acerca de la instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Se pueden modificar el archivo y directorio predeterminados de la base de datos además del perfil de correo y la cuenta del servidor. Estas propiedades permanecen para la duración de la conexión.  
  
 Las propiedades del objeto <xref:Microsoft.SqlServer.Management.Smo.UserOptions> contienen información sobre el comportamiento de las conexiones actuales relacionado con la aritmética, los estándares ANSI y las transacciones.  
  
 Hay también un conjunto de opciones de configuración que se representa mediante el <xref:Microsoft.SqlServer.Management.Smo.Configuration> objeto. Contiene un conjunto de propiedades que representan las opciones que pueden ser modificadas por el procedimiento almacenado **sp_configure** . Opciones tales como **Priority Boost**, **Recovery Interval** y **Network Packet Size**controlan el rendimiento de la instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Se pueden cambiar muchas de estas opciones dinámicamente, pero en algunos casos el valor se configura primero y a continuación se cambia cuando se reinicia la instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Hay un <xref:Microsoft.SqlServer.Management.Smo.Configuration> propiedad para cada opción de configuración de objeto. Con el objeto <xref:Microsoft.SqlServer.Management.Smo.ConfigProperty> puede modificar la configuración global. Muchas propiedades tienen valores máximos y mínimos que también se almacenan como propiedades de <xref:Microsoft.SqlServer.Management.Smo.ConfigProperty>. Estas propiedades requieren la <xref:Microsoft.SqlServer.Management.Smo.ConfigurationBase.Alter%2A> método para confirmar el cambio a la instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Todas las opciones de configuración en el <xref:Microsoft.SqlServer.Management.Smo.Configuration> objeto debe cambiarse por el administrador del sistema.  
  
## <a name="examples"></a>Ejemplos  
 Para los siguientes ejemplos de código, deberá seleccionar el entorno de programación, la plantilla de programación y el lenguaje de programación en los que crear su aplicación. Para obtener más información, consulte [crear a Visual C&#35; proyecto SMO en Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="modifying-sql-server-configuration-options-in-visual-basic"></a>Modificar las opciones de configuración de SQL Server en Visual Basic  
 En el ejemplo de código se muestra cómo actualizar una opción de configuración en Visual Basic .NET. También recupera y muestra información sobre los valores máximos y mínimos para la opción de configuración especificada. Por último, el programa notifica al usuario si el cambio se ha realizado dinámicamente o si se almacena hasta que la instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] se reinicia.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Display all the configuration options.
Dim p As ConfigProperty
For Each p In srv.Configuration.Properties
    Console.WriteLine(p.DisplayName)
Next
Console.WriteLine("There are " & srv.Configuration.Properties.Count.ToString & " configuration options.")
'Display the maximum and minimum values for ShowAdvancedOptions.
Dim min As Integer
Dim max As Integer
min = srv.Configuration.ShowAdvancedOptions.Minimum
max = srv.Configuration.ShowAdvancedOptions.Maximum
Console.WriteLine("Minimum and Maximum values are " & min & " and " & max & ".")
'Modify the value of ShowAdvancedOptions and run the Alter method.
srv.Configuration.ShowAdvancedOptions.ConfigValue = 0
srv.Configuration.Alter()
'Display when the change takes place according to the IsDynamic property.
If srv.Configuration.ShowAdvancedOptions.IsDynamic = True Then
    Console.WriteLine("Configuration option has been updated.")
Else
    Console.WriteLine("Configuration option will be updated when SQL Server is restarted.")
End If
``` 
  
## <a name="modifying-sql-server-settings-in-visual-basic"></a>Modificar la configuración de SQL Server en Visual Basic  
 El ejemplo de código muestra información sobre la instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en <xref:Microsoft.SqlServer.Management.Smo.Information> y <xref:Microsoft.SqlServer.Management.Smo.Settings>y modifica la configuración de <xref:Microsoft.SqlServer.Management.Smo.Settings> y <xref:Microsoft.SqlServer.Management.Smo.UserOptions>propiedades del objeto.  
  
 En el ejemplo el objeto <xref:Microsoft.SqlServer.Management.Smo.UserOptions> y el objeto <xref:Microsoft.SqlServer.Management.Smo.Settings> tienen un método <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A>. Puede ejecutar el <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> métodos para estos individualmente.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Display information about the instance of SQL Server in Information and Settings.
Console.WriteLine("OS Version = " & srv.Information.OSVersion)
Console.WriteLine("State = " & srv.Settings.State.ToString)
'Display information specific to the current user in UserOptions.
Console.WriteLine("Quoted Identifier support = " & srv.UserOptions.QuotedIdentifier)
'Modify server settings in Settings.

srv.Settings.LoginMode = ServerLoginMode.Integrated
'Modify settings specific to the current connection in UserOptions.
srv.UserOptions.AbortOnArithmeticErrors = True
'Run the Alter method to make the changes on the instance of SQL Server.
srv.Alter()
```
  
## <a name="modifying-sql-server-settings-in-visual-c"></a>Modificar la configuración de SQL Server en Visual C#  
 El ejemplo de código muestra información sobre la instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en <xref:Microsoft.SqlServer.Management.Smo.Information> y <xref:Microsoft.SqlServer.Management.Smo.Settings>y modifica la configuración de <xref:Microsoft.SqlServer.Management.Smo.Settings> y <xref:Microsoft.SqlServer.Management.Smo.UserOptions>propiedades del objeto.  
  
 En el ejemplo el objeto <xref:Microsoft.SqlServer.Management.Smo.UserOptions> y el objeto <xref:Microsoft.SqlServer.Management.Smo.Settings> tienen un método <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A>. Puede ejecutar el <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> métodos para estos individualmente.  
  
 `//Connect to the local, default instance of SQL Server.`  
  
```csharp  
{  
            Server srv = new Server();  
            //Display all the configuration options.   
  
            foreach (ConfigProperty p in srv.Configuration.Properties)  
            {  
                Console.WriteLine(p.DisplayName);  
            }  
            Console.WriteLine("There are " + srv.Configuration.Properties.Count.ToString() + " configuration options.");  
            //Display the maximum and minimum values for ShowAdvancedOptions.   
            int min = 0;  
            int max = 0;  
            min = srv.Configuration.ShowAdvancedOptions.Minimum;  
            max = srv.Configuration.ShowAdvancedOptions.Maximum;  
            Console.WriteLine("Minimum and Maximum values are " + min + " and " + max + ".");  
            //Modify the value of ShowAdvancedOptions and run the Alter method.   
            srv.Configuration.ShowAdvancedOptions.ConfigValue = 0;  
            srv.Configuration.Alter();  
            //Display when the change takes place according to the IsDynamic property.   
            if (srv.Configuration.ShowAdvancedOptions.IsDynamic == true)  
            {  
                Console.WriteLine("Configuration option has been updated.");  
            }  
            else  
            {  
                Console.WriteLine("Configuration option will be updated when SQL Server is restarted.");  
            }  
        }  
```  
  
## <a name="modifying-sql-server-settings-in-powershell"></a>Modificar la configuración de SQL Server en PowerShell  
 El ejemplo de código muestra información sobre la instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en <xref:Microsoft.SqlServer.Management.Smo.Information> y <xref:Microsoft.SqlServer.Management.Smo.Settings>y modifica la configuración de <xref:Microsoft.SqlServer.Management.Smo.Settings> y <xref:Microsoft.SqlServer.Management.Smo.UserOptions>propiedades del objeto.  
  
 En el ejemplo el objeto <xref:Microsoft.SqlServer.Management.Smo.UserOptions> y el objeto <xref:Microsoft.SqlServer.Management.Smo.Settings> tienen un método <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A>. Puede ejecutar el <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> métodos para estos individualmente.  
  
```powershell 
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\  
$srv = get-item default  
  
#Display information about the instance of SQL Server in Information and Settings.  
"OS Version = " + $srv.Information.OSVersion  
"State = "+ $srv.Settings.State.ToString()  
  
#Display information specific to the current user in UserOptions.  
"Quoted Identifier support = " + $srv.UserOptions.QuotedIdentifier  
  
#Modify server settings in Settings.  
$srv.Settings.LoginMode = [Microsoft.SqlServer.Management.SMO.ServerLoginMode]::Integrated  
  
#Modify settings specific to the current connection in UserOptions.  
$srv.UserOptions.AbortOnArithmeticErrors = $true  
  
#Run the Alter method to make the changes on the instance of SQL Server.  
$srv.Alter()  
```  
  
## <a name="modifying-sql-server-configuration-options-in-powershell"></a>Modificar las opciones de configuración de SQL Server en PowerShell  
 En el ejemplo de código se muestra cómo actualizar una opción de configuración en Visual Basic .NET. También recupera y muestra información sobre los valores máximos y mínimos para la opción de configuración especificada. Por último, el programa notifica al usuario si el cambio se ha realizado dinámicamente o si se almacena hasta que la instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] se reinicia.  
  
```powershell 
#Get a server object which corresponds to the default instance replace LocalMachine with the physical server  
cd \sql\LocalMachine  
$svr = get-item default  
  
#enumerate its properties  
foreach ($Item in $Svr.Configuration.Properties)   
{  
 $Item.DisplayName  
}  
  
"There are " + $svr.Configuration.Properties.Count.ToString() + " configuration options."  
  
#Display the maximum and minimum values for ShowAdvancedOptions.  
$min = $svr.Configuration.ShowAdvancedOptions.Minimum  
$max = $svr.Configuration.ShowAdvancedOptions.Maximum  
"Minimum and Maximum values are " + $min.ToString() + " and " + $max.ToString() + "."  
  
#Modify the value of ShowAdvancedOptions and run the Alter method.  
$svr.Configuration.ShowAdvancedOptions.ConfigValue = 0  
$svr.Configuration.Alter()  
  
#Display when the change takes place according to the IsDynamic property.  
If ($svr.Configuration.ShowAdvancedOptions.IsDynamic -eq $true)  
 {    
   "Configuration option has been updated."  
 }  
Else  
{  
    "Configuration option will be updated when SQL Server is restarted."  
}  
```  
  
  
