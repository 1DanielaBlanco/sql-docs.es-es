---
title: MSSQLSERVER_10532 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 10532 (Database Engine error)
ms.assetid: 01da29ee-bf67-433f-8148-587a7e8d1d76
caps.latest.revision: 10
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 690a5da7eb3ed2da417fc0b5baf53d6668e11f90
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36105860"
---
# <a name="mssqlserver10532"></a>MSSQLSERVER_10532
    
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|SQL Server|  
|Identificador del evento|10532|  
|Origen del evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|PG_NO_ELIGIBLE_STMT|  
|Texto del mensaje|No se puede crear la Guía de plan ' %. \*ls' porque el lote o módulo especificado por `@plan_handle` no contiene una instrucción válida para una guía de plan. Especifique un valor distinto para `@plan_handle`.|  
  
## <a name="explanation"></a>Explicación  
 El lote o módulo especificado por `@plan_handle` no contiene una instrucción válida para una guía de plan.  
  
## <a name="user-action"></a>Acción del usuario  
 Especifique un valor distinto para `@plan_handle`.  
  
## <a name="see-also"></a>Vea también  
 [Guías de plan](../performance/plan-guides.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
