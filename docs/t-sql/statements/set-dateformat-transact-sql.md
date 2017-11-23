---
title: SET DATEFORMAT (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATEFORMAT
- SET DATEFORMAT
- SET_DATEFORMAT_TSQL
- DATEFORMAT_TSQL
dev_langs: TSQL
helpviewer_keywords:
- dates [SQL Server], formats
- dates [SQL Server], ordering date parts
- SET DATEFORMAT option [SQL Server]
- DATEFORMAT option [SQL Server]
- date and time [SQL Server], SET DATEFORMAT
- options [SQL Server], date
- date and time [SQL Server], DATEFORMAT
- dateparts [SQL Server], dateformat
ms.assetid: da217878-7ec4-477e-aa13-604073c948f8
caps.latest.revision: "49"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 3b1e233508eaedab627b57a3ce6938b90a9e196d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="set-dateformat-transact-sql"></a>SET DATEFORMAT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Establece el orden de las partes de fecha del mes, día y año para interpretar **fecha**, **smalldatetime**, **datetime**, **datetime2** y **datetimeoffset** cadenas de caracteres.  
  
 Para obtener información general de todos los [!INCLUDE[tsql](../../includes/tsql-md.md)] tipos de datos de fecha y hora y funciones, vea [funciones y tipos de datos de hora y fecha &#40; Transact-SQL &#41; ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
SET DATEFORMAT { format | @format_var }   
```  
  
## <a name="arguments"></a>Argumentos  
 *formato* | **@***format_var*  
 Es el orden de las partes de la fecha. Parámetros válidos son **mdy**, **DMA**, **AMD**, **adm**, **MAD**, y **DAM**. Puede ser Unicode o juegos de caracteres de doble byte (DBCS) convertidos a Unicode. El valor predeterminado para inglés Valor predeterminado para inglés **mdy**. Para DATEFORMAT predeterminado de todos los lenguajes admitidos, vea [sp_helplanguage &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-helplanguage-transact-sql.md).  
  
## <a name="remarks"></a>Comentarios  
 El DATEFORMAT **adm** no se admite para **fecha**, **datetime2** y **datetimeoffset** tipos de datos.  
  
 El efecto de la configuración DATEFORMAT en la interpretación de cadenas de caracteres que pueden ser diferente **datetime** y **smalldatetime** valores **fecha**, **datetime2** y **datetimeoffset** valores, según el formato de cadena. Esta configuración de idioma afecta a la interpretación de cadenas de caracteres cuando se convierten en valores de fecha para el almacenamiento en la base de datos. No afecta a la presentación de valores de tipo de datos de fecha que se almacenan en el formato de base de datos o de almacenamiento.  
  
 Algunos formatos de cadenas de caracteres, por ejemplo ISO 8601, se interpretan independientemente del valor DATEFORMAT.  
  
 La opción SET DATEFORMAT se establece en tiempo de ejecución, no en tiempo de análisis.  
  
 SET DATEFORMAT anula la fecha implícita de configuración de formato [SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Debe pertenecer al rol **public** .  
  
## <a name="examples"></a>Ejemplos  
 El ejemplo siguiente utiliza cadenas de fecha diferentes como entradas en sesiones con el mismo valor `DATEFORMAT`.  
  
```  
-- Set date format to day/month/year.  
SET DATEFORMAT dmy;  
GO  
DECLARE @datevar datetime2 = '31/12/2008 09:01:01.1234567';  
SELECT @datevar;  
GO  
-- Result: 2008-12-31 09:01:01.123  
SET DATEFORMAT dmy;  
GO  
DECLARE @datevar datetime2 = '12/31/2008 09:01:01.1234567';  
SELECT @datevar;  
GO  
-- Result: Msg 241: Conversion failed when converting date and/or time -- from character string.  
  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [Instrucciones SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  

