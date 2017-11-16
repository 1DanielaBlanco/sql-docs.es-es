---
title: Obtener ayuda de SQL Server PowerShell | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help [PowerShell]
- Help [SQL Server], PowerShell
- PowerShell [SQL Server], help
ms.assetid: 968c316d-db83-4c24-8ea6-9f18736842f7
caps.latest.revision: "18"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d0a1c7d0f50f672bedd2f3c4d375bfef983f7a5e
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="get-help-sql-server-powershell"></a>Obtener ayuda de SQL Server PowerShell
  Hay varios orígenes de información sobre cómo utilizar los cmdlets y el proveedor de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para Windows PowerShell. Esto incluye la ayuda que está disponible en el entorno de Windows PowerShell.  
  
## <a name="before-you-begin"></a>Antes de comenzar  
 Para obtener información sobre Windows PowerShell, vea el [Guía de Introducción de Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=217083).  
  
 Para ver una introducción a los cmdlets y el proveedor de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vea [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md).  
  
### <a name="help-in-the-windows-powershell-environment"></a>Ayuda en el entorno de Windows PowerShell  
 Use el cmdlet **Get-Help** para obtener ayuda en el entorno de Windows PowerShell. **Get-Help** proporciona ayuda básica para el lenguaje de Windows PowerShell y los diversos cmdlets y proveedores disponibles en Windows PowerShell.  
  
 Para obtener más información sobre las formas en que puede usar **Get-Help**, vea [Obtener Ayuda: Get-Help](http://go.microsoft.com/fwlink/?LinkId=102136).  
  
### <a name="sql-server-powershell-provider-help"></a>Ayuda del proveedor de SQL Server PowerShell  
 El proveedor de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell implementa varias carpetas en una unidad virtual de SQLSERVER, como el SQLSERVER: \ SQL y SQLSERVER: \ Carpetas de DAC. Cada carpeta está asociada con uno de los modelos de objetos de administración de SQL Server. Aunque puede mostrar los métodos y propiedades asociados con cada nodo en una ruta de acceso de SQL Server, no puede obtener ayuda para ellos en el entorno de PowerShell. Para una tabla de carpetas con vínculos a referencia de programación asociada, vea [SQL Server PowerShell Provider](../../relational-databases/scripting/sql-server-powershell-provider.md).  
  
### <a name="invoke-sqlcmd-help"></a>Ayuda de Invoke-Sqlcmd  
 El cmdlet **Invoke-Sqlcmd** toma como entrada cualquier archivo de script o consulta que la utilidad **sqlcmd** pueda ejecutar. Puede usar **Get-Help** para obtener información sobre **Invoke-Sqlcmd** y sus parámetros, pero no hay ninguna cobertura de **Get-Help** para las consultas **sqlcmd** .  
  
 La entrada *-Query* o *-QueryFromFile* puede contener:  
  
-   Variables y comandos de**sqlcmd** . Para obtener información sobre estas variables y comandos, consulte la sección Comentarios de [sqlcmd Utility](../../tools/sqlcmd-utility.md).  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] . Para obtener más información sobre el idioma [!INCLUDE[tsql](../../includes/tsql-md.md)], vea [Referencia de Transact-SQL &#40;motor de base de datos&#41;](../../t-sql/transact-sql-reference-database-engine.md).  
  
-   Instrucciones XQuery. Para obtener más información sobre lenguaje XQuery admitido por [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vea [Referencia del lenguaje XQuery &#40;SQL Server&#41;](../../xquery/xquery-language-reference-sql-server.md).  
  
## <a name="get-help-for-a-sql-server-cmdlet"></a>Obtener ayuda para un cmdlet de SQL Server.  
 **Para obtener ayuda para un cmdlet**  
  
-   Ejecute Get-Help especificando el nombre del cmdlet y el nivel de ayuda que se va a devolver.  
  
### <a name="example-cmdlet-get-help"></a>Ejemplo: Get-Help de cmdlet  
 Los siguientes ejemplos devuelven diferentes niveles de ayuda para **Invoke-Sqlcmd**:  
  
```  
## Get the basic help.  
Get-Help Invoke-Sqlcmd  
  
## Get the full help.  
Get-Help Invoke-Sqlcmd –Full  
  
## Get the parameter descriptions.  
Get-Help Invoke-Sqlcmd -Parameter *  
  
## Get the code examples.  
Get-Help Invoke-Sqlcmd –Examples  
  
## Get the syntax diagram.  
Get-Help Invoke-Sqlcmd –Syntax  
```  
  
## <a name="get-a-list-of-providers"></a>Obtener una lista de proveedores  
 **Para obtener una lista de proveedores activo**  
  
1.  Ejecute Get-Help ejecutando la categoría del proveedor.  
  
 Para obtener más información sobre cómo obtener ayuda del proveedor en Windows PowerShell, vea [Unidades y proveedores](http://go.microsoft.com/fwlink/?LinkId=102137).  
  
### <a name="example-get-a-list-of-providers"></a>Ejemplo: Obtener una lista de proveedores  
 Este código devuelve una lista de los proveedores habilitados actualmente en la sesión de Windows PowerShell:  
  
```  
Get-Help -Category provider  
```  
  
## <a name="get-help-about-the-sql-server-provider"></a>Obtener ayuda acerca del proveedor de SQL Server  
 **Para obtener ayuda acerca del proveedor**  
  
1.  Ejecute Get-Help especificando el nombre SQLServer  
  
### <a name="example-get-sql-server-provider-help"></a>Ejemplo: Obtener Ayuda del proveedor de SQL Server  
 Este ejemplo devuelve información básica sobre el proveedor de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
```  
Get-Help SQLServer  
```  
  
## <a name="list-methods-and-properties"></a>Enumerar métodos y propiedades  
 **Para mostrar los métodos y propiedades para un nodo en una ruta de acceso del proveedor de SQL Server**  
  
1.  Un CD de un nodo de la ruta de acceso de SQL Server, o crear una variable establecida en esa ubicación.  
  
2.  Ejecute el cmdlet **Get-Member** con el parámetro –Type establecido en métodos o propiedades.  
  
### <a name="examples-listing-methods-and-properties"></a>Ejemplos: Enumerar métodos y propiedades  
 En este ejemplo se enumeran los métodos admitidos para el nodo de bases de datos:  
  
```  
Set-Location SQL:\MyComputer\DEFAULT\Databases  
Get-Item . | Get-Member -Type Methods  
```  
  
 Este ejemplo enumera las propiedades de una variable que se ha establecido en un objeto SMO Table:  
  
```  
$MyVar = New-Object Microsoft.SqlServer.Management.SMO.Table  
$MyVar | Get-Member -Type Properties  
```  
  
## <a name="see-also"></a>Vea también  
 [SQL Server PowerShell Provider](../../relational-databases/scripting/sql-server-powershell-provider.md)   
 [Utilizar los cmdlets del motor de base de datos](../../relational-databases/scripting/use-the-database-engine-cmdlets.md)  
  
  
