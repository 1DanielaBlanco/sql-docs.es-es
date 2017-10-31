---
title: MSSQLSERVER_10502 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 10502 (Database Engine error)
ms.assetid: 26d9b64d-4299-4b55-92d0-0a32a3688c0a
caps.latest.revision: 9
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 2f7e1cd208d731f1a8c0cde03a01e2feb0bacadc
ms.contentlocale: es-es
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver10502"></a>MSSQLSERVER_10502
  
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|SQL Server|  
|Identificador del evento|10502|  
|Origen del evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|PG_DUP_FOUND|  
|Texto del mensaje|No se puede crear la guía de plan '%.*ls' porque la instrucción especificada por @stmt y @module_or_batch, o por @plan_handle y @statement_start_offset, coincide con la guía de plan '%.\*ls' existente en la base de datos. Quite la guía de plan existente antes de crear la nueva.|  
  
## <a name="explanation"></a>Explicación  
Existe una guía de plan para la instrucción especificada.  
  
## <a name="user-action"></a>Acción del usuario  
Quite la guía de plan existente antes de crear la nueva.  
  
## <a name="see-also"></a>Vea también  
[Plan Guides](~/relational-databases/performance/plan-guides.md) (Guías de plan)  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  

