---
title: Utilizar servidores vinculados en SMO | Documentos de Microsoft
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: smo
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- linked servers [SQL Server], SMO
ms.assetid: 0ea8837b-2596-4df1-b065-3bb717c9f22c
caps.latest.revision: 36
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 5e14e7516cbf5998c89165efe6b55775d8da9ecb
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="using-linked-servers-in-smo"></a>Utilizar servidores vinculados en SMO
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Un servidor vinculado representa un origen de datos OLE DB en un servidor remoto. Orígenes de datos OLE DB remotos están vinculados a la instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mediante el uso de la <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> objeto.  
  
 Servidores de base de datos remota pueden vincularse a la instancia actual de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mediante un proveedor OLE DB. En SMO, los servidores vinculados están representados por la <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> objeto. El <xref:Microsoft.SqlServer.Management.Smo.LinkedServer.LinkedServerLogins%2A> propiedad hace referencia a una colección de <xref:Microsoft.SqlServer.Management.Smo.LinkedServerLogin> objetos. Estos objetos almacenan las credenciales de inicio de sesión necesarias para establecer una conexión con el servidor vinculado.  
  
## <a name="ole-db-providers"></a>Proveedores OLE-DB  
 En SMO, una colección de objetos <xref:Microsoft.SqlServer.Management.Smo.OleDbProviderSettings> representa los proveedores OLE DB instalados.  
  
## <a name="example"></a>Ejemplo  
 Para los siguientes ejemplos de código, deberá seleccionar el entorno de programación, la plantilla de programación y el lenguaje de programación en los que crear su aplicación. Para obtener más información, consulte [crear a Visual C&#35; proyecto SMO en Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-visual-c"></a>Crear un vínculo a un servidor de proveedor OLE-DB en Visual C#  
 El ejemplo de código muestra cómo crear un vínculo a un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB, origen de datos heterogéneo mediante el uso de la <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> objeto. Mediante la especificación de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] como el nombre del producto, acceso a los datos en el servidor vinculado mediante el uso de la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cliente proveedor OLE DB, que es el proveedor OLE DB oficial para [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```csharp  
//Connect to the local, default instance of SQL Server.   
{   
   Server srv = new Server();   
   //Create a linked server.   
   LinkedServer lsrv = default(LinkedServer);   
   lsrv = new LinkedServer(srv, "OLEDBSRV");   
   //When the product name is SQL Server the remaining properties are   
   //not required to be set.   
   lsrv.ProductName = "SQL Server";   
   lsrv.Create();   
}   
```  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-powershell"></a>Crear un vínculo a un servidor de proveedor OLE-DB en PowerShell  
 El ejemplo de código muestra cómo crear un vínculo a un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB, origen de datos heterogéneo mediante el uso de la <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> objeto. Mediante la especificación de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] como el nombre del producto, acceso a los datos en el servidor vinculado mediante el uso de la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cliente proveedor OLE DB, que es el proveedor OLE DB oficial para [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```powershell  
#Get a server object which corresponds to the default instance  
$svr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Create a linked server object which corresponds to an OLEDB type of SQL server product  
$lsvr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.LinkedServer -argumentlist $svr,"OLEDBSRV"  
  
#When the product name is SQL Server the remaining properties are not required to be set.   
$lsvr.ProductName = "SQL Server"  
  
#Create the Database Object  
$lsvr.Create()   
```  
  
  
