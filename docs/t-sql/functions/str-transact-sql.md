---
title: STR (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/16/2017
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
- STR
- STR_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- converting numbers to characters
- characters [SQL Server], converting
- character data [SQL Server]
- STR function
ms.assetid: de03531b-d9e7-4c3c-9604-14e582ac20c6
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 04386cd8dafb69d08c72b460f3794963c8b6da36
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/18/2018
---
# <a name="str-transact-sql"></a>STR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Devuelve datos de caracteres convertidos de datos numéricos.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STR ( float_expression [ , length [ , decimal ] ] )  
```  
  
## <a name="arguments"></a>Argumentos  
 *float_expression*  
 Es una expresión de numérico aproximado (**float**) tipo de datos con un separador decimal.  
  
 *length*  
 Es la longitud total. Ésta incluye el separador decimal, el signo, los dígitos y los espacios. El valor predeterminado es 10.  
  
 *decimal*  
 Es el número de posiciones a la derecha del separador decimal. *decimal* debe ser menor o igual que 16. Si *decimal* es mayor que 16, a continuación, el resultado se trunca a dieciséis lugares a la derecha del separador decimal.  
  
## <a name="return-types"></a>Tipos devueltos  
 **varchar**  
  
## <a name="remarks"></a>Comentarios  
 Si se especifican, los valores para *longitud* y *decimal* parámetros STR deben ser positivos. El número se redondea a un entero de forma predeterminada, o si el parámetro decimal es 0. La longitud especificada debe ser mayor o igual que la parte del número situada delante del separador decimal más el signo del número (si lo hay). Un valor bajo *float_expression* está justificado a la derecha en la longitud especificada y un valor largo *float_expression* se trunca en el número especificado de posiciones decimales. Por ejemplo, STR (12**,**10) da como resultado 12. Se justifica a la derecha en el conjunto de resultados. Sin embargo, STR (1223**,**2) trunca el conjunto de resultados a **. Las funciones de cadena se pueden anidar.  
  
> [!NOTE]  
>  Para convertir en datos Unicode, utilice STR en una conversión o [conversión](../../t-sql/functions/cast-and-convert-transact-sql.md) función de conversión.  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se convierte una expresión formada por un máximo de cinco dígitos y un separador decimal en una cadena de caracteres de seis posiciones. La parte fraccionaria del número se redondea a un lugar decimal.  
  
```  
SELECT STR(123.45, 6, 1);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
------  
 123.5  
  
(1 row(s) affected)  
```  
  
 Cuando la expresión excede la longitud especificada, la cadena devuelve `**` para esa longitud.  
  
```  
SELECT STR(123.45, 2, 2);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--  
**  
  
(1 row(s) affected)  
```  
  
 Incluso cuando se anidan datos numéricos en `STR`, el resultado son datos de tipo carácter con el formato especificado.  
  
```  
SELECT STR (FLOOR (123.45), 8, 3;)  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--------  
 123.000  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vea también  
 [CAST y CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
 [FORMAT &#40;Transact-SQL&#41;](../../t-sql/functions/format-transact-sql.md)  
 [Funciones de cadena &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  
  

