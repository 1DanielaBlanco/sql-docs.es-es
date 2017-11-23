---
title: NULL y UNKNOWN (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, pdw, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 9d491846-4730-4740-a680-77c69fae4a58
caps.latest.revision: "5"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: d0523877d572bd644fa772713f3c7edb82d645f2
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="null-and-unknown-transact-sql"></a>NULL y UNKNOWN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-pdw-md.md)]

  NULL indica que el valor es desconocido. Un valor null es diferente de un valor vacío o cero. No hay dos valores NULL que sean iguales. Las comparaciones entre dos valores null, o entre un valor null y cualquier otro valor, un resultado desconocidas porque el valor de cada NULL es desconocido.  
  
 Valores NULL indican generalmente que los datos que es desconocido, no está disponible, o que se agregará más tarde. Por ejemplo, la inicial de un cliente puede que no sea conocida en el momento en que éste hace un pedido.  
  
 Tenga en cuenta lo siguiente acerca de los valores null:  
  
-   Para comprobar si hay valores NULL en una consulta, use IS NULL o IS NOT NULL en la cláusula WHERE.  
  
-   Valores NULL se pueden insertar en una columna si se indica explícitamente NULL en una instrucción INSERT o UPDATE, o dejando una columna fuera de una instrucción INSERT.  
  
-   Valores NULL no se puede usar como la información necesaria para distinguir una fila en una tabla de otra fila de una tabla, como las claves principales, o para obtener información que se usa para distribuir filas, como las claves de distribución.  
  
 Cuando hay valores NULL en los datos, los operadores lógicos y de comparación pueden devolver un tercer resultado UNKNOWN (desconocido) en lugar de simplemente TRUE (verdadero) o FALSE (falso). Esta necesidad de una lógica de tres valores es el origen de muchos errores de la aplicación. En estas tablas se destaca el efecto de escribir comparaciones con NULL.  
  
 La siguiente tabla muestra los resultados de aplicar un operador AND a dos operandos booleanos donde uno de los operandos devuelve NULL.  
  
|Operando 1|Operando de 2|Resultado|  
|---------------|---------------|------------|  
|TRUE|NULL|FALSE|  
|NULL|NULL|FALSE|  
|FALSE|NULL|FALSE|  
  
 La siguiente tabla muestra los resultados de aplicar un operador OR a dos operandos booleanos donde uno de los operandos devuelve NULL.  
  
|Operando 1|Operando de 2|Resultado|  
|---------------|---------------|------------|  
|TRUE|NULL|TRUE|  
|NULL|NULL|UNKNOWN|  
|FALSE|NULL|UNKNOWN|  
  
## <a name="see-also"></a>Vea también  
 [Y &#40; Transact-SQL &#41;](../../t-sql/language-elements/and-transact-sql.md)   
 [O &#40; Transact-SQL &#41;](../../t-sql/language-elements/or-transact-sql.md)   
 [No &#40; Transact-SQL &#41;](../../t-sql/language-elements/not-transact-sql.md)   
 [ES NULL &#40; Transact-SQL &#41;](../../t-sql/queries/is-null-transact-sql.md)  
  
  
