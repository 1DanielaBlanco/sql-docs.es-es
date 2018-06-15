---
title: sp_updatestats (Transact-SQL) | Documentos de Microsoft
ms.custom: ''
ms.date: 09/25/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_updatestats_TSQL
- sp_updatestats
dev_langs:
- TSQL
helpviewer_keywords:
- sp_updatestats
ms.assetid: 01184651-6e61-45d9-a502-366fecca0ee4
caps.latest.revision: 45
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 895c3fd65ac6cad3a0ce67dee54cfe8cf1070ea4
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33259475"
---
# <a name="spupdatestats-transact-sql"></a>sp_updatestats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Ejecuta UPDATE STATISTICS para todas las tablas internas y definidas por el usuario de la base de datos actual.  
  
 Para obtener más información acerca de UPDATE STATISTICS, vea [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md). Para obtener más información acerca de las estadísticas, vea [estadísticas](../../relational-databases/statistics/statistics.md).  
    
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_updatestats [ [ @resample = ] 'resample']  
```  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 0 (correcto) o 1 (error)  
  
## <a name="arguments"></a>Argumentos  
 [ **@resample** =] **'resample'**  
 Especifica que **sp_updatestats** utilizará la opción RESAMPLE de la [UPDATE STATISTICS](../../t-sql/statements/update-statistics-transact-sql.md) instrucción. Si **'resample'** no se especifica, **sp_updatestats** actualiza las estadísticas mediante el muestreo predeterminado. **volver a muestrear** es **varchar (8)** con un valor predeterminado de NO.  
  
## <a name="remarks"></a>Comentarios  
 **sp_updatestats** ejecuta UPDATE STATISTICS, especificando la palabra clave ALL en todas las tablas internas y definidas por el usuario en la base de datos. sp_updatestats muestra mensajes que indican su progreso. Cuando la actualización se ha completado, informa de que se han actualizado las estadísticas de todas las tablas.  
  
 sp_updatestats actualiza las estadísticas en índices no clúster deshabilitados y no actualiza las estadísticas en índices clúster deshabilitados.  
  
 Para las tablas basadas en disco, **sp_updatestats** actualiza las estadísticas basándose en el **modification_counter** información en el **sys.dm_db_stats_properties** vista de catálogo Actualizar estadísticas donde se ha modificado al menos una fila. Las estadísticas en tablas optimizadas en memoria se actualizan siempre al ejecutar **sp_updatestats**. Por lo tanto, no se ejecutan **sp_updatestats** más de lo necesario.  
  
 **sp_updatestats** puede desencadenar una regeneración de procedimientos almacenados u otro código compilado. Sin embargo, **sp_updatestats** podría desencadenar una regeneración si solo un plan de consulta es posible que las tablas de referencia y los índices en ellos. En estos casos sería necesaria una recompilación, aunque las estadísticas estén actualizadas.  
  
 Para las bases de datos con un nivel de compatibilidad inferior a 90, ejecutar **sp_updatestats** no conserva la configuración más reciente de NORECOMPUTE para estadísticas específicas. Para las bases de datos con un nivel de compatibilidad de 90 o superior, sp_updatestats conserva la más reciente de NORECOMPUTE para estadísticas específicas. Para obtener más información sobre cómo deshabilitar y volver a habilitar las actualizaciones de estadísticas, vea [Estadísticas](../../relational-databases/statistics/statistics.md).  
  
## <a name="permissions"></a>Permissions  
 Debe pertenecer a la **sysadmin** rol fijo de servidor o la propiedad de la base de datos (**dbo**).  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se actualizan las estadísticas de las tablas de la base de datos [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_updatestats;   
```  
  
## <a name="see-also"></a>Vea también  
 [Opciones de ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md)   
 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [DROP STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/drop-statistics-transact-sql.md)   
 [sp_autostats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-autostats-transact-sql.md)   
 [sp_createstats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-createstats-transact-sql.md)   
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)   
 [Procedimientos almacenados del sistema](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
