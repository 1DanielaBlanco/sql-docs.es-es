---
title: sp_column_privileges_ex (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_column_privileges_ex
- sp_column_privileges_ex_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_column_privileges_ex
ms.assetid: 98cb6e58-4007-40fc-b048-449fb2e7e6be
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1f374a87fe41d08774eca9bd0e90de42d5204cbe
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/27/2017
---
# <a name="spcolumnprivilegesex-transact-sql"></a>sp_column_privileges_ex (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve privilegios de columna para la tabla especificada del servidor vinculado indicado.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_column_privileges_ex [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]   
     [ , [ @table_catalog = ] 'table_catalog' ]   
     [ , [ @column_name = ] 'column_name' ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@table_server =** ] **'***table_server***'**  
 Es el nombre del servidor vinculado para el que se devuelve información. *table_server* es **sysname**, no tiene ningún valor predeterminado.  
  
 [  **@table_name =** ] **'***table_name***'**  
 Es el nombre de la tabla que contiene la columna especificada. *table_name* es **sysname**, su valor predeterminado es null.  
  
 [  **@table_schema =** ] **'***table_schema***'**  
 Es el esquema de la tabla. *TABLE_SCHEMA* es **sysname**, su valor predeterminado es null.  
  
 [  **@table_catalog =** ] **'***table_catalog***'**  
 Es el nombre de la base de datos en el que el especificado *table_name* reside. *TABLE_CATALOG* es **sysname**, su valor predeterminado es null.  
  
 [  **@column_name =** ] **'***column_name***'**  
 Es el nombre de la columna para la que se va a proporcionar información acerca de los privilegios. *column_name* es **sysname**, su valor predeterminado es null (común para todos).  
  
## <a name="result-sets"></a>Conjuntos de resultados  
 En la siguiente tabla se muestran las columnas del conjunto de resultados. Los resultados devueltos se ordenan por **TABLE_QUALIFIER**, **TABLE_OWNER**, **TABLE_NAME**, **COLUMN_NAME**, y  **PRIVILEGIO**.  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|Nombre del calificador de tabla. Varios productos DBMS admiten nombres de tres partes para tablas (*calificador***.** *propietario***.** *nombre*). En [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], esta columna representa el nombre de la base de datos. En algunos productos, representa el nombre del servidor del entorno de base de datos de la tabla. Este campo puede ser NULL.|  
|**SEGÚN TABLE_SCHEM**|**sysname**|Nombre de propietario de la tabla. En [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], esta columna representa el nombre de usuario de base de datos que creó la tabla. Este campo siempre devuelve un valor.|  
|**TABLE_NAME**|**sysname**|Nombre de la tabla. Este campo siempre devuelve un valor.|  
|**COLUMN_NAME**|**sysname**|Nombre de columna para cada columna de la **TABLE_NAME** devuelto. Este campo siempre devuelve un valor.|  
|**OTORGANTE DE PERMISOS**|**sysname**|Nombre de usuario de base de datos que ha concedido permisos en el objeto **COLUMN_NAME** a la lista **receptor**. En [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], esta columna siempre es el mismo que el **TABLE_OWNER**. Este campo siempre devuelve un valor.<br /><br /> El **otorgante de permisos** columna puede ser el propietario de base de datos (**TABLE_OWNER**) o un usuario a los que el propietario de la base de datos concedido permisos mediante la cláusula WITH GRANT OPTION en la instrucción GRANT.|  
|**RECEPTOR**|**sysname**|Nombre de usuario de base de datos que se ha concedido permisos en el objeto **COLUMN_NAME** la **otorgante de permisos**. Este campo siempre devuelve un valor.|  
|**CON PRIVILEGIOS**|**varchar (**32**)**|Uno de los permisos de columna disponibles. Los permisos de columna pueden ser uno de los valores siguientes (u otros valores compatibles con el origen de datos cuando se define la implementación):<br /><br /> Seleccione = **receptor** puede recuperar datos de las columnas.<br /><br /> INSERT = **receptor** puede proporcionar datos para esta columna cuando se inserten nuevas filas (por la **receptor**) en la tabla.<br /><br /> UPDATE = **receptor** puede modificar datos existentes en la columna.<br /><br /> REFERENCIAS = **receptor** puede hacer referencia a una columna de una tabla externa en una relación de clave principal/clave externa. Las relaciones entre clave principal y clave externa se definen con restricciones de tabla.|  
|**IS_GRANTABLE**|**varchar (**3**)**|Indica si la **receptor** permiten conceder permisos a otros usuarios (a menudo se conoce como el permiso "conceder por concesión"). Puede ser YES, NO o NULL. Un valor desconocido, o NULL, hace referencia a un origen de datos en el que no se aplica “conceder por concesión”.|  
  
## <a name="permissions"></a>Permissions  
 Es necesario contar con un permiso de tipo SELECT sobre el esquema.  
  
## <a name="examples"></a>Ejemplos  
 En el siguiente ejemplo se devuelve información de privilegios de columna de la tabla `HumanResources.Department` de la base de datos [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] del servidor vinculado `Seattle1`.  
  
```  
EXEC sp_column_privileges_ex @table_server = 'Seattle1',   
   @table_name = 'Department',   
   @table_schema = 'HumanResources',  
   @table_catalog ='AdventureWorks2012';  
```  
  
## <a name="see-also"></a>Vea también  
 [sp_table_privileges_ex &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-ex-transact-sql.md)   
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
