---
title: Las transacciones en ODBC | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client|ODBC
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, transactions
- transactions [ODBC]
- ODBC, transactions
ms.assetid: c5a87fa5-827a-4e6f-a0d9-924bac881eb0
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: bb43eb3868027e9fca091f79ee8ee7f331262285
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2018
ms.locfileid: "37421864"
---
# <a name="performing-transactions-in-odbc"></a>Realizar transacciones en ODBC
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Las transacciones en ODBC se administran en las conexiones. Cuando una aplicación completa una transacción, confirma o revierte todo el trabajo completado a través de todos los identificadores de instrucciones de dicha conexión. Para confirmar o revertir una transacción, las aplicaciones deberían llamar a [SQLEndTran](../../../relational-databases/native-client-odbc-api/sqlendtran.md) en lugar de enviar una instrucción COMMIT o ROLLBACK.  
  
 Una aplicación llama a [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) para intercambiar entre los dos modos ODBC de administrar transacciones:  
  
-   Modo de confirmación automática  
  
     Todas las instrucciones se confirman automáticamente cuando se completan correctamente. Cuando se ejecuta en modo de confirmación automática, no se requiere ninguna otra función de administración de transacciones.  
  
-   Modo de confirmación manual  
  
     Todos las instrucciones ejecutadas se incluyen en la misma transacción hasta que se detenga específicamente llamando a **SQLEndTran**.  
  
 El modo de confirmación automática es el modo de transacción para ODBC. Cuando se realiza una conexión, se encuentra en modo de confirmación automática hasta que se llame a **SQLSetConnectAttr** para pasar al modo de confirmación manual desactivando el modo de confirmación automática. Cuando una aplicación desactiva la confirmación automática, la siguiente instrucción enviada a la base de datos inicia una transacción. A continuación, la transacción permanece activa hasta que la aplicación llama a **SQLEndTran** con las opciones SQL_COMMIT o SQL_ROLLBACK. El comando enviado a la base de datos después de que **SQLEndTran** inicia la siguiente transacción.  
  
 Si una aplicación pasa del modo de confirmación manual al modo de confirmación automática, el controlador confirma cualquier transacción actualmente abierta en la conexión.  
  
 Las aplicaciones ODBC no deberían usar instrucciones de transacción de Transact-SQL como BEGIN TRANSACTION, COMMIT TRANSACTION o ROLLBACK TRANSACTION porque esto puede producir un comportamiento indeterminado en el controlador. Una aplicación ODBC se debería ejecutar en modo de confirmación automática y no usar instrucciones o funciones de administración de transacciones o bien, ejecutarse en el modo de confirmación manual y usar la función **SQLEndTran** ODBC para confirmar o revertir transacciones.  
  
## <a name="see-also"></a>Vea también  
 [Realizar transacciones &#40;ODBC&#41;](http://msdn.microsoft.com/library/f431191a-5762-4f0b-85bb-ac99aff29724)  
  
  
