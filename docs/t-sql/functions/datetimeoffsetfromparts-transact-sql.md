---
title: DATETIMEOFFSETFROMPARTS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DATETIMEOFFSETFROMPARTS_TSQL
- DATETIMEOFFSETFROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- DATETIMEOFFSETFROMPARTS function
ms.assetid: 463da1f4-b4b6-45a3-9a95-ea1f99575542
caps.latest.revision: 19
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 5549f258e758cc91a228d5fee707120b57963d46
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "33053135"
---
# <a name="datetimeoffsetfromparts-transact-sql"></a>DATETIMEOFFSETFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Devuelve un valor **datetimeoffset** para la fecha y la hora especificadas, y con los desplazamientos y la precisión indicados.
  
![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintaxis  
  
```sql
DATETIMEOFFSETFROMPARTS ( year, month, day, hour, minute, seconds, fractions, hour_offset, minute_offset, precision )  
```  
  
## <a name="arguments"></a>Argumentos  
*year*  
Expresión entera que especifica un año.
  
*month*  
Expresión entera que especifica un mes.
  
*day*  
Expresión entera que especifica un día.
  
*hour*  
Expresión entera que especifica horas.
  
*minute*  
Expresión entera que especifica minutos.
  
*segundos*  
Expresión entera que especifica segundos.
  
*fractions*  
Expresión entera que especifica fracciones.
  
*hour_offset*  
Expresión entera que especifica la parte de hora del ajuste de zona horaria.
  
*minute_offset*  
Expresión entera que especifica la parte de minutos del ajuste de zona horaria.
  
*precisión*  
Literal entero que especifica la precisión del valor **datetimeoffset** que se va a devolver.
  
## <a name="return-types"></a>Tipos de valores devueltos
**datetimeoffset(** *precision* **)**
  
## <a name="remarks"></a>Notas  
**DATETIMEOFFSETFROMPARTS** devuelve un tipo de datos **datetimeoffset** totalmente inicializado. Los argumentos de desplazamiento se usan para representar el ajuste de zona horaria. Si se omiten los argumentos de desplazamiento, se supone que el ajuste de zona horaria es 00:00; es decir, no hay ningún ajuste de zona horaria. Si se especifican los argumentos de desplazamiento, ambos argumentos deben estar presente y ambos deben ser positivos o negativos. Si *minute_offset* se especifica sin *hour_offset*, se genera un error. Si otros argumentos no son válidos, se generará un error. Si los argumentos necesarios son NULL, se devuelve un valor NULL. Pero si el argumento *precision* es NULL, se generará un error.
  
El argumento *fractions* depende del argumento *precision*. Por ejemplo, si *precision* es 7, cada fracción representa 100 nanosegundos; si *precision* es 3, cada fracción representa un milisegundo. Si el valor de *precision* es cero, el valor de *fractions* también debe ser cero; de lo contrario, se generará un error.
  
Esta función se puede enviar de forma remota a servidores de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y superiores. No se puede enviar de forma remota a servidores que tengan una versión inferior a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-simple-example-without-fractions-of-a-second"></a>A. Ejemplo simple sin fracciones de segundo  
  
```sql
SELECT DATETIMEOFFSETFROMPARTS ( 2010, 12, 31, 14, 23, 23, 0, 12, 0, 7 ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
-------------------------------------------  
2010-12-07 00:00:00.0000000 +00:00  
  
(1 row(s) affected)  
```  
  
### <a name="b-example-with-fractions-of-a-second"></a>B. Ejemplo con fracciones de segundo  
En este ejemplo se muestra el uso de los parámetros *fractions* y *precision*:
1.   Cuando *fractions* tiene el valor 5 y *precision*, el valor 1, el valor de *fractions* representa 5/10 de un segundo.  
1.   Cuando *fractions* tiene el valor 50 y *precision*, el valor 2, el valor de *fractions* representa 50/100 de un segundo.  
1.   Cuando *fractions* tiene el valor 500 y *precision*, el valor 3, el valor de *fractions* representa 500/1000 de un segundo.  
  
```sql
SELECT DATETIMEOFFSETFROMPARTS ( 2011, 8, 15, 14, 30, 00, 5, 12, 30, 1 );  
SELECT DATETIMEOFFSETFROMPARTS ( 2011, 8, 15, 14, 30, 00, 50, 12, 30, 2 );  
SELECT DATETIMEOFFSETFROMPARTS ( 2011, 8, 15, 14, 30, 00, 500, 12, 30, 3 );  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
----------------------------------  
2011-08-15 14:30:00.5 +12:30  
  
(1 row(s) affected)  
  
----------------------------------  
2011-08-15 14:30:00.50 +12:30  
  
(1 row(s) affected)  
  
----------------------------------  
2011-08-15 14:30:00.500 +12:30  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vea también
[datetimeoffset &#40;Transact-SQL&#41;](../../t-sql/data-types/datetimeoffset-transact-sql.md)  
[AT TIME ZONE &#40;Transact-SQL&#41;](../../t-sql/queries/at-time-zone-transact-sql.md)
  
  


