---
title: SMALLDATETIMEFROMPARTS (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SMALLDATETIMEFROMPARTS
- SMALLDATETIMEFROMPARTS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SMALLDATETIMEFROMPARTS function
ms.assetid: 7467fdab-e588-419c-9e29-42caec34a9ea
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 90be7b0ad4f7fcc7677f820e374705636891d458
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="smalldatetimefromparts-transact-sql"></a>SMALLDATETIMEFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Devuelve un **smalldatetime** valor para la fecha y hora especificadas.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
SMALLDATETIMEFROMPARTS ( year, month, day, hour, minute )  
```  
  
## <a name="arguments"></a>Argumentos  
 *año*  
 Expresión entera que especifica un año.  
  
 *mes*  
 Expresión entera que especifica un mes.  
  
 *día*  
 Expresión entera que especifica un día.  
  
 *hora*  
 Expresión entera que especifica horas.  
  
 *minuto*  
 Expresión entera que especifica minutos.  
  
## <a name="return-types"></a>Tipos devueltos  
 **smalldatetime**  
  
## <a name="remarks"></a>Comentarios  
 Esta función actúa como un constructor para una totalmente inicializado **smalldatetime** valor. Si los argumentos no son válidos, se produce un error. Si los argumentos necesarios son NULL, se devuelve un valor NULL.  
  
 Esta función se puede enviar de forma remota a servidores de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y superiores. No se puede enviar de forma remota a servidores que tengan una versión inferior a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="examples"></a>Ejemplos  
  
```  
SELECT SMALLDATETIMEFROMPARTS ( 2010, 12, 31, 23, 59 ) AS Result  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
---------------------------  
2011-01-01 00:00:00  
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Ejemplos: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] y[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
```  
SELECT SMALLDATETIMEFROMPARTS ( 2010, 12, 31, 23, 59 ) AS Result  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
---------------------------  
2011-01-01 00:00:00  
  
(1 row(s) affected)  
```  
  
  


