---
title: TIMEFROMPARTS (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TIMEFROMPARTS_TSQL
- TIMEFROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- TIMEFROMPARTS function
ms.assetid: 786c65a1-2b3f-4e4b-82b6-4940d62f3801
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 5e046e203e7ebd5243cdfc6f10948dfd353b2dd3
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2018
---
# <a name="timefromparts-transact-sql"></a>TIMEFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Devuelve un **tiempo** valor durante el tiempo especificado y con la precisión especificada.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
TIMEFROMPARTS ( hour, minute, seconds, fractions, precision )  
```  
  
## <a name="arguments"></a>Argumentos  
 *hora*  
 Expresión entera que especifica horas.  
  
 *minuto*  
 Expresión entera que especifica minutos.  
  
 *segundos*  
 Expresión entera que especifica segundos.  
  
 *fracciones*  
 Expresión entera que especifica fracciones.  
  
 *precisión*  
 Literal entero que especifica la precisión de la **tiempo** valor va a devolver.  
  
## <a name="return-types"></a>Tipos devueltos  
 **tiempo (** *precisión* **)**  
  
## <a name="remarks"></a>Comentarios  
 TIMEROMPARTS devuelve un valor de hora totalmente inicializado. Si los argumentos no son válidos, se generará un error. Si alguno de los parámetros es NULL, se devuelve NULL. Sin embargo, si la *precisión* del argumento es null, a continuación, se produce un error.  
  
 El *fracciones* argumento depende el *precisión* argumento. Por ejemplo, si *precisión* es 7, a continuación, cada fracción representa 100 nanosegundos; si *precisión* es 3, cada fracción representa un milisegundo. Si el valor de *precisión* es cero, el valor de *fracciones* también debe ser cero; en caso contrario, se produce un error.  
  
 Esta función se puede enviar de forma remota a servidores [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] y posteriores. No se puede enviar de forma remota a servidores que tengan una versión inferior a[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-simple-example-without-fractions-of-a-second"></a>A. Ejemplo simple sin fracciones de segundo  
  
```  
SELECT TIMEFROMPARTS ( 23, 59, 59, 0, 0 ) AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
--------------------  
23:59:59.0000000  
  
(1 row(s) affected)  
```  
  
### <a name="b-example-with-fractions-of-a-second"></a>B. Ejemplo con fracciones de segundo  
 En el ejemplo siguiente se muestra el uso de la *fracciones* y *precisión* parámetros:  
  
1.  Cuando *fracciones* tiene un valor de 5 y *precisión* tiene un valor de 1, a continuación, el valor de *fracciones* representa 5/10 de un segundo.  
  
2.  Cuando *fracciones* tiene un valor de 50 y *precisión* tiene un valor de 2, a continuación, el valor de *fracciones* representa 50/100 de un segundo.  
  
3.  Cuando *fracciones* tiene un valor de 500 y *precisión* tiene un valor de 3, a continuación, el valor de *fracciones* representa 500/1000 de un segundo.  
  
```sql  
SELECT TIMEFROMPARTS ( 14, 23, 44, 5, 1 );  
SELECT TIMEFROMPARTS ( 14, 23, 44, 50, 2 );  
SELECT TIMEFROMPARTS ( 14, 23, 44, 500, 3 );  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------------  
14:23:44.5  
  
(1 row(s) affected)  
  
----------------  
14:23:44.50  
  
(1 row(s) affected)  
  
----------------  
14:23:44.500  
  
(1 row(s) affected)  
```  
  

