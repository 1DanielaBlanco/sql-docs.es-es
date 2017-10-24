---
title: DATALENGTH (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATALENGTH_TSQL
- DATALENGTH
dev_langs:
- TSQL
helpviewer_keywords:
- number of bytes representing expression
- data types [SQL Server], length
- DATALENGTH function
- expressions [SQL Server], length
- lengths [SQL Server], data
ms.assetid: 00f377f1-cc3e-4eac-be47-b3e3f80267c9
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: d8887c50cb482e27bce63e08aa18b8ca54616faa
ms.contentlocale: es-es
ms.lasthandoff: 10/17/2017

---
# <a name="datalength-transact-sql"></a>DATALENGTH (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Devuelve el número de bytes utilizados para representar cualquier expresión.
  
![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintaxis  
  
```sql
DATALENGTH ( expression )   
```  
  
## <a name="arguments"></a>Argumentos  
*expression*  
Es un [expresión](../../t-sql/language-elements/expressions-transact-sql.md) de cualquier tipo de datos.
  
## <a name="return-types"></a>Tipos de valor devuelto
**bigint** si *expresión* reviste la **varchar (max)**, **nvarchar (max)** o **varbinary (max)** tipos de datos; en caso contrario, **int**.
  
## <a name="remarks"></a>Comentarios  
DATALENGTH es especialmente útil con **varchar**, **varbinary**, **texto**, **imagen**, **nvarchar**, y **ntext** tipos de datos porque estos tipos de datos pueden almacenar datos de longitud variable.
  
DATALENGTH de NULL es NULL.
  
> [!NOTE]  
>  Los niveles de compatibilidad pueden afectar a los valores devueltos. Para obtener más información sobre los niveles de compatibilidad, vea [Nivel de compatibilidad de ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
## <a name="examples"></a>Ejemplos  
En el siguiente ejemplo se busca la longitud de la columna `Name` de la tabla `Product`.
  
```sql
-- Uses AdventureWorks  
  
SELECT length = DATALENGTH(EnglishProductName), EnglishProductName  
FROM dbo.DimProduct  
ORDER BY EnglishProductName;  
GO  
```  
  
## <a name="see-also"></a>Vea también
[LEN &#40; Transact-SQL &#41;](../../t-sql/functions/len-transact-sql.md)  
[CAST y CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Tipos de datos &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[Funciones del sistema &#40; Transact-SQL &#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)
  
  


