---
title: "Establecer un idioma de la sesi&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "errores [SQL Server], consideraciones internacionales"
  - "globalización [SQL Server], sesiones"
  - "tiempo [SQL Server]"
  - "sesiones [SQL Server], idiomas"
  - "consideraciones internacionales [SQL Server], sesiones"
  - "fechas [SQL Server], idiomas de la sesión"
  - "consideraciones globales [SQL Server], sesiones"
  - "idioma de la sesión del cliente"
  - "hora [SQL Server], idiomas de la sesión"
  - "mensajes [SQL Server], consideraciones internacionales"
  - "idioma de la sesión del servidor"
ms.assetid: de7f2c90-8f4f-4cfc-94cc-4933a7fd2bde
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# Establecer un idioma de la sesi&#243;n
  El idioma de la sesión se puede utilizar para establecer la forma en que se muestran los siguientes elementos en el servidor, dependiendo de la preferencia cultural y de idioma:  
  
-   El lenguaje que se usará para los mensajes de error y otros mensajes del sistema. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] admite varias copias de todas las cadenas de error del sistema y mensajes en todos los idiomas en los que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] está disponible. Estos mensajes se pueden ver en la vista de catálogo [sys.messages](../Topic/sys.messages%20\(Transact-SQL\).md) . Cuando se instala una versión traducida de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], estos mensajes del sistema se traducen a la versión de idioma que se instala. También se obtiene de forma predeterminada. El conjunto en inglés de EE.UU. de estos mensajes Además, se pueden agregar mensajes definidos por el usuario en un idioma específico con [sp_addmessage](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md).  
  
-   El formato de los datos de fecha y hora.  
  
-   Los nombres de días y meses, incluidas las abreviaturas.  
  
-   El primer día de la semana.  
  
-   Los datos de moneda.  
  
 Existen 33 idiomas disponibles para ser utilizados como valores de la sesión. Para obtener una lista de los idiomas, vea [sys.syslanguages](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md).  
  
## Configurar el idioma de la sesión desde el servidor  
 Para establecer el idioma de la sesión desde el servidor, utilice [SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md).  
  
## Configurar el idioma de la sesión desde el cliente  
 El idioma de la sesión se puede establecer del lado cliente con OLE DB, ODBC o ADO.NET. Para OLE DB, utilice la propiedad SSPROP_INIT_CURRENTLANGUAGE. Para obtener más información, vea [Propiedades de inicialización y autorización](../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md).  
  
 Para ODBC, utilice la palabra clave Language. Para más información, consulte [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md).  
  
 Para ADO.NET, utilice el parámetro **Current Language** del objeto **ConnectionString** . Para obtener más información, vea la documentación del kit de desarrollo de software (SDK) de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Data Access Components (MDAC).  
  
  