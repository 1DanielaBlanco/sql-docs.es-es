---
title: Compatibilidad del controlador OLE DB para SQL Server con LocalDB | Microsoft Docs
description: Compatibilidad del controlador OLE DB para SQL Server con LocalDB
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 6dc2acb8239c8c4002094ffb6003cb1b9a5fe40e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47768963"
---
# <a name="ole-db-driver-for-sql-server-support-for-localdb"></a>Controlador OLE DB para la compatibilidad de SQL Server con LocalDB
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  A partir de [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], estará disponible una versión ligera de SQL Server, denominada LocalDB. En este tema se describe cómo conectarse a una base de datos en una instancia de LocalDB.  
  
## <a name="remarks"></a>Notas  
 Para obtener más información acerca de LocalDB, incluyendo cómo instalarlo y configurar la instancia de LocalDB, vea:  
  
-   [Referencia de SQL Server Express LocalDB](../../../relational-databases/sql-server-express-localdb-reference.md)  
  
-   [SQL Server 2016 Express LocalDB](../../../database-engine/configure-windows/sql-server-2016-express-localdb.md)  
  
 En resumen, LocalDB permite:  
  
-   Usar **sqllocaldb.exe i** para detectar el nombre de la instancia predeterminada.  
  
-   Usar la palabra clave de la cadena de conexión de **AttachDBFilename** para especificar a qué el archivo de base de datos se debe adjuntar el servidor. Al utilizar **AttachDBFilename**, si no especifica el nombre de la base de datos con la palabra clave de la cadena de conexión **Database** , la base de datos se quitará de la instancia de LocalDB cuando se cierre la aplicación.  
  
-   Especifique una instancia de LocalDB en la cadena de conexión:  
  
```  
SERVER=(localdb)\v11.0  
```  
  
 Si fuera necesario, puede crear una instancia de LocalDB con sqllocaldb.exe. También puede utilizar sqlcmd.exe para agregar y modificar las bases de datos de una instancia de LocalDB. Por ejemplo, **sqlcmd -S (localdb)\v11.0**.  
  
## <a name="see-also"></a>Ver también  
 [Controlador OLE DB para las características de SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
