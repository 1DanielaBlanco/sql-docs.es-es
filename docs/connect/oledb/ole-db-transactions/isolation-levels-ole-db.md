---
title: Niveles de aislamiento (OLE DB) | Microsoft Docs
description: Niveles de aislamiento (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-transactions
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- isolation levels [OLE DB]
- transactions [OLE DB]
- OLE DB Driver for SQL Server, transactions
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 4bcb9de1cc0d09875dbe283b6ac8fe3cf46e883f
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "43024781"
---
# <a name="isolation-levels-ole-db"></a>Niveles de aislamiento (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Los clientes [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pueden controlar los niveles de aislamiento de la transacción para una conexión. Para controlar el nivel de aislamiento de transacción, se usa el controlador OLE DB para el consumidor de SQL Server:  
  
-   La propiedad de DBPROPSET_SESSION DBPROP_SESS_AUTOCOMMITISOLEVELS para el modo de confirmación automática predeterminado del controlador OLE DB para SQL Server.  
  
     El controlador OLE DB para el valor predeterminado de SQL Server para el nivel es DBPROPVAL_TI_READCOMMITTED.  
  
-   El parámetro *isoLevel* del método **ITransactionLocal::StartTransaction** para las transacciones locales de confirmación manual.  
  
-   El parámetro *isoLevel* del método **ITransactionDispenser::BeginTransaction** para las transacciones distribuidas coordinadas por MS DTC.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] permite el acceso de solo lectura en el nivel de aislamiento de lectura de datos sucios. Todos los demás niveles restringen la simultaneidad aplicando bloqueos a los objetos [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Cuando el cliente requiere niveles de simultaneidad mayores, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] aplica mayores restricciones al acceso simultáneo a los datos. Para mantener el mayor nivel de acceso simultáneo a los datos, el consumidor del controlador OLE DB para SQL Server debe controlar inteligentemente sus solicitudes de niveles de simultaneidad específicos.  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] presentó el nivel del aislamiento de instantánea. Para obtener más información, vea [Trabajar con aislamiento de instantánea](../../oledb/features/working-with-snapshot-isolation.md).  
  
## <a name="see-also"></a>Ver también  
 [Transacciones](../../oledb/ole-db-transactions/transactions.md)  
  
  
