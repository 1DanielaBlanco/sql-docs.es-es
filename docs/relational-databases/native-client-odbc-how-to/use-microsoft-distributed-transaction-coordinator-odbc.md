---
title: Utilice Microsoft Distributed Transaction Coordinator (ODBC) | Documentos de Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-how-to
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: MS DTC, using
ms.assetid: 12a275e1-8c7e-436d-8a4e-b7bee853b35c
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a1f982500e38722032f1edb9ffda70eee8b12251
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="use-microsoft-distributed-transaction-coordinator-odbc"></a>Usar Microsoft DTC (Coordinador de transacciones distribuidas) (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

    
### <a name="to-update-two-or-more-sql-servers-by-using-ms-dtc"></a>Para actualizar dos o más servidores SQL Server mediante MS DTC  
  
1.  Conéctese a MS DTC utilizando la función OLE DtcGetTransactionManager de MS DTC. Para obtener información acerca de MS DTC, vea Microsoft DTC (Coordinador de transacciones distribuidas).  
  
2.  Llame a SQL DriverConnect una vez para cada conexión que desee establecer a Microsoft® SQL Server™.  
  
3.  Llame a la función OLE ITransactionDispenser::BeginTransaction de MS DTC para iniciar una transacción MS DTC y obtener un objeto Transaction que represente la transacción.  
  
4.  Llame a [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) una vez o más para cada conexión ODBC que quiera dar de alta en la transacción de MS DTC. Es preciso que el segundo parámetro de [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) sea SQL_ATTR_ENLIST_IN_DTC y que el tercer parámetro sea un objeto Transaction (obtenido en el paso 3).  
  
5.  Llame una vez a [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399) para cada servidor SQL Server que quiera actualizar.  
  
6.  Llame a la función OLE ITransaction::Commit de MS DTC para confirmar la transacción MS DTC. El objeto Transaction ya no es válido.  
  
 Para realizar una serie de transacciones MS DTC, repita los pasos del 3 al 6.  
  
 Para liberar la referencia al objeto Transaction, llame a la función OLE ITransaction::Return de MS DTC.  
  
 Para usar una conexión ODBC con una transacción MS DTC y, después, usar la misma conexión con una transacción local de SQL Server, llame a [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) con SQL_DTC_DONE.  
  
> [!NOTE]  
>  También puede llamar a [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) y [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399) sucesivamente para cada servidor SQL Server en lugar de llamarlos tal y como se sugería anteriormente en los pasos 4 y 5.  
  
## <a name="see-also"></a>Vea también  
 [Realización de transacciones &#40; ODBC &#41;](http://msdn.microsoft.com/library/f431191a-5762-4f0b-85bb-ac99aff29724)  
  
  
