---
title: Llamar a procedimientos almacenados (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], calling
ms.assetid: 31176be8-d40e-4f93-8d44-a46e804a3e2d
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 82845d2faac407385cf3ec8036fd6b63e5457b3c
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "43085179"
---
# <a name="running-stored-procedures---call-stored-procedures"></a>Ejecutar procedimientos almacenados: llamar a procedimientos almacenados
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  El controlador ODBC de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permite ejecutar los procedimientos almacenados como procedimientos almacenados remotos. La ejecución de un procedimiento almacenado como un procedimiento almacenado remoto permite al controlador y al servidor optimizar el rendimiento de la ejecución del procedimiento.  
  
  Cuando una instrucción SQL llama a un procedimiento almacenado mediante la cláusula de escape ODBC CALL, el controlador de Microsoft® SQL Server™ envía el procedimiento a SQL Server usando el mecanismo de llamada a un procedimiento almacenado remoto (RPC). Las solicitudes de RPC omiten gran parte del análisis de la instrucción y del procesamiento del parámetro en SQL Server, y es más rápido que usar la instrucción Transact-SQL EXECUTE.  
  
 Para una aplicación de ejemplo que muestra esta característica, consulte [proceso códigos de retorno y parámetros de salida &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/running-stored-procedures-process-return-codes-and-output-parameters.md).  
  
### <a name="to-run-a-procedure-as-an-rpc"></a>Para ejecutar un procedimiento como una RPC  
  
1.  Cree una instrucción SQL que use la secuencia de escape ODBC CALL. La instrucción usa marcadores de parámetros para cada parámetro de entrada, de entrada/salida y de salida, así como para el valor devuelto por el procedimiento (si existe):  
  
    ```  
    {? = CALL procname (?,?)}  
    ```  
  
2.  Llame a [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) para cada entrada, entrada/salida y el parámetro de salida y para el procedimiento de valor devuelto (si existe).  
  
3.  Ejecute la instrucción con [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399).  
  
> [!NOTE]  
>  Si una aplicación envía un procedimiento con la sintaxis de Transact-SQL EXECUTE (en contraposición al flujo de escape ODBC CALL), el controlador ODBC de SQL Server pasa la llamada al procedimiento a SQL Server como una instrucción SQL en lugar de como una RPC. Además, los parámetros de salida no se devuelven si se usa la instrucción Transact-SQL EXECUTE.  
  
## <a name="see-also"></a>Vea también  
  [Procesamiento por lotes las llamadas de procedimiento almacenado](../../relational-databases/native-client-odbc-stored-procedures/batching-stored-procedure-calls.md)   
 [Ejecutar procedimientos almacenados](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)   
 [Llamar a un procedimiento almacenado](../../relational-databases/native-client-odbc-stored-procedures/calling-a-stored-procedure.md)   
 [Procedimientos](../../relational-databases/native-client-odbc-queries/executing-statements/procedures.md)  
  
  
