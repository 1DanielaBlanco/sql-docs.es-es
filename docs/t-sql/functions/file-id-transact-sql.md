---
title: File_ID (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FILE_ID
- FILE_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IDs [SQL Server], files
- file IDs [SQL Server]
- FILE_ID function
- names [SQL Server], files
- identification numbers [SQL Server], files
- file names [SQL Server], FILE_ID
ms.assetid: 6a7382cf-a360-4d62-b9d2-5d747f56f076
caps.latest.revision: 34
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2544da5cb252b27f42a82e1fa400d7c28f503f20
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="fileid-transact-sql"></a>FILE_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve el número de identificación del archivo (Id.) del nombre de archivo lógico dado de la base de datos actual.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Use [FILE_IDEX](../../t-sql/functions/file-idex-transact-sql.md) en su lugar.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
FILE_ID ( file_name )  
```  
  
## <a name="arguments"></a>Argumentos  
 *file_name*  
 Es una expresión de tipo **sysname** que representa el nombre del archivo para el que se va a devolver el identificador de archivo.  
  
## <a name="return-types"></a>Tipos devueltos  
 **smallint**  
  
## <a name="remarks"></a>Comentarios  
 *file_name* se corresponde con el nombre de archivo lógico mostrado en la columna de nombre de las vistas de catálogo sys.master_files o sys.database_files.  
  
 En [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], el número de identificación de archivo asignado a los catálogos de texto completo es mayor que 32767. Dado que el tipo de valor devuelto de la función FILE_ID es **smallint**, esta función no se puede usar para archivos de texto completo. Use [FILE_IDEX](../../t-sql/functions/file-idex-transact-sql.md) en su lugar.  
  
## <a name="examples"></a>Ejemplos  
 El siguiente ejemplo devuelve el Id. de archivo para el archivo `AdventureWorks_Data`.  
  
```tsql  
USE AdventureWorks2012;  
GO  
SELECT FILE_ID('AdventureWorks2012_Data')AS 'File ID';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
File ID   
-------   
1  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vea también  
 [Características desusadas del motor de base de datos de SQL Server 2016](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)   
 [File_name &#40; Transact-SQL &#41;](../../t-sql/functions/file-name-transact-sql.md)   
 [Funciones de metadatos &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  
