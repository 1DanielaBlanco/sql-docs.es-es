---
title: Crear un paquete mediante programación | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SSIS packages, creating
- Integration Services packages, creating
- packages [Integration Services], creating
- SQL Server Integration Services packages, creating
ms.assetid: e44bcc70-32d3-43e8-a84b-29aef819d5d3
caps.latest.revision: 51
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 691f5c3cc96f1963116839dcaa846dbda4eae2fb
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35313064"
---
# <a name="creating-a-package-programmatically"></a>Crear un paquete mediante programación
  El objeto <xref:Microsoft.SqlServer.Dts.Runtime.Package> es el contenedor de nivel superior para todos los demás objetos de una solución de proyecto [!INCLUDE[ssIS](../../includes/ssis-md.md)]. Al igual que el contenedor de nivel superior, el paquete es el primer objeto creado y los objetos subsiguientes se agregan a él y, a continuación, se ejecutan dentro del contexto del paquete. El propio paquete no mueve o transforma los datos. El paquete se basa en las tareas que contiene para realizar el trabajo. Las tareas realizan la mayor parte del trabajo que realiza un paquete y definen la funcionalidad de un paquete. Un paquete se crea y ejecuta con solo tres líneas de código, pero se agregan varias tareas y los objetos <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> para proporcionar una funcionalidad adicional al paquete. En esta sección se describe cómo crear un paquete mediante programación. No proporciona información acerca de cómo crear las tareas o <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>. Estos temas se tratan en secciones posteriores.  
  
## <a name="example"></a>Ejemplo  
 Para escribir código mediante el IDE de Visual Studio, se exige una referencia a Microsoft.SqlServer.ManagedDTS.DLL para crear una instrucción `using` (`Imports` en Visual Basic .NET) a Microsoft.SqlServer.Dts.Runtime. En el ejemplo de código siguiente se muestra cómo crear un paquete vacío.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package package;  
      package = new Package();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim package As Package  
    package = New Package  
  
  End Sub  
  
End Module  
```  
  
 Para compilar y ejecutar el ejemplo, presione F5 en Visual Studio. Para compilar el código mediante el compilador de C#, **csc.exe**, en el símbolo del sistema que se debe compilar, use las siguientes referencias de comando y archivo, reemplazando *\<filename>* por el nombre del archivo .cs o .vb y proporcionando el nombre *\<outputfilename>* que elija.  
  
 **csc /target:library /out: \<outputfilename>.dll \<filename>.cs /r:Microsoft.SqlServer.Managed DTS.dll" /r:System.dll**  
  
 Para compilar el código mediante el compilador de Visual Basic .NET, **vbc.exe**, en el símbolo del sistema que se debe compilar, use las siguientes referencias de comando y archivo.  
  
 **vbc /target:library /out: \<outputfilename>.dll \<filename>.vb /r:Microsoft.SqlServer.Managed DTS.dll" /r:System.dll**  
  
 También puede crear un paquete cargando un paquete existente que se guardó en disco, en el sistema de archivos o en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La diferencia es que primero se crea el objeto <xref:Microsoft.SqlServer.Dts.Runtime.Application> y, después, uno de los métodos sobrecargados de la aplicación rellena el objeto de paquete: **LoadPackage** para archivos planos, **LoadFromSQLServer** para archivos guardados en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromDtsServer%2A> para los paquetes guardados en el sistema de archivos. En el ejemplo siguiente se carga un paquete existente desde el disco y, a continuación, se muestran varias propiedades en el paquete.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class ApplicationTests  
  {  
    static void Main(string[] args)  
    {  
      // The variable pkg points to the location of the  
      // ExecuteProcess package sample that was installed with  
      // the SSIS samples.  
      string pkg = @"C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" +  
        @"\Package Samples\ExecuteProcess Sample\ExecuteProcess\UsingExecuteProcess.dtsx";  
  
      Application app = new Application();  
      Package p = app.LoadPackage(pkg, null);  
  
      // Now that the package is loaded, we can query on  
      // its properties.  
      int n = p.Configurations.Count;  
      DtsProperty p2 = p.Properties["VersionGUID"];  
      DTSProtectionLevel pl = p.ProtectionLevel;  
  
      Console.WriteLine("Number of configurations = " + n.ToString());  
      Console.WriteLine("VersionGUID = " + (string)p2.GetValue(p));  
      Console.WriteLine("ProtectionLevel = " + pl.ToString());  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module ApplicationTests  
  
  Sub Main()  
  
    ' The variable pkg points to the location of the  
    ' ExecuteProcess package sample that was installed with  
    ' the SSIS samples.  
    Dim pkg As String = _  
      "C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" & _  
      "\Package Samples\ExecuteProcess Sample\ExecuteProcess\UsingExecuteProcess.dtsx"  
  
    Dim app As Application = New Application()  
    Dim p As Package = app.LoadPackage(pkg, Nothing)  
  
    ' Now that the package is loaded, we can query on  
    ' its properties.  
    Dim n As Integer = p.Configurations.Count  
    Dim p2 As DtsProperty = p.Properties("VersionGUID")  
    Dim pl As DTSProtectionLevel = p.ProtectionLevel  
  
    Console.WriteLine("Number of configurations = " & n.ToString())  
    Console.WriteLine("VersionGUID = " & CType(p2.GetValue(p), String))  
    Console.WriteLine("ProtectionLevel = " & pl.ToString())  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
 **Salida del ejemplo:**  
  
 `Number of configurations = 2`  
  
 `VersionGUID = {09016682-89B8-4406-AAC9-AF1E527FF50F}`  
  
 `ProtectionLevel = DontSaveSensitive`  
  
## <a name="external-resources"></a>Recursos externos  
  
-   Entrada del blog sobre el [ejemplo de API, origen OleDB y destino OleDB](http://go.microsoft.com/fwlink/?LinkId=220824), en blogs.msdn.com.  
  
-   Entrada del blog sobre [EzAPI, actualizado para SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=243223), en blogs.msdn.com.  
  
## <a name="see-also"></a>Ver también  
 [Agregar tareas mediante programación](../../integration-services/building-packages-programmatically/adding-tasks-programmatically.md)  
  
  
