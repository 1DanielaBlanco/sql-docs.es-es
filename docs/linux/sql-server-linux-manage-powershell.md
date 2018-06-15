---
title: Administrar SQL Server en Linux con PowerShell | Documentos de Microsoft
description: Este artículo proporciona información general sobre cómo usar PowerShell en Windows con SQL Server en Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: a3492ce1-5d55-4505-983c-d6da8d1a94ad
ms.openlocfilehash: 54892a66cea7643d708bcd7ba5cf1b6b07d4523f
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2018
ms.locfileid: "34323676"
---
# <a name="use-powershell-on-windows-to-manage-sql-server-on-linux"></a>Usar PowerShell en Windows para administrar SQL Server en Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Este artículo se detallan [SQL Server PowerShell](https://msdn.microsoft.com/en-us/library/mt740629.aspx) y le guía a través de un par de ejemplos sobre cómo usar con SQL Server 2017 en Linux. Compatibilidad con PowerShell para SQL Server está disponible actualmente en Windows, por lo que puede usar cuando tiene una máquina de Windows que se puede conectar a una instancia remota de SQL Server en Linux.

## <a name="install-the-newest-version-of-sql-powershell-on-windows"></a>Instale la versión más reciente de PowerShell de SQL en Windows

[PowerShell de SQL](https://msdn.microsoft.com/en-us/library/mt740629.aspx) en Windows se incluye con [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md). Al trabajar con SQL Server, debe utilizar siempre la versión más reciente de SSMS y PowerShell de SQL. La versión más reciente de SSMS se actualiza continuamente y optimizado y funciona con SQL Server actualmente Linux de 2017. Para descargar e instalar la versión más reciente, consulte [descargar SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md). Para mantenerse al día, la versión más reciente de SSMS le avisa cuando hay una nueva versión disponible para su descarga.

## <a name="before-you-begin"></a>Antes de empezar

Leer la [problemas conocidos](sql-server-linux-release-notes.md) para SQL Server de 2017 en Linux.

## <a name="launch-powershell-and-import-the-sqlserver-module"></a>Inicie PowerShell e importe la *sqlserver* módulo

Empecemos por iniciar PowerShell en Windows. Abra un *símbolo* en el equipo de Windows y escribir **PowerShell** para iniciar una nueva sesión de Windows PowerShell.

```
PowerShell
```

SQL Server proporciona un módulo de Windows PowerShell denominado **SqlServer** que puede usar para importar los componentes de SQL Server (proveedor de SQL Server y los cmdlets) en un entorno de PowerShell o la secuencia de comandos.

Copie y pegue el siguiente comando en el símbolo del sistema de PowerShell para importar la **SqlServer** módulo en la sesión actual de PowerShell:

```powershell
Import-Module SqlServer
```

Escriba el comando siguiente en el símbolo del sistema de PowerShell para comprobar que la **SqlServer** módulo se importó correctamente:

```powershell
Get-Module -Name SqlServer
```

PowerShell debería mostrar información similar a la siguiente salida:

```
ModuleType Version    Name          ExportedCommands
---------- -------    ----          ----------------
Script     0.0        SqlServer
Manifest   20.0       SqlServer     {Add-SqlAvailabilityDatabase, Add-SqlAvailabilityGroupList...
```

## <a name="connect-to-sql-server-and-get-server-information"></a>Conectarse a SQL Server y obtener información del servidor

Vamos a usar PowerShell en Windows para conectarse a la instancia de SQL Server 2017 en Linux y mostrar un par de propiedades del servidor.

Copie y pegue los siguientes comandos en el símbolo del sistema de PowerShell. Al ejecutar estos comandos, PowerShell hará lo siguiente:
- Mostrar la *solicitud de credenciales de Windows PowerShell* cuadro de diálogo que le pide las credenciales (*nombre de usuario SQL* y *contraseña SQL*) para conectarse a su servidor de SQL 2017 instancia en Linux
- Cargar el ensamblado de objetos de administración de SQL Server (SMO)
- Cree una instancia de la [Server](https://msdn.microsoft.com/en-us/library/microsoft.sqlserver.management.smo.server.aspx) objeto
- Conectarse a la **Server** y mostrar una serie de propiedades

No olvide reemplazar **\<your_server_instance\>** con la dirección IP o el nombre de host de la instancia de SQL Server 2017 en Linux.

```powershell
# Prompt for credentials to login into SQL Server
$serverInstance = "<your_server_instance>"
$credential = Get-Credential

# Load the SMO assembly and create a Server object
[System.Reflection.Assembly]::LoadWithPartialName('Microsoft.SqlServer.SMO') | out-null
$server = New-Object ('Microsoft.SqlServer.Management.Smo.Server') $serverInstance

# Set credentials
$server.ConnectionContext.LoginSecure=$false
$server.ConnectionContext.set_Login($credential.UserName)
$server.ConnectionContext.set_SecurePassword($credential.Password)

# Connect to the Server and get a few properties
$server.Information | Select-Object Edition, HostPlatform, HostDistribution | Format-List
# done
```

PowerShell debería mostrar información similar a la siguiente salida:

```
Edition          : Developer Edition (64-bit)
HostPlatform     : Linux
HostDistribution : Ubuntu
```
> [!NOTE]
> Si no se mostrará estos valores, probablemente error en la conexión a la instancia de SQL Server de destino. Asegúrese de que puede usar la misma información de conexión para conectarse desde SQL Server Management Studio. Luego revise las [recomendaciones para solucionar problemas de conexión](sql-server-linux-troubleshooting-guide.md#connection).

## <a name="examine-sql-server-error-logs"></a>Examine los registros de errores de SQL Server

Vamos a usar PowerShell en Windows para examinar los registros de errores de connect en la instancia de SQL Server 2017 en Linux. También se usará el **Out-GridView** cmdlet para mostrar información del error se registra en una visualización de la vista de cuadrícula.

Copie y pegue los siguientes comandos en el símbolo del sistema de PowerShell. Pueden tardar unos minutos en ejecutarse. Estos comandos hacer lo siguiente:
- Mostrar la *solicitud de credenciales de Windows PowerShell* cuadro de diálogo que le pide las credenciales (*nombre de usuario SQL* y *contraseña SQL*) para conectarse a su servidor de SQL 2017 instancia en Linux
- Use la **Get SqlErrorLog** para conectarse a la instancia de SQL Server 2017 en Linux y recuperar el error se registra desde **ayer**
- Canalizar la salida del **Out-GridView** cmdlet

No olvide reemplazar **\<your_server_instance\>** con la dirección IP o el nombre de host de la instancia de SQL Server 2017 en Linux.

```powershell
# Prompt for credentials to login into SQL Server
$serverInstance = "<your_server_instance>"
$credential = Get-Credential

# Retrieve error logs since yesterday
Get-SqlErrorLog -ServerInstance $serverInstance -Credential $credential -Since Yesterday | Out-GridView
# done
```
## <a name="see-also"></a>Vea también
- [SQL Server PowerShell](../relational-databases/scripting/sql-server-powershell.md)
