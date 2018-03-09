---
title: Llamadas a procedimientos almacenados de procesamiento por lotes | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], batching
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- batches [ODBC]
- ODBC CALL escape sequence
ms.assetid: b7f53e11-15f0-4602-8134-b166160888f0
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0f2015efa4e176865d3fa99c24b9bc7f9a616643
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="batching-stored-procedure-calls"></a>Procesar por lotes las llamadas a procedimientos almacenados
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] controlador ODBC Native Client procesa automáticamente por lotes las llamadas a procedimientos almacenados en el servidor cuando sea apropiado. El controlador solamente hace esto cuando se usa la secuencia de escape ODBC CALL; no lo hace para la instrucción EXECUTE de [!INCLUDE[tsql](../../includes/tsql-md.md)]. El procesamiento por lotes de las llamadas de procedimiento almacenado puede reducir el número de ciclos de ida y vuelta del servidor y aumentar de forma significativa el rendimiento.  
  
 El controlador procesa por lotes las llamadas de procedimiento al servidor al ejecutar un lote que contiene varias secuencias de escape ODBC CALL. También procesa por lotes las llamadas a procedimiento cuando se usan las matrices de parámetros enlazadas con una secuencia de escape ODBC CALL. Por ejemplo, si utiliza cualquier enlace de parámetros de modo de fila o columna para enlazar una matriz con cinco elementos a los parámetros de una instrucción ODBC CALL de SQL, cuando **SQLExecute** o **SQLExecDirect** se llama, el controlador envía un lote único con cinco llamadas de procedimiento en el servidor.  
  
## <a name="see-also"></a>Vea también  
 [Ejecutar procedimientos almacenados](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
