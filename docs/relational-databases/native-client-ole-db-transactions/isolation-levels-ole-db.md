---
title: Niveles de aislamiento (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- isolation levels [OLE DB]
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: d70ee72c-6e2a-4bcd-9456-4a697a866361
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 00d6b525c0a52fb5b792926f110d73d3d77bdd6a
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2018
ms.locfileid: "37421096"
---
# <a name="isolation-levels-ole-db"></a>Niveles de aislamiento (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Los clientes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pueden controlar los niveles de aislamiento de la transacción para una conexión. Para controlar el nivel de aislamiento de transacción, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consumidor de proveedor OLE DB de Native Client usa:  
  
-   Propiedad de DBPROPSET_SESSION DBPROP_SESS_AUTOCOMMITISOLEVELS para el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] modo de confirmación automática predeterminada de proveedor de OLE DB de Native Client.  
  
     El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] predeterminado del proveedor OLE DB de Native Client para el nivel es DBPROPVAL_TI_READCOMMITTED.  
  
-   El *isoLevel* parámetro de la **ITransactionLocal:: StartTransaction** método para realizar transacciones locales de confirmación manual.  
  
-   El *isoLevel* parámetro de la **ITransactionDispenser:: BeginTransaction** transacciones distribuidas de método para coordinada con MS DTC.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permite el acceso de solo lectura en el nivel de aislamiento de lectura de datos sucios. Todos los demás niveles restringen la simultaneidad aplicando bloqueos a los objetos [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cuando el cliente requiere niveles de simultaneidad mayores, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aplica mayores restricciones al acceso simultáneo a los datos. Para mantener el máximo nivel de acceso simultáneo a datos, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consumidor del proveedor OLE DB de Native Client debe controlar inteligentemente sus solicitudes para los niveles de simultaneidad específicos.  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] presentó el nivel del aislamiento de instantánea. Para obtener más información, consulte [trabajar con aislamiento de instantánea](../../relational-databases/native-client/features/working-with-snapshot-isolation.md).  
  
## <a name="see-also"></a>Vea también  
 [Transacciones](../../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
  
