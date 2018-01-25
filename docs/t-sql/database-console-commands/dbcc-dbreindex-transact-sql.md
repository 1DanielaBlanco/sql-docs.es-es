---
title: DBCC DBREINDEX (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DBCC DBREINDEX
- DBREINDEX_TSQL
- DBREINDEX
- DBCC_DBREINDEX_TSQL
dev_langs: TSQL
helpviewer_keywords:
- index rebuilding [SQL Server]
- rebuilding indexes
- dynamic index rebuilding [SQL Server]
- DBCC DBREINDEX statement
ms.assetid: 6e929d09-ccb5-4855-a6af-b616022bc8f6
caps.latest.revision: "52"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Active
ms.openlocfilehash: 991c16eea9a651270ca299e72cafbc822465a9b3
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="dbcc-dbreindex-transact-sql"></a>DBCC DBREINDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]Vuelve a generar uno o varios índices para una tabla en la base de datos especificada.
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Use [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md) en su lugar.  
  
**Se aplica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a través de [versión actual](http://go.microsoft.com/fwlink/p/?LinkId=299658))
  
![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintaxis  
  
```sql
DBCC DBREINDEX   
(   
    table_name   
    [ , index_name [ , fillfactor ] ]  
)  
    [ WITH NO_INFOMSGS ]   
```  
  
## <a name="arguments"></a>Argumentos  
 *table_name*  
 Es el nombre de la tabla que contiene los índices especificados que se van a volver a generar. Los nombres de tabla deben seguir las reglas para [identificadores](../../relational-databases/databases/database-identifiers.md)*.*  
  
 *index_name*  
 Es el nombre del índice que se va a volver a generar. Los nombres de los índices deben ajustarse a las reglas de los identificadores. Si *index_name* se especifica, *table_name* debe especificarse. Si *index_name* no se especifica o es "", se vuelven a generar todos los índices de la tabla.  
  
 *fillfactor*  
 Es el porcentaje de espacio de cada página de índice que se utiliza para almacenar los datos cuando el índice se crea o se vuelve a generar. *valor de FILLFACTOR* reemplaza el factor de relleno cuando se creó el índice, se convierta en el nuevo valor predeterminado para el índice y para cualquier otro índice no clúster vuelve a generar porque se vuelve a generar un índice agrupado.  
 Cuando *fillfactor* es 0, DBCC DBREINDEX utiliza el valor de factor de relleno para el índice de la última vez. Este valor se almacena en la **sys.indexes** vista de catálogo.   
 Si *fillfactor* se especifica, *table_name* y *index_name* debe especificarse. Si *fillfactor* no se especifica, se utiliza el factor de relleno predeterminado, 100,. Para obtener más información, vea [Especificar el factor de relleno para un índice](../../relational-databases/indexes/specify-fill-factor-for-an-index.md).  
  
 WITH NO_INFOMSGS  
 Suprime todos los mensajes informativos con niveles de gravedad entre 0 y 10.  
  
## <a name="remarks"></a>Comentarios  
DBCC DBREINDEX vuelve a generar un índice de una tabla o todos los índices definidos de una tabla. Al permitir que los índices se vuelvan a generar dinámicamente, los índices que implementen restricciones PRIMARY KEY o UNIQUE se pueden volver a generar sin tener que quitar y volver a crear las restricciones. Esto significa que un índice puede volver a generarse sin conocer la estructura de una tabla ni sus restricciones. Esto puede suceder después de copiar datos de forma masiva en la tabla.

DBCC DBREINDEX puede volver a generar todos los índices para una tabla en una instrucción. Es más sencillo que codificar varias instrucciones DROP INDEX y CREATE INDEX. Como todo el trabajo se hace con una instrucción, DBCC DBREINDEX es, automáticamente, una acción atómica, mientras que, para ser atómicas, las instrucciones DROP INDEX y CREATE INDEX individuales deben formar parte de una transacción. Además, DBCC DBREINDEX ofrece más optimizaciones que las instrucciones DROP INDEX y CREATE INDEX individuales.

A diferencia de DBCC INDEXDEFRAG o ALTER INDEX, con la opción REORGANIZE, DBCC DBREINDEX es una operación sin conexión. Si se vuelve a generar un índice no clúster, se mantiene un bloqueo compartido en la tabla en cuestión durante la operación. Esto evita que se modifique la tabla. Si el índice clúster se vuelve a generar, se mantiene un bloqueo de tabla exclusivo. Así se evita cualquier acceso a la tabla, haciendo que la tabla esté sin conexión. Utilice la instrucción ALTER INDEX REBUILD con la opción ONLINE para volver a agregar un índice en línea o para controlar el grado de paralelismo durante la operación de regeneración del índice.

Para obtener más información acerca de cómo seleccionar un método para volver a generar o reorganizar un índice, vea [reorganizar y volver a generar índices](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md) .
  
## <a name="restrictions"></a>Restricciones  
No se admite el uso de DBCC DBREINDEX en los objetos siguientes:
-   Tablas del sistema  
-   Índices espaciales  
-   índices de almacén de columnas optimizados de memoria xVelocity  
  
## <a name="result-sets"></a>Conjuntos de resultados  
A menos que se especifique NO_INFOMSGS (se debe especificar el nombre de la tabla), DBCC DBREINDEX siempre devuelve:
  
```sql
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Permissions  
Autor de la llamada debe poseer la tabla o ser miembro de la **sysadmin** rol fijo de servidor, el **db_owner** función fija de base de datos, o la **db_ddladmin** rol fijo de base de datos.
  
## <a name="examples"></a>Ejemplos  
### <a name="a-rebuilding-an-index"></a>A. Volver a generar un índice  
En este ejemplo se vuelve a generar el índice clúster `Employee_EmployeeID` con un factor de relleno de `80` en la tabla `Employee` de la base de datos `AdventureWorks`.
  
```sql  
USE AdventureWorks2012;   
GO  
DBCC DBREINDEX ('HumanResources.Employee', PK_Employee_BusinessEntityID,80);  
GO  
```  
  
### <a name="b-rebuilding-all-indexes"></a>B. Volver a generar todos los índices  
En este ejemplo se vuelven a generar todos los índices de la tabla `Employee` de `AdventureWorks` con un valor de factor de relleno de `70`.
  
```sql
USE AdventureWorks2012;   
GO  
DBCC DBREINDEX ('HumanResources.Employee', ' ', 70);  
GO  
```  
  
## <a name="see-also"></a>Vea también  
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)  
[sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)  
[ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)  
  
  

