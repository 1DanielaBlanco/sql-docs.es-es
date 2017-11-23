---
title: sp_help_fulltext_columns_cursor (Transact-SQL) | Documentos de Microsoft
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
- sp_help_fulltext_columns_cursor
- sp_help_fulltext_columns_cursor_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_help_fulltext_columns_cursor
ms.assetid: 26054e76-53b7-4004-8d48-92ba3435e9d7
caps.latest.revision: "28"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cd12180fc4c5c4a923c8a89b5a204468072d94bd
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="sphelpfulltextcolumnscursor-transact-sql"></a>sp_help_fulltext_columns_cursor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Utiliza un cursor para devolver las columnas designadas para la indización de texto completo.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Use la [sys.fulltext_index_columns](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md) vista de catálogo en su lugar.  
  
||  
|-|  
|**Se aplica a:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] hasta la [versión actual](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].|  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_help_fulltext_columns_cursor [ @cursor_return = ] @cursor_variable OUTPUT   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @column_name = ] 'column_name' ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@cursor_return =**]  *@cursor_variable*  SALIDA  
 Es la variable de salida de tipo **cursor**. El cursor resultante es desplazable, dinámico y de solo lectura.  
  
 [  **@table_name =**] **'***table_name***'**  
 Es el nombre de tabla de una o dos partes para la que se solicita información de índice de texto completo. *table_name* es **nvarchar (517)**, su valor predeterminado es null. Si *table_name* se omite, se recupera información de la columna de índice de texto completo para cada tabla indizada de texto completo.  
  
 [  **@column_name =**] **'***column_name***'**  
 Es el nombre de la columna cuyos metadatos de índice de texto completo se desean. *column_name* es **sysname** con un valor predeterminado es NULL. Si *column_name* se omite o es NULL, se devuelve información de columna de texto completo para cada columna de índice de texto completo de *table_name*. Si *table_name* también se omite o es NULL, se devuelve información de columna de índice de texto completo para cada columna de índice de texto completo de todas las tablas de la base de datos.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 0 (correcto) o 1 (error)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_OWNER**|**sysname**|Propietario de la tabla. Es el nombre del usuario de la base de datos que ha creado la tabla.|  
|**TABLE_ID**|**int**|Id. de la tabla.|  
|**TABLE_NAME**|**sysname**|Nombre de la tabla.|  
|**FULLTEXT_COLUMN_NAME**|**sysname**|Columna de una tabla con índice de texto completo que está designada para su indización.|  
|**FULLTEXT_COLID**|**int**|Id. de columna de la columna de índice de texto completo.|  
|**FULLTEXT_BLOBTP_COLNAME**|**sysname**|Columna de una tabla con índice de texto completo que especifica el tipo de documento de la columna de índice de texto completo. Este valor solo es aplicable cuando la columna indizada de texto completo es un **varbinary (max)** o **imagen** columna.|  
|**FULLTEXT_BLOBTP_COLID**|**int**|Id. de la columna de tipo de documento. Este valor solo es aplicable cuando la columna indizada de texto completo es un **varbinary (max)** o **imagen** columna.|  
|**FULLTEXT_LANGUAGE**|**sysname**|Lenguaje utilizado para la búsqueda de texto completo de la columna.|  
  
## <a name="permissions"></a>Permissions  
 De forma predeterminada, los permisos de ejecución corresponden a los miembros del rol **public** .  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se devuelve información acerca de las columnas que se han designado para la indización de texto completo en todas las tablas de la base de datos.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @mycursor CURSOR;  
EXEC sp_help_fulltext_columns_cursor @mycursor OUTPUT  
FETCH NEXT FROM @mycursor;  
WHILE (@@FETCH_STATUS <> -1)  
   BEGIN  
      FETCH NEXT FROM @mycursor;  
   END;  
CLOSE @mycursor;  
DEALLOCATE @mycursor;  
GO   
```  
  
## <a name="see-also"></a>Vea también  
 [COLUMNPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/columnproperty-transact-sql.md)   
 [sp_fulltext_column &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-fulltext-column-transact-sql.md)   
 [sp_help_fulltext_columns &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-columns-transact-sql.md)   
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
