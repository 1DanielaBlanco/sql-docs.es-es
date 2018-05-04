---
title: CHANGE_TRACKING_IS_COLUMN_IN_MASK (Transact-SQL) | Documentos de Microsoft
ms.custom: ''
ms.date: 08/08/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CHANGE_TRACKING_IS_COLUMN_IN_MASK_TSQL
- CHANGE_TRACKING_IS_COLUMN_IN_MASK
dev_langs:
- TSQL
helpviewer_keywords:
- change tracking [SQL Server], CHANGE_TRACKING_IS_COLUMN_IN_MASK
- CHANGE_TRACKING_IS_COLUMN_IN_MASK
ms.assetid: 649b370b-da54-4915-919d-1b597a39d505
caps.latest.revision: 15
author: rothja
ms.author: jroth
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 24316c384dbf8f7074a852dfce8ff8358321eb06
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="changetrackingiscolumninmask-transact-sql"></a>CHANGE_TRACKING_IS_COLUMN_IN_MASK (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Interpreta el valor SYS_CHANGE_COLUMNS devuelto por la función CHANGETABLE (CHANGES …). Esto permite a una aplicación determinar si la columna especificada está incluida en los valores devueltos para SYS_CHANGE_COLUMNS.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
CHANGE_TRACKING_IS_COLUMN_IN_MASK ( column_id , change_columns )  
```  
  
## <a name="arguments"></a>Argumentos  
 *column_id*  
 Es el Id. de la columna que se está comprobando. La columna de identificador se puede obtener mediante el uso de la [COLUMNPROPERTY](../../t-sql/functions/columnproperty-transact-sql.md) función.  
  
 *change_columns*  
 Son los datos binarios de la columna SYS_CHANGE_COLUMNS de la [CHANGETABLE](../../relational-databases/system-functions/changetable-transact-sql.md) datos.  
  
## <a name="return-type"></a>Tipo devuelto  
 **bit**  
  
## <a name="return-values"></a>Valores devueltos  
 CHANGE_TRACKING_IS_COLUMN_IN_MASK devuelve los siguientes valores.  
  
|Valor devuelto|Description|  
|------------------|-----------------|  
|0|La columna especificada no está en el *change_columns* lista.|  
|1|La columna especificada está en la *change_columns* lista.|  
  
## <a name="remarks"></a>Comentarios  
 CHANGE_TRACKING_IS_COLUMN_IN_MASK no realiza ninguna comprobación para validar el *column_id* valor o que la *change_columns* parámetro se obtuvo de la tabla desde la que el  *column_id* se obtuvo.  
  
## <a name="examples"></a>Ejemplos  
 El siguiente ejemplo determina si la columna `Salary` de la tabla `Employees` está actualizada. El `COLUMNPROPERTY` función devuelve el identificador de columna de la `Salary` columna. La variable local `@change_columns` debe establecerse en los resultados de una consulta con CHANGETABLE como origen de datos.  
  
```sql  
SET @SalaryChanged = CHANGE_TRACKING_IS_COLUMN_IN_MASK  
    (COLUMNPROPERTY(OBJECT_ID('Employees'), 'Salary', 'ColumnId')  
    ,@change_columns);  
```  
  
## <a name="see-also"></a>Vea también  
 [Funciones de seguimiento de cambios &#40;Transact-SQL&#41;](../../relational-databases/system-functions/change-tracking-functions-transact-sql.md)   
 [CHANGETABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/changetable-transact-sql.md)   
 [Seguimiento de cambios de datos &#40;SQL Server&#41;](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
  
