---
title: Instalar SQL Server Native Client | Documentos de Microsoft
ms.custom: 
ms.date: 07/15/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|applications
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, uninstalling
- SQLNCLI, installing
- SQLNCLI, uninstalling
- Setup [SQL Server Native Client]
- uninstalling SQL Server Native Client
- data access [SQL Server Native Client], uninstalling SQL Server Native Client
- installing SQL Server Native Client
- SQL Server Native Client, installing
- data access [SQL Server Native Client], installing SQL Server Native Client
- removing SQL Server Native Client
ms.assetid: c6abeab2-0052-49c9-be79-cfbc50bff5c1
caps.latest.revision: "44"
manager: craigg
ms.workload: Active
ms.openlocfilehash: f981559ea90373bab72d25689196b50fcd97b0c4
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2018
---
# <a name="installing-sql-server-native-client"></a>Instalar SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
 > Para el contenido relacionado con las versiones anteriores de SQL Server, vea [instalar SQL Server Native Client](https://msdn.microsoft.com/en-US/library/ms131321(SQL.120).aspx).

[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 se instala al instalar [!INCLUDE[ssSQL15](../../../includes/sssql15-md.md)]. 
 
 No hay ningún cliente nativo de SQL Server 2016. Para obtener más información, consulte [SQL Server Native Client](../../../relational-databases/native-client/sql-server-native-client.md). 
 
También puede obtener sqlncli.msi de la página web de SQL Server 2012 Feature Pack. Para descargar la versión más reciente de las SQL Server Native Client, vaya a [Microsoft® SQL Server® 2012 Feature Pack](http://www.microsoft.com/en-us/download/confirmation.aspx?id=29065). Si una versión anterior de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client anteriores a SQL Server 2012 también está instalado en el equipo, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 estarán instalados en paralelo con la versión anterior.  
  
 Los archivos de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (sqlncli11.dll, sqlnclir11.rll y s11ch_sqlncli.chm) se instalan en la siguiente ubicación:  
  
 `%SYSTEMROOT%\system32\`  
  
> [!NOTE]  
>  Todos los valores del Registro adecuados para el proveedor OLE DB de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client y el controlador ODBC de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client se crean como parte del proceso de instalación.  
  
 Los archivos de encabezado y biblioteca de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (sqlncli.h y sqlncli11.lib) se instalan en la siguiente ubicación:  
  
 `%PROGRAMFILES%\Microsoft SQL Server\110\SDK`  
  
 Además de instalar [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client como parte de la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instalación, también hay un programa de instalación redistribuible denominado sqlncli.msi, que se encuentra en la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] disco de instalación en la siguiente ubicación: `%CD%\Setup\`.  
  
 Puede distribuir [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client a través de sqlncli.msi. Es posible que tenga que instalar [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client al implementar una aplicación. Una manera de instalar varios paquetes en lo que al usuario le parece ser una instalación única es usar tecnología de encadenador y arranque. Para obtener más información, consulte [crear un paquete de arranque personalizado para Visual Studio 2005](http://go.microsoft.com/fwlink/?LinkId=115667) y [Agregar requisitos previos personalizados](http://go.microsoft.com/fwlink/?LinkId=115668).  
  
 Las versiones x64 e Itanium de sqlncli.msi también instalan las versiones de 32 bits de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Si su aplicación está diseñada para una plataforma distinta de aquella en la que se desarrolló, puede descargar versiones de sqlncli.msi para x64, Itanium y x86 en el Centro de descarga de Microsoft.  
  
 Cuando se llama a sqlncli.msi, solo se instalan los componentes de cliente de forma predeterminada. Los componentes de cliente son archivos que permiten la ejecución de una aplicación que se desarrolló mediante [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Para instalar también los componentes SDK, especifique `ADDLOCAL=All` en la línea de comandos. Por ejemplo:  
  
 `msiexec /i sqlncli.msi ADDLOCAL=ALL APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
## <a name="silent-install"></a>Instalación silenciosa  
 Si usa la opción /passive, /qn, /qb o /qr con msiexec, también debe especificar IACCEPTSQLNCLILICENSETERMS=YES, para indicar explícitamente que acepta los términos de la licencia de usuario final. Esta opción se debe especificar con todas las letras mayúsculas.  
  
## <a name="uninstalling-sql-server-native-client"></a>Desinstalar SQL Server Native Client  
 Dado que aplicaciones como [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] servidor y el [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] herramientas dependen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, es importante no desinstalar [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client hasta que se desinstalen todas las aplicaciones dependientes. A los usuarios de proveedor con una advertencia que depende la aplicación [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, utilice la opción de instalación APPGUID en su MSI, como se indica a continuación:  
  
 `msiexec /i sqlncli.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
 El valor pasado a APPGUID es su código de producto específico. Se debe crear un código de producto al usar Microsoft Installer para empaquetar su programa de instalación de la aplicación.  
  
## <a name="see-also"></a>Vea también  
 [Creación de aplicaciones con SQL Server Native Client](../../../relational-databases/native-client/applications/installing-sql-server-native-client.md)   
 [Temas de procedimientos de instalación](http://msdn.microsoft.com/library/59de41e7-557f-462a-8914-53ec35496baa)  
  
  
