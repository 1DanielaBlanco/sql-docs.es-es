---
title: money y smallmoney (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- money_TSQL
- money
- smallmoney
- smallmoney_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- money data type, about money data type
- money data type
- smallmoney data type
- values [SQL Server], monetary
- currency [SQL Server]
ms.assetid: 57861137-89ea-4b89-b361-390597d7bccc
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: c9c66d9934618b1b8b21b0d4dcb0a234ff94731f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="money-and-smallmoney-transact-sql"></a>money y smallmoney (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Tipos de datos que representan valores monetarios o de moneda.
  
## <a name="remarks"></a>Notas  
  
|Tipo de datos|Intervalo|Storage|  
|---|---|---|
|**money**|De -922.337.203.685.477,5808 a 922.337.203.685.477,5807 (de -922.337.203.685.477,58<br />a 922.337.203.685.477,58 en el caso de Informatica.  Informatica admite únicamente dos decimales, no cuatro).|8 bytes|  
|**smallmoney**|De - 214.748,3648 a 214.748,3647|4 bytes|  
  
Los tipos de datos **money** y **smallmoney** tienen una precisión de una diezmilésima de las unidades monetarias que representan. En Informatica, los tipos de datos **money** y **smallmoney** tienen una precisión de una centésima de las unidades monetarias que representan.
  
Use un punto para separar las unidades parciales de moneda, como céntimos, de las unidades completas de moneda. Por ejemplo, 2.15 puede especificar 2 dólares y 15 centavos.
  
Estos tipos de datos pueden usar alguno de los siguientes símbolos de moneda.
  
![Tabla de símbolos de moneda, valores hexadecimales](../../t-sql/data-types/media/money01.gif "Tabla de símbolos de moneda, valores hexadecimales")
  
No es necesario incluir los datos de moneda entre comillas simples ('). Es importante recordar que aunque es posible especificar valores monetarios precedidos de un símbolo de moneda, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no almacena ninguna información de moneda asociada con el símbolo, solo almacena el valor numérico.
  
## <a name="converting-money-data"></a>Convertir datos money
Cuando se convierte a **money** desde tipos de datos enteros, se supone que las unidades están en unidades de moneda. Por ejemplo, el valor entero 4 se convierte al equivalente **money** de 4 unidades monetarias.
  
En el siguiente ejemplo se convierten valores **smallmoney** y **money** a tipos de datos **varchar** y **decimal** respectivamente.
  
```sql
DECLARE @mymoney_sm smallmoney = 3148.29,  
        @mymoney    money = 3148.29;  
SELECT  CAST(@mymoney_sm AS varchar) AS 'SM_MONEY varchar',  
        CAST(@mymoney AS decimal)    AS 'MONEY DECIMAL';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
SM_MONEY VARCHAR               MONEY DECIMAL  
------------------------------ ----------------------  
3148.29                        3148    
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vea también
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)
[CAST y CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)
[Tipos de datos &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)
[sys.types &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)
  
  
