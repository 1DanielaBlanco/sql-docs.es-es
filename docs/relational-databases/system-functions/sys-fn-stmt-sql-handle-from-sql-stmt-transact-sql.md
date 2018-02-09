---
title: sys.fn_stmt_sql_handle_from_sql_stmt (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 6794e073-0895-4507-aba3-c3545acc843f
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c3ee062aeadaec0c79af0b822b50442d4c575902
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="sysfnstmtsqlhandlefromsqlstmt-transact-sql"></a>sys.fn_stmt_sql_handle_from_sql_stmt (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Obtiene el **stmt_sql_handle** para un [!INCLUDE[tsql](../../includes/tsql-md.md)] instrucción en tipo de parametrización (simple o forzada) determinado. Esto permite hacer referencia a las consultas almacenadas en el almacén de consultas mediante el uso de sus **stmt_sql_handle** cuando conozca su texto.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
sys.fn_stmt_sql_handle_from_sql_stmt   
(  
    'query_sql_text',   
    [ query_param_type   
) [;]  
```  
  
## <a name="arguments"></a>Argumentos  
 *query_sql_text*  
 Es el texto de la consulta en el que desea que el identificador de almacén de consultas. *query_sql_text* es un **nvarchar (max)**, no tiene ningún valor predeterminado.  
  
 *query_param_type*  
 Es el tipo de parámetro de la consulta. *query_param_type* es un **tinyint**. Los valores posibles son:  
  
-   NULL: el valor predeterminado es 0  
  
-   0: ninguno  
  
-   1 – usuario  
  
-   2-simple  
  
-   3 – forzada  
  
## <a name="columns-returned"></a>Columnas devueltas  
 En la tabla siguiente se muestra las columnas que sys.fn_stmt_sql_handle_from_sql_stmt devuelve.  
  
|Nombre de columna|Tipo|Description|  
|-----------------|----------|-----------------|  
|**statement_sql_handle**|**varbinary(64)**|El identificador SQL.|  
|**query_sql_text**|**nvarchar(max)**|El texto de la [!INCLUDE[tsql](../../includes/tsql-md.md)] instrucción.|  
|**query_parameterization_type**|**tinyint**|El tipo de la parametrización de la consulta.|  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 0 (correcto) o 1 (error)  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="permissions"></a>Permissions  
 Requiere la **EXECUTE** permiso en la base de datos y **eliminar** permiso en las vistas de catálogo del almacén de consultas.  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se ejecuta una instrucción y, a continuación, utiliza `sys.fn_stmt_sql_handle_from_sql_stmt` para devolver el identificador SQL de esa instrucción.  
  
```  
SELECT * FROM sys.databases;   
SELECT * FROM sys.fn_stmt_sql_handle_from_sql_stmt('SELECT * FROM sys.databases', NULL);  
```  
  
 Utilice la función para correlacionar datos de almacén de consultas con otras vistas de administración dinámica. El ejemplo siguiente:  
  
```  
SELECT qt.query_text_id, q.query_id, qt.query_sql_text, qt.statement_sql_handle,  
q.context_settings_id, qs.statement_context_id   
FROM sys.query_store_query_text AS qt  
JOIN sys.query_store_query AS q   
    ON qt.query_text_id = q.query_id  
CROSS APPLY sys.fn_stmt_sql_handle_from_sql_stmt (qt.query_sql_text, null) AS fn_handle_from_stmt  
JOIN sys.dm_exec_query_stats AS qs   
    ON fn_handle_from_stmt.statement_sql_handle = qs.statement_sql_handle;  
```  
  
## <a name="see-also"></a>Vea también  
 [sp_query_store_force_plan &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md)   
 [sp_query_store_remove_plan &#40;Transct-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-remove-plan-transct-sql.md)   
 [sp_query_store_unforce_plan &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md)   
 [sp_query_store_reset_exec_stats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-reset-exec-stats-transact-sql.md)   
 [sp_query_store_flush_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-flush-db-transact-sql.md)   
 [sp_query_store_remove_query &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-remove-query-transact-sql.md)   
 [Query Store Catalog Views &#40;Transact-SQL&#41; (Vistas de catálogo del Almacén de consultas &#40;Transact-SQL&#41;)](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)   
 [Supervisar el rendimiento mediante el almacén de consultas](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)  
  
  
