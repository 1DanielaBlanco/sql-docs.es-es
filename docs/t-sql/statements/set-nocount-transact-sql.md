---
title: SET NOCOUNT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, database-engine, sql-database
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- NOCOUNT
- SET_NOCOUNT_TSQL
- NOCOUNT_TSQL
- SET NOCOUNT
dev_langs:
- TSQL
helpviewer_keywords:
- NOCOUNT option
- number of rows affected by statement
- row affected by statements [SQL Server]
- counting rows
- SET NOCOUNT statement
ms.assetid: eb3e6727-cb26-4bc2-84c7-171cbac02029
caps.latest.revision: 42
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 190f6f859eef8e2bc89138ef7183a00e276abd57
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="set-nocount-transact-sql"></a>SET NOCOUNT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  Evita que se devuelva el mensaje que muestra el recuento del número de filas afectadas por una instrucción o un procedimiento almacenado de [!INCLUDE[tsql](../../includes/tsql-md.md)] como parte del conjunto de resultados.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
SET NOCOUNT { ON | OFF }   
```  
  
## <a name="remarks"></a>Notas  
 Si se establece SET NOCOUNT en ON, no se devuelve el recuento. Cuando SET NOCOUNT es OFF, sí se devuelve ese número.  
  
 La función @@ROWCOUNT se actualiza incluso cuando SET NOCOUNT está en ON.  
  
 SET NOCOUNT ON impide el envío al cliente de mensajes DONE_IN_PROC por cada instrucción de un procedimiento almacenado. En los procedimientos almacenados que contengan varias instrucciones que no devuelven mucha información real o en los procedimientos que contengan bucles de [!INCLUDE[tsql](../../includes/tsql-md.md)], establecer SET NOCOUNT en ON puede suponer una mejora significativa del rendimiento, ya que el tráfico de la red se reduce en gran medida.  
  
 La configuración especificada por SET NOCOUNT está activa en tiempo de ejecución, no en tiempo de análisis.  
  
 Para ver la configuración actual de este valor, ejecute la consulta siguiente.  
  
```  
DECLARE @NOCOUNT VARCHAR(3) = 'OFF';  
IF ( (512 & @@OPTIONS) = 512 ) SET @NOCOUNT = 'ON';  
SELECT @NOCOUNT AS NOCOUNT;  
  
```  
  
## <a name="permissions"></a>Permisos  
 Debe pertenecer al rol **public** .  
  
## <a name="examples"></a>Ejemplos  
 En este ejemplo no se muestra el mensaje que indica el número de filas afectado.  
  
```  
USE AdventureWorks2012;  
GO  
SET NOCOUNT OFF;  
GO  
-- Display the count message.  
SELECT TOP(5)LastName  
FROM Person.Person  
WHERE LastName LIKE 'A%';  
GO  
-- SET NOCOUNT to ON to no longer display the count message.  
SET NOCOUNT ON;  
GO  
SELECT TOP(5) LastName  
FROM Person.Person  
WHERE LastName LIKE 'A%';  
GO  
-- Reset SET NOCOUNT to OFF  
SET NOCOUNT OFF;  
GO  
```  
  
## <a name="see-also"></a>Ver también  
 [@@ROWCOUNT &#40;Transact-SQL&#41;](../../t-sql/functions/rowcount-transact-sql.md)   
 [Instrucciones SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  
