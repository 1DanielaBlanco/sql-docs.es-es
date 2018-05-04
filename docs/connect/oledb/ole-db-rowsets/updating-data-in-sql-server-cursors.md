---
title: Actualizar datos en los cursores SQL Server | Documentos de Microsoft
description: Actualizar datos en los cursores de SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- isolation levels [SQL Server]
- delayed update mode [OLE DB]
- immediate update mode [OLE DB]
- cursors [OLE DB]
- data updates [SQL Server], OLE DB
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: cb4513b1e674b8d55503ba6ea494e0445785bb17
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="updating-data-in-sql-server-cursors"></a>Actualizar datos en cursores de SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Al buscar y actualizar datos a través de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cursores, un controlador de OLE DB para SQL Server la aplicación de consumidor está limitada por las mismas consideraciones y restricciones que se aplican a cualquier otra aplicación cliente.  
  
 Solo las filas de cursores de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] participan en el control del acceso simultáneo a datos. Cuando el consumidor solicita un conjunto de filas modificable, DBPROP_LOCKMODE controla el control de simultaneidad. Para modificar el nivel de control de acceso simultáneo, el consumidor establece la propiedad DBPROP_LOCKMODE antes de abrir el conjunto de filas.  
  
 Los niveles de aislamiento de las transacciones pueden producir diferencias significativas en la posición de las filas si el diseño de la aplicación cliente permite que las transacciones permanezcan abiertas durante largos períodos de tiempo. De forma predeterminada, el controlador OLE DB para SQL Server utiliza el nivel de aislamiento de lectura confirmada especificado por DBPROPVAL_TI_READCOMMITTED. El controlador OLE DB para SQL Server admite el aislamiento de lectura de datos sucio cuando la simultaneidad del conjunto de filas es de solo lectura. Por consiguiente, el consumidor puede solicitar un nivel superior de aislamiento en un conjunto de filas modificable pero no puede solicitar con éxito un nivel inferior.  
  
## <a name="immediate-and-delayed-update-modes"></a>Modos de actualización inmediata y retrasada  
 En el modo de actualización inmediata, cada llamada a **IRowsetChange:: SetData** hace un recorrido de ida y a la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Si el consumidor realiza varios cambios en una sola fila, resulta más eficaz enviar todos los cambios con una sola **SetData** llamar.  
  
 En el modo de actualización retrasada, se realiza un ida y vuelta a la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] para cada fila indicada en el *cRows* y *rghRows* parámetros de **IRowsetUpdate:: Update**.  
  
 En ambos modos, un viaje de ida y vuelta representa una transacción distinta cuando no queda abierto ningún objeto de transacción para el conjunto de filas.  
  
 Cuando se utiliza **IRowsetUpdate:: Update**, el controlador OLE DB para SQL Server intenta procesar cada fila indicada. Un error que se producen debido a valores de datos, la longitud o el estado no válidos para una fila no detiene el controlador OLE DB para el procesamiento de SQL Server. Se pueden modificar todas o ninguna de las demás filas que participan en la actualización. El consumidor debe examinar el valor devuelto *prgRowStatus* matriz para determinar el error de cualquier fila concreta cuando el controlador OLE DB para SQL Server devuelve DB_S_ERRORSOCCURRED.  
  
 Un consumidor no debe suponer que las filas se procesan en un orden determinado. Si un consumidor necesita el procesamiento ordenado de modificación de datos en más de una fila, debe establecer ese orden en la lógica de la aplicación y abrir una transacción para incluir en ella el proceso.  
  
## <a name="see-also"></a>Vea también  
 [Actualizar datos en conjuntos de filas](../../oledb/ole-db-rowsets/updating-data-in-rowsets.md)  
  
  
