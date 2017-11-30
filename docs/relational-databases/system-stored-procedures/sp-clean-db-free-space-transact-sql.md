---
title: sp_clean_db_free_space (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_clean_db_free_space_TSQL
- sp_clean_db_free_space
dev_langs: TSQL
helpviewer_keywords:
- sp_clean_db_free_space
- ghost records
ms.assetid: faa96f7e-be92-47b1-8bc5-4dbba5331655
caps.latest.revision: "12"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 28035865fa180e9b1e379a0fbb3843956e162ccf
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/27/2017
---
# <a name="spcleandbfreespace-transact-sql"></a>sp_clean_db_free_space (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Quita la información residual que queda en las páginas de base de datos a causa de las rutinas de modificación de datos en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. sp_clean_db_free_space limpia todas las páginas en todos los archivos de la base de datos.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_clean_db_free_space   
[ @dbname ] = 'database_name'   
[ , [ @cleaning_delay = ] 'delay_in_seconds' ] [;]  
```  
  
## <a name="arguments"></a>Argumentos  
 [ @dbname=] '*database_name*'  
 Es el nombre de la base de datos que se va a limpiar. *dbname* es **sysname** y no puede ser NULL.  
  
 [ @cleaning_delay=] '*retraso_en_segundos*'  
 Especifica un intervalo de retardo entre la limpieza de páginas. Esto ayuda a reducir el efecto en el sistema de E/S. *retraso_en_segundos* es **int** con un valor predeterminado es 0.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 0 (correcto) o 1 (error)  
  
## <a name="remarks"></a>Comentarios  
 Operaciones de eliminación de una tabla o las operaciones de actualización que hacen que una fila que se va a mover puede liberar inmediatamente espacio en una página quitando las referencias a la fila. Sin embargo, en determinadas circunstancias, la fila puede permanecer físicamente en la página de datos como un registro fantasma. Los registros fantasma se quitan periódicamente mediante un proceso en segundo plano. No devuelve estos datos residuales el [!INCLUDE[ssDE](../../includes/ssde-md.md)] en respuesta a consultas. Sin embargo, en entornos en los que la seguridad física de los datos o de los archivos de copia de seguridad corre un riesgo, puede utilizar sp_clean_db_free_space para limpiar estos registros fantasma.  
  
 El período de tiempo necesario para ejecutar sp_clean_db_free_space depende del tamaño del archivo, del espacio disponible y de la capacidad del disco. Dado que la ejecución de sp_clean_db_free_space puede afectar significativamente a la actividad de E/S, se recomienda ejecutar este procedimiento fuera del horario de funcionamiento habitual.  
  
 Antes de ejecutar sp_clean_db_free_space es aconsejable crear una copia de seguridad completa de la base de datos.  
  
 Relacionado [sp_clean_db_file_free_space](../../relational-databases/system-stored-procedures/sp-clean-db-file-free-space-transact-sql.md) procedimiento almacenado puede limpiar un único archivo.  
  
## <a name="permissions"></a>Permissions  
 Debe pertenecer al rol de la base de datos db_owner.  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se limpia toda la información residual de la base de datos `AdventureWorks2012`.  
  
```  
USE master;  
GO  
EXEC sp_clean_db_free_space   
@dbname = N'AdventureWorks2012' ;  
```  
  
## <a name="see-also"></a>Vea también  
 [Motor de base de datos almacenados procedimientos &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)  
  
  
