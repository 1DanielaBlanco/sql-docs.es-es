---
title: '@@LOCK_TIMEOUT (Transact-SQL) | Documentos de Microsoft'
ms.custom: 
ms.date: 09/19/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@LOCK_TIMEOUT'
- '@@LOCK_TIMEOUT_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- timeout options [SQL Server], locks
- '@@LOCK_TIMEOUT function'
- current lock time-out setting
- locking [SQL Server], time-outs
ms.assetid: 6bf8bf97-60b8-40c1-b89d-8f5a00bcae2e
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 84b885d21e5d940e3c532eef43040ba29c2b45ea
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="x40x40locktimeout-transact-sql"></a>&#x40;&#x40;LOCK_TIMEOUT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Devuelve el valor actual de tiempo de espera de bloqueo en milisegundos para la sesión actual.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
@@LOCK_TIMEOUT  
```  
  
## <a name="return-types"></a>Tipos devueltos  
 **integer**  
  
## <a name="remarks"></a>Comentarios  
 SET LOCK_TIMEOUT permite a una aplicación establecer el tiempo máximo que espera una instrucción en un recurso bloqueado. Cuando una instrucción ha esperado más tiempo que el indicado en LOCK_TIMEOUT, la instrucción bloqueada se cancela automáticamente y se devuelve un mensaje de error a la aplicación.  
  
 @@LOCK_TIMEOUT devuelve un valor de -1 si SET LOCK_TIMEOUT aún no se ha ejecutado en la sesión actual.  
  
## <a name="examples"></a>Ejemplos  
 En este ejemplo se muestra el conjunto de resultados cuando no se establece un valor en LOCK_TIMEOUT.  
  
```  
SELECT @@LOCK_TIMEOUT AS [Lock Timeout];  
GO  
```  
  
 El conjunto de resultados es:  
  
```  
Lock Timeout  
------------  
-1  
```  
  
 Este ejemplo establece LOCK_TIMEOUT en 1.800 milisegundos y, a continuación, llama a@LOCK_TIMEOUT .  
  
```  
SET LOCK_TIMEOUT 1800;  
SELECT @@LOCK_TIMEOUT AS [Lock Timeout];  
GO  
```  
  
 El conjunto de resultados es:  
  
```  
Lock Timeout  
------------  
1800          
```  
  
## <a name="see-also"></a>Vea también  
 [Funciones de configuración &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [SET LOCK_TIMEOUT &#40; Transact-SQL &#41;](../../t-sql/statements/set-lock-timeout-transact-sql.md)  
  
  
