---
title: MSSQLSERVER_10538 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 10538 (Database Engine error)
ms.assetid: 284d19b4-4979-4cbe-a9be-ac1104433c69
caps.latest.revision: 10
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3467e7cd3bc16dce9d80d4db134467c0beebd813
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver10538"></a>MSSQLSERVER_10538
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|SQL Server|  
|Identificador del evento|10538|  
|Origen del evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|PG_INVALID_PLANGUIDE_HANDLE|  
|Texto del mensaje|No se encuentra la guía de plan porque el Id. de guía de plan especificado es NULL o no es válido, o porque no tiene permiso para el objeto al que hace referencia la guía de plan. Compruebe que el id. de guía de plan es válido, la sesión actual está establecida en el contexto de base de datos correcto y que tiene permiso ALTER para el objeto al que hace referencia la guía de plan o el permiso ALTER DATABASE.|  
  
## <a name="explanation"></a>Explicación  
El identificador de la guía de plan especificada es NULL o no es válido, o no se tiene permiso para el objeto al que hace referencia la guía de plan.  
  
## <a name="user-action"></a>Acción del usuario  
Compruebe que el identificador de guía de plan es válido, la sesión actual está establecida en el contexto de base de datos correcto y se tiene el permiso ALTER DATABASE o ALTER para el objeto al que hace referencia la guía de plan.  
  
## <a name="see-also"></a>Ver también  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[Guías de plan](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
