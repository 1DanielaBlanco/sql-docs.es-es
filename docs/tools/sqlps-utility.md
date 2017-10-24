---
title: Utilidad sqlps | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sqlps utility
- PowerShell [SQL Server], sqlps utility
ms.assetid: 4b2515a6-12c3-44fb-b263-1c567681cd2b
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 730d20d8f3accf9a172553fdec5c46aa95530b15
ms.contentlocale: es-es
ms.lasthandoff: 08/02/2017

---
# <a name="sqlps-utility"></a>sqlps, utilidad
  La utilidad **sqlps** inicia una sesión de Windows PowerShell 2.0 con el proveedor de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell y los cmdlets cargados y registrados. Puede escribir scripts o comandos de PowerShell que usen los componentes de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell para trabajar con instancias de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] y sus objetos.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../includes/ssnotedepfutureavoid-md.md)]Use la **sqlps** módulo de PowerShell en su lugar. Para más información acerca del módulo **sqlps** , consulte [Import the SQLPS Module](../relational-databases/scripting/import-the-sqlps-module.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sqlps   
[ [ [ -NoLogo ][ -NoExit ][ -NoProfile ]  
    [ -OutPutFormat { Text | XML } ] [ -InPutFormat { Text | XML } ]  
  ]  
  [ -Command { -  
             | script_block [ -args argument_array ]  
             | string [ command_parameters ]  
             }  
  ]  
]  
[ -? | -Help ]  
```  
  
## <a name="arguments"></a>Argumentos  
 **-NoLogo**  
 Especifica que la utilidad **sqlps** debe ocultar el título de copyright cuando se inicia.  
  
 **-NoExit**  
 Especifica que la utilidad **sqlps** debe seguir ejecutándose después de que los comandos de inicio se hayan completado.  
  
 **-NoProfile**  
 Especifica que la utilidad **sqlps** no debe cargar un perfil de usuario. Los perfiles de usuario registran los alias, funciones y variables de uso frecuente para usarlos en las sesiones de PowerShell.  
  
 **-OutPutFormat** { **Text** | **XML** }  
 Especifica que se dé formato a la salida de la utilidad **sqlps** como cadenas de texto (**Text**) o en un formato CLIXML serializado (**XML**).  
  
 **-InPutFormat** { **Text** | **XML** }  
 Especifica que se dé formato a la entrada de la utilidad **sqlps** como cadenas de texto (**Text**) o en un formato CLIXML serializado (**XML**).  
  
 **-Command**  
 Especifica el comando que debe ejecutar la utilidad **sqlps** . La utilidad **sqlps** ejecuta el comando y luego se cierra, a menos que también se especifique **-NoExit** . No especifique ningún otro modificador después de **-Command**; se leerían como parámetros del comando.  
  
 **-**  
 **-Command-** especifica que la utilidad **sqlps** debe leer la entrada desde la entrada estándar.  
  
 *script_block* [ **-args***argument_array* ]  
 Especifica un bloque de comandos de PowerShell que se han de ejecutar; el bloque debe incluirse entre llaves: {}. *Script_block* solo se puede especificar cuando se llama a la utilidad **sqlps** desde **PowerShell** o desde otra sesión de la utilidad **sqlps** . *argument_array* es una matriz de variables de PowerShell que contiene los argumentos de los comandos de PowerShell en *script_block*.  
  
 *string* [ *command_parameters* ]  
 Especifica una cadena que contiene los comandos de PowerShell que se han de ejecutar. Use el formato **"&{***command***}"**. Las comillas indican una cadena y el operador de invocación (&) hace que la utilidad **sqlps** ejecute el comando.  
  
 [ **-?** | **-Help** ]  
 Muestra el resumen de la sintaxis de las opciones de la utilidad **sqlps** .  
  
## <a name="remarks"></a>Comentarios  
 La utilidad **sqlps** inicia el entorno de PowerShell (PowerShell.exe) y carga el módulo de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell. El módulo, también denominado **sqlps**, carga y registra estos complementos de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell:  
  
-   Microsoft.SqlServer.Management.PSProvider.dll  
  
     Implementa el proveedor de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell y cmdlets asociados como **Encode-SqlName** y **Decode-SqlName**.  
  
-   Microsoft.SqlServer.Management.PSSnapin.dll  
  
     Implementa los cmdlets **Invoke-Sqlcmd** e **Invoke-PolicyEvaluation** .  
  
 Puede usar la utilidad **sqlps** para realizar las tareas siguientes:  
  
-   Ejecutar interactivamente comandos de PowerShell.  
  
-   Ejecutar archivos de script de PowerShell.  
  
-   Ejecutar cmdlets de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
-   Usar las rutas de acceso del proveedor de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] para navegar por la jerarquía de objetos de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 De forma predeterminada, la utilidad **sqlps** se ejecuta con la directiva de ejecución de scripting establecida en **Restricted**. Esto evita la ejecución de cualquier script de PowerShell. Puede usar el cmdlet **Set-ExecutionPolicy** para habilitar la ejecución de scripts firmados o de cualquier script. Ejecute solo scripts de orígenes de confianza y proteja todos los archivos de entrada y salida con los permisos NTFS adecuados. Para obtener más información sobre cómo habilitar los scripts de PowerShell, vea [Running Windows PowerShell Scripts](http://go.microsoft.com/fwlink/?LinkId=103166).  
  
 La versión de la utilidad **sqlps** en [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] y [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] se implementó como un shell mínimo de Windows PowerShell 1.0. Los shells mínimos tienen ciertas restricciones, como no permitir que los usuarios carguen complementos distintos de los que ha cargado el shell mínimo. Estas restricciones no se aplican a la versión [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] y posteriores de la utilidad, que se han cambiado para usar el módulo **sqlps** .  
  
## <a name="examples"></a>Ejemplos  
 **A. Ejecute la utilidad sqlps en de forma predeterminada, el modo interactivo sin la pancarta de copyright**  
  
```  
sqlps -NoLogo  
```  
  
 **B. Ejecutar un script de PowerShell de SQL Server desde la línea de comandos**  
  
```  
sqlps -Command "&{.\MyFolder.MyScript.ps1}"  
```  
  
 **C. Ejecutar un script de PowerShell de SQL Server desde el símbolo del sistema y continuar la ejecución una vez completada la secuencia de comandos**  
  
```  
sqlps -NoExit -Command "&{.\MyFolder.MyScript.ps1}"  
```  
  
## <a name="see-also"></a>Vea también  
 [Habilitar o deshabilitar un protocolo de red de servidor](../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)   
 [SQL Server PowerShell](../relational-databases/scripting/sql-server-powershell.md)  
  
  

