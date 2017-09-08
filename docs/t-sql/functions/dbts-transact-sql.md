---
title: '@@DBTS (Transact-SQL) | Documentos de Microsoft'
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@DBTS_TSQL'
- '@@DBTS'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@DBTS function'
- timestamp data type
ms.assetid: 91842ddd-91c0-4445-a03f-116f6bc991d0
caps.latest.revision: 35
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f044c71018186baaf2bd5c27076b78aae139b34f
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="dbts-transact-sql"></a>@@DBTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Devuelve el valor del tipo de datos **timestamp** actual de la base de datos actual. Se garantiza que la marca de tiempo es única en la base de datos.
  
![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintaxis  
  
```sql
@@DBTS  
```  
  
## <a name="return-types"></a>Tipos de valor devuelto
**varbinary**
  
## <a name="remarks"></a>Comentarios  
@@DBTS devuelve el valor de marca de tiempo utilizó por última vez de la base de datos actual. Se genera un nuevo valor de marca de tiempo cuando se inserta o actualiza una fila con una columna de tipo **timestamp** .
  
El @@DBTS función no se ve afectada por los cambios en los niveles de aislamiento de transacción.
  
## <a name="examples"></a>Ejemplos  
En el ejemplo siguiente se devuelve el valor actual **timestamp** desde el [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] base de datos.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT @@DBTS;  
```  
  
## <a name="see-also"></a>Vea también
[Funciones de configuración &#40; Transact-SQL &#41;](../../t-sql/functions/configuration-functions-transact-sql.md)  
[Simultaneidad de cursor &#40; ODBC &#41;](../../relational-databases/native-client-odbc-cursors/properties/cursor-concurrency-odbc.md)  
[Tipos de datos &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[MIN_ACTIVE_ROWVERSION &#40; Transact-SQL &#41;](../../t-sql/functions/min-active-rowversion-transact-sql.md)
  
  

