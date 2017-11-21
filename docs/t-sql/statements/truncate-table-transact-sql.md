---
title: TRUNCATE TABLE (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TRUNCATE
- TRUNCATE TABLE
- TRUNCATE_TSQL
- TRUNCATE_TABLE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- row removal [SQL Server], TRUNCATE TABLE statement
- table truncating [SQL Server]
- removing rows
- TRUNCATE TABLE statement
- deleting rows
- dropping rows
ms.assetid: 3d544eed-3993-4055-983d-ea334f8c5c58
caps.latest.revision: 41
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: dd20fe12af6f1dcaf378d737961bc2ba354aabe5
ms.openlocfilehash: 1d393c67c8489765aa92c861bc28c8e4d0e2eea4
ms.contentlocale: es-es
ms.lasthandoff: 10/04/2017

---
# <a name="truncate-table-transact-sql"></a>TRUNCATE TABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Quita todas las filas de una tabla o las particiones especificadas de una tabla, sin iniciar la eliminación de filas individuales. TRUNCATE TABLE es similar a la instrucción DELETE sin una cláusula WHERE; no obstante, TRUNCATE TABLE es más rápida y utiliza menos recursos de registros de transacciones y de sistema.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```tsql  
-- Syntax for SQL Server and Azure SQL Database  
  
TRUNCATE TABLE   
    [ { database_name .[ schema_name ] . | schema_name . } ]  
    table_name  
    [ WITH ( PARTITIONS ( { <partition_number_expression> | <range> }   
    [ , ...n ] ) ) ]  
[ ; ]  
  
<range> ::=  
<partition_number_expression> TO <partition_number_expression>  
```  
  
```tsql  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
TRUNCATE TABLE [ { database_name . [ schema_name ] . | schema_name . ] table_name  
[;]  
```  
  
## <a name="arguments"></a>Argumentos  
 *database_name*  
 Es el nombre de la base de datos.  
  
 *schema_name*  
 Es el nombre del esquema al que pertenece la tabla.  
  
 *table_name*  
 Es el nombre de la tabla que se va a truncar o de la que se van a quitar todas las filas. *table_name* debe ser un literal. *table_name* no puede ser el **object_id ()** función o una variable.  
  
 CON (particiones ({ \< *partition_number_expression*> | \< *intervalo*>} [,.. .n]))  
**Se aplica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a través de [versión actual](http://go.microsoft.com/fwlink/p/?LinkId=299658))
  
 Especifica las particiones para truncar o desde las que se quitan todas las filas. Si la tabla no tiene particiones, la **con particiones** argumento generará un error. Si el **con particiones** cláusula no se proporciona, se truncará toda la tabla.  
  
 *\<partition_number_expression >* se puede especificar de las maneras siguientes: 
  
-   Proporcione el número de una partición, por ejemplo:`WITH (PARTITIONS (2))`  
  
-   Proporcione el número de particiones para varias particiones individuales separadas por comas, por ejemplo:`WITH (PARTITIONS (1, 5))`  
  
-   Proporcione ambos rangos y particiones individuales, por ejemplo:`WITH (PARTITIONS (2, 4, 6 TO 8))`  
  
-   *\<intervalo >* se puede especificar como números de partición separados por la palabra **TO**, por ejemplo:`WITH (PARTITIONS (6 TO 8))`  
  
 Para truncar una tabla con particiones, la tabla y los índices se deben alinear (con particiones en la misma función de partición).  
  
## <a name="remarks"></a>Comentarios  
 En comparación con la instrucción DELETE, TRUNCATE TABLE ofrece las siguientes ventajas:  
  
-   Se utiliza menos espacio del registro de transacciones.  
  
     La instrucción DELETE quita una a una las filas y graba una entrada en el registro de transacciones por cada fila eliminada. TRUNCATE TABLE quita los datos al cancelar la asignación de las páginas de datos utilizadas para almacenar los datos de la tabla y solo graba en el registro de transacciones las cancelaciones de asignación de páginas.  
  
-   Por regla general, se utilizan menos bloqueos.  
  
     Si se ejecuta la instrucción DELETE con un bloqueo de fila, se bloquea cada fila de la tabla para su eliminación. TRUNCATE TABLE siempre bloquea la tabla (incluido un bloqueo de esquema (SCH-M)) y la página, pero no cada fila.  
  
-   Las páginas cero se conservan en la tabla sin excepciones.  
  
     Después de ejecutar una instrucción DELETE, la tabla puede seguir conteniendo páginas vacías. Por ejemplo, no se puede cancelar la asignación de las páginas vacías de un montón sin un bloqueo de tabla exclusivo (LCK_M_X) como mínimo. Si en la operación de eliminación no se utiliza un bloqueo de tabla, la tabla (montón) contiene muchas páginas vacías. En el caso de los índices, la operación de eliminación puede dejar páginas vacías, aunque la asignación de estas páginas se puede cancelar rápidamente mediante un proceso de limpieza en segundo plano.  
  
 TRUNCATE TABLE quita todas las filas de una tabla, pero permanecen la estructura y sus columnas, las restricciones, los índices, etc. Para quitar la definición de tabla además de los datos, utilice la instrucción DROP TABLE.  
  
 Si la tabla contiene una columna de identidad, el contador para dicha columna se restablece al valor de inicialización definido para ella. Si no se define ningún valor de inicialización, se utiliza el valor predeterminado 1. Para conservar el contador de identidad, utilice DELETE.  
  
## <a name="restrictions"></a>Restricciones  
 No puede utilizar TRUNCATE TABLE en las siguientes tablas:  
  
-   Tablas a las que se hace referencia mediante una restricción FOREIGN KEY. (Puede truncar una tabla que tenga una clave externa que haga referencia a sí misma).  
  
-   Tablas que participan en una vista indizada.  
  
-   Tablas que se publican mediante replicación transaccional o replicación de mezcla.  
  
 En el caso de las tablas con una o más de estas características, utilice la instrucción DELETE.  
  
 TRUNCATE TABLE no puede activar un desencadenador porque la operación no registra eliminaciones de filas individuales. Para obtener más información, vea [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md). 
 
 En [!INCLUDE[sssdwfull](../../includes/sssdwfull-md.md)] y [!INCLUDE[sspdw](../../includes/sspdw-md.md)]:

- TRUNCATE TABLE no se permite en la instrucción de explicación.

- TRUNCATE TABLE no se debe ejecutar dentro de una transacción.
  
## <a name="truncating-large-tables"></a>Truncar tablas de gran tamaño  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tiene la capacidad de quitar o truncar las tablas que tienen más de 128 extensiones sin mantener bloqueos simultáneos en todas las extensiones necesarias para la eliminación.  
  
## <a name="permissions"></a>Permissions  
 El permiso mínimo necesario es ALTER en *table_name*. Los permisos predeterminados de TRUNCATE TABLE son los de propietario de la tabla, los miembros del rol fijo de servidor sysadmin y los miembros de los roles fijos de base de datos db_owner y db_ddladmin, y no son transferibles. No obstante, puede incorporar la instrucción TRUNCATE TABLE en un módulo, por ejemplo un procedimiento almacenado, y conceder los permisos correspondientes al módulo mediante la cláusula EXECUTE AS.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-truncate-a-table"></a>A. Truncar una tabla  
 En el siguiente ejemplo se quitan todos los datos de la tabla `JobCandidate`. Se incluyen instrucciones `SELECT` antes y después de la instrucción `TRUNCATE TABLE` para comparar los resultados.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT COUNT(*) AS BeforeTruncateCount   
FROM HumanResources.JobCandidate;  
GO  
TRUNCATE TABLE HumanResources.JobCandidate;  
GO  
SELECT COUNT(*) AS AfterTruncateCount   
FROM HumanResources.JobCandidate;  
GO  
```  
  
### <a name="b-truncate-table-partitions"></a>B. Truncar la tabla de particiones  
  
**Se aplica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a través de [versión actual](http://go.microsoft.com/fwlink/p/?LinkId=299658))
  
 En el ejemplo siguiente se trunca las particiones especificadas de una tabla con particiones. La sintaxis de `WITH (PARTITIONS (2, 4, 6 TO 8))` provoca que los números de partición 2, 4, 6, 7 y 8 se trunquen.  
  
```  
TRUNCATE TABLE PartitionTable1   
WITH (PARTITIONS (2, 4, 6 TO 8));  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [Eliminar tabla &#40; Transact-SQL &#41;](../../t-sql/statements/drop-table-transact-sql.md)   
 [IDENTITY &#40;propiedad de Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql-identity-property.md)  
  
  


