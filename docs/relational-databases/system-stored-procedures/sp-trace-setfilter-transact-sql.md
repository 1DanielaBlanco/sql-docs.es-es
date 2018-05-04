---
title: sp_trace_setfilter (Transact-SQL) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_trace_setfilter
- sp_trace_setfilter_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_trace_setfilter
ms.assetid: 11e7c7ac-a581-4a64-bb15-9272d5c1f7ac
caps.latest.revision: 35
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 07f7f486c8d5cdee2b27369f8c488f975d68fbc8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="sptracesetfilter-transact-sql"></a>sp_trace_setfilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aplica un filtro a un seguimiento. **sp_trace_setfilter** se puede ejecutar solo en seguimientos existentes que estén detenidos (*estado* es **0**). [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Devuelve un error si este procedimiento almacenado se ejecuta en un seguimiento que no existe o cuyo *estado* no **0**.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Use eventos extendidos en su lugar.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_trace_setfilter [ @traceid = ] trace_id   
          , [ @columnid = ] column_id  
          , [ @logical_operator = ] logical_operator  
          , [ @comparison_operator = ] comparison_operator  
          , [ @value = ] value  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@traceid=** ] *trace_id*  
 Es el id. del seguimiento en el que se establece el filtro. *trace_id* es **int**, no tiene ningún valor predeterminado. El usuario utiliza este *trace_id* valor para identificar, modificar y controlar el seguimiento.  
  
 [  **@columnid=** ] *column_id*  
 Es el id. de la columna en la que se aplica el filtro. *column_id* es **int**, no tiene ningún valor predeterminado. Si *column_id* es NULL, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] borra todos los filtros para el seguimiento especificado.  
  
 [ **@logical_operator** =] *logical_operator*  
 Especifica si la operación AND (**0**) o OR (**1**) se aplica el operador. *logical_operator* es **int**, no tiene ningún valor predeterminado.  
  
 [  **@comparison_operator=** ] *comparison_operator*  
 Especifica el tipo de comparación que va a realizarse. *comparison_operator* es **int**, no tiene ningún valor predeterminado. Esta tabla contiene los operadores de comparación y sus valores representativos.  
  
|Value|Operador de comparación|  
|-----------|-------------------------|  
|**0**|= (Es igual a)|  
|**1**|<> (No es igual a)|  
|**2**|> (Mayor que)|  
|**3**|< (Menor que)|  
|**4**|>= (Mayor o igual que)|  
|**5**|< = (menor o igual que)|  
|**6**|LIKE|  
|**7**|No es como|  
  
 [  **@value=** ] *valor*  
 Especifica el valor en el que se va a filtrar. Tipo de datos de *valor* debe coincidir con el tipo de datos de la columna que desea filtrar. Por ejemplo, si el filtro está establecido en una columna de Id. de objeto que sea un **int** tipo de datos, *valor* debe ser **int**. Si *valor* es **nvarchar** o **varbinary**, puede tener una longitud máxima de 8000.  
  
 Cuando el operador de comparación es LIKE o NOT LIKE, el operador lógico puede incluir "%" u otro filtro adecuado para la operación LIKE.  
  
 También puede especificar NULL para *valor* para filtrar los eventos con valores de columna NULL. Solo **0** (= igual a) y **1** operadores (<> no es igual) son válidos con NULL. En este caso, estos operadores son equivalentes a los operadores IS NULL e IS NOT NULL de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Para aplicar el filtro entre un intervalo de valores de columna, **sp_trace_setfilter** se debe ejecutar dos veces: una vez con una mayor que-o igual ('> =') operador de comparación y otra vez con un menor que-o igual ('< =') (operador) .  
  
 Para obtener más información acerca de los tipos de datos de columna de datos, vea el [SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md).  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 En la tabla siguiente se describen los valores del código que los usuarios pueden obtener después de completar el procedimiento almacenado.  
  
|Código de retorno|Description|  
|-----------------|-----------------|  
|0|Ningún error.|  
|1|Error desconocido.|  
|2|El seguimiento está actualmente en ejecución. Si se cambia el seguimiento en este momento, se producirá un error.|  
|4|La columna especificada no es válida.|  
|5|La columna especificada no está permitida para el filtro. Este valor solo se devuelve desde **sp_trace_setfilter**.|  
|6|El operador de comparación especificado no es válido.|  
|7|El operador lógico especificado no es válido.|  
|9|El controlador de traza especificado no es válido.|  
|13|Memoria insuficiente. Se devuelve cuando no hay memoria suficiente para realizar la acción especificada.|  
|16|La función no es válida para este seguimiento.|  
  
## <a name="remarks"></a>Comentarios  
 **sp_trace_setfilter** es un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] procedimiento almacenado que realiza muchas de las acciones que anteriormente ejecutadas los procedimientos almacenados extendidos disponibles en versiones anteriores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Use **sp_trace_setfilter** en lugar de la **xp_trace_set\*filtro** extendidos procedimientos almacenados para crear, aplicar, quitar o manipular filtros en trazas. Para obtener más información, consulte [filtrar un seguimiento](../../relational-databases/sql-trace/filter-a-trace.md).  
  
 Todos los filtros de una columna en particular deben habilitarse conjuntamente en una única ejecución de **sp_trace_setfilter**. Por ejemplo, si un usuario se propone aplicar dos filtros en la columna del nombre de la aplicación y uno en la columna del nombre del usuario, el usuario deberá especificar los filtros en el nombre de la aplicación en secuencia. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] devolverá un error si el usuario intenta especificar un filtro de nombre de aplicación en una llamada a un procedimiento almacenado, seguido de un filtro de nombre de usuario y, luego, otro filtro de nombre de aplicación.  
  
 Parámetros de seguimiento de SQL todos los procedimientos almacenados (**sp_trace_xx**) deben escribirse. Si no se llama a estos parámetros con los tipos de datos de parámetros de entrada correctos, según se especifica en la descripción del argumento, el procedimiento almacenado devuelve un error.  
  
## <a name="permissions"></a>Permissions  
 El usuario debe tener permiso ALTER TRACE.  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se establecen tres filtros en Trace `1`. Los filtros `N'SQLT%'` y `N'MS%'` actúan en una columna (`AppName`, valor `10`) utilizando el operador de comparación "`LIKE`". El filtro `N'joe'` actúa en otra columna (`UserName`, valor `11`) utilizando el operador de comparación "`EQUAL`".  
  
```  
sp_trace_setfilter  1, 10, 0, 6, N'SQLT%';  
sp_trace_setfilter  1, 10, 0, 6, N'MS%';  
sp_trace_setfilter  1, 11, 0, 0, N'joe';  
```  
  
## <a name="see-also"></a>Vea también  
 [sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md)   
 [sys.fn_trace_getinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md)   
 [Seguimiento de SQL](../../relational-databases/sql-trace/sql-trace.md)  
  
  
