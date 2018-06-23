---
title: Archivos y números de versión | Documentos de Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, versions
- components [SMO]
- files [SMO], components
- SMO [SQL Server], versions
- versions [SMO]
ms.assetid: 510907b6-e7a9-41bd-b892-d6d99a5118e1
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 63602af6a7d798086c3e41d3796b20a2f71d6950
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36203915"
---
# <a name="files-and-version-numbers"></a>Archivos y números de versión
  Todos los [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] componentes de Management Objects (SMO) se instalan como parte de una instancia de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cliente o servidor. SMO se implementa en varios ensamblados administrados. Puede desarrollar aplicaciones SMO en un cliente o un servidor.  
  
|Directorio|Archivo|Descripción|  
|---------------|----------|-----------------|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|Microsoft.SqlServer.ConnectionInfo.dll|Contiene compatibilidad para conectar a una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|Microsoft.SqlServer.ServiceBrokerEnum.dll|Contiene compatibilidad para programar [!INCLUDE[msCoName](../../includes/msconame-md.md)] Service Broker. Solo se requiere en programas que tienen acceso a Service Broker.|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|Microsoft.SqlServer.Smo.dll|Contiene la mayoría de las clases SMO.|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|Microsoft.SqlServer.SmoExtended.dll<br /><br /> Microsoft.SqlServer.Management.Sdk.Sfc.dll<br /><br /> Microsoft.SqlServer.SqlEnum.dll|Contiene compatibilidad para las clases SMO.|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|Microsoft.SqlServer.WmiEnum.dll|Contiene las clases de proveedor de Instrumental de administración de Windows (WMI). Solo se requiere en los programas que utilizan las clases del proveedor WMI.|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|Microsoft.SqlServer.RegSvrEnum.dll|Contiene las clases de servidor registrado. Solo se requiere en los programas que utilizan las clases de servidor registrado.|  
  
  