---
title: Comprobar la versión del controlador ODBC de SQL Server (Windows) | Microsoft Docs
ms.custom: ''
ms.date: 11/07/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- driver version number [ODBC]
- ODBC drivers, version number
ms.assetid: 43451080-a562-4231-b1d4-1ba35ca0ea79
caps.latest.revision: 23
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: c7e602687a8f677af5a3160a7e3e1c5b0c2f900d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32863420"
---
# <a name="check-the-odbc-sql-server-driver-version-windows"></a>Comprobar la versión del controlador ODBC de SQL Server (Windows)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Su equipo puede contener varios controladores ODBC, de [!INCLUDE[msCoName](../../includes/msconame-md.md)] y de otras empresas. En este tema se describe cómo usar el **Administrador de orígenes de datos ODBC** de Windows para comprobar la versión de los controladores ODBC instalados.  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-check-the-odbc-sql-server-driver-version-32-bit-odbc"></a>Para comprobar la versión del controlador ODBC de SQL Server (ODBC de 32 bits)  
  
-   En el **Administrador de origen de datos ODBC**, haga clic en la pestaña **Controladores** .  
  
     La información de la entrada de Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se muestra en la columna **Versión** .  


> [!NOTE]  
>  En el caso de conexiones a Azure Active Directory Authentication para SQL Database, instale el controlador más reciente, como [ODBC Driver 13.1 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53339).   

  
## <a name="see-also"></a>Ver también  
 [Abrir el Administrador de orígenes de datos ODBC](../../database-engine/configure-windows/open-the-odbc-data-source-administrator.md)  
  
  
