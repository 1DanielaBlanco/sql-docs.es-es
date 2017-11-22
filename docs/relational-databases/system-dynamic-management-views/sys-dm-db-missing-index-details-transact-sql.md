---
title: Sys.dm_db_missing_index_details (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_db_missing_index_details
- dm_db_missing_index_details
- sys.dm_db_missing_index_details_TSQL
- dm_db_missing_index_details_TSQL
dev_langs: TSQL
helpviewer_keywords:
- missing indexes feature [SQL Server], sys.dm_db_missing_index_details dynamic management view
- sys.dm_db_missing_index_details dynamic management view
ms.assetid: ced484ae-7c17-4613-a3f9-6d8aba65a110
caps.latest.revision: "37"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 9c23f2c1d045b50261abd067c7c6860972b433aa
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmdbmissingindexdetails-transact-sql"></a>sys.dm_db_missing_index_details (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Devuelve información detallada sobre los índices que faltan, excluidos los índices espaciales.  
  
 En [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], las vistas de administración dinámica no pueden exponer información que impactaría a la contención de la base de datos ni acerca de otras bases de datos a las que el usuario tenga acceso. Para evitar exponer esta información, cada fila que contiene datos que no pertenecen al inquilino conectado se filtra.  

  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**index_handle**|**int**|Identifica un índice que falta específico. El identificador es único en todo el servidor. **index_handle** es la clave de esta tabla.|  
|**database_id**|**smallint**|Identifica la base de datos en la que reside la tabla en la que falta un índice.|  
|**object_id**|**int**|Identifica la tabla en la que falta el índice.|  
|**equality_columns**|**nvarchar(4000)**|Lista de columnas separadas por comas que contribuyen a predicados de igualdad de la forma:<br /><br /> *Table.Column* =*constant_value*|  
|**inequality_columns**|**nvarchar(4000)**|Lista de columnas separadas por comas que contribuyen a predicados de desigualdad; por ejemplo, a predicados de la forma:<br /><br /> *Table.Column* > *constant_value*<br /><br /> Cualquier operador de comparación distinto de "=" expresa desigualdad.|  
|**included_columns**|**nvarchar(4000)**|Lista de columnas de cobertura separadas por comas requeridas por la consulta. Para obtener más información acerca de la cobertura o las columnas incluidas, vea [crear índices con columnas incluidas](../../relational-databases/indexes/create-indexes-with-included-columns.md).<br /><br /> Para los índices con optimización para memoria (tanto hash con optimización para memoria no agrupado), omitir **included_columns**. Todas las columnas de la tabla se incluyen en cada índice optimizado para memoria.|  
|**instrucción**|**nvarchar(4000)**|Nombre de la tabla en la que falta el índice.|  
  
## <a name="remarks"></a>Comentarios  
 Información devuelta por **sys.dm_db_missing_index_details** se actualiza cuando una consulta está optimizada por el optimizador de consultas y no se conserva. La información sobre índices que faltan solo se conserva hasta que se reinicia [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Los administradores de bases de datos deben realizar copias de seguridad de forma periódica de la información de índices que faltan si desean conservarla después de reciclar el servidor.  
  
 Para determinar qué índices que faltan los grupos que falta un índice determinado forma parte de, puede consultar la **sys.dm_db_missing_index_groups** vista de administración dinámica por una combinación de igualdad con **sys.dm_db_missing_index_details**  tomando como base la **index_handle** columna.  
  
## <a name="using-missing-index-information-in-create-index-statements"></a>Utilizar información de índices que faltan en instrucciones CREATE INDEX  
 Para convertir la información devuelta por **sys.dm_db_missing_index_details** en una instrucción CREATE INDEX para los índices basados en disco y con optimización para memoria, deben colocar las columnas de igualdad antes de las columnas de desigualdad y juntos deben formar la clave del índice. Las columnas incluidas deben agregarse a la instrucción CREATE INDEX mediante la cláusula INCLUDE. Para determinar un orden efectivo para las columnas de igualdad, ordénelas en función de su selectividad, mostrando primero las columnas más selectivas (en la parte izquierda de la lista de columnas).  
  
 Para obtener más información acerca de los índices con optimización para memoria, vea [índices para tablas con optimización para memoria](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md).  
  
## <a name="transaction-consistency"></a>Coherencia de las transacciones  
 Si una transacción crea o quita una tabla, las filas que contienen información de índices que faltan sobre los objetos quitados se eliminan de este objeto de administración dinámica para mantener la coherencia de la transacción.  
  
## <a name="permissions"></a>Permissions  
En [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], requiere `VIEW SERVER STATE` permiso.   
En [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] niveles de Premium, requieren la `VIEW DATABASE STATE` permiso en la base de datos. En [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] niveles estándar y básico, requiere la **administrador del servidor** o un **Administrador de Azure Active Directory** cuenta.  
  
## <a name="see-also"></a>Vea también  
 [Sys.dm_db_missing_index_columns &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-columns-transact-sql.md)   
 [Sys.dm_db_missing_index_groups &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-groups-transact-sql.md)   
 [Sys.dm_db_missing_index_group_stats &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-group-stats-transact-sql.md)  
  
  
