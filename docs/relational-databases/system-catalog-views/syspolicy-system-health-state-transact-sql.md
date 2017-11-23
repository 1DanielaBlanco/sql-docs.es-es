---
title: syspolicy_system_health_state (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- syspolicy_system_health_state_TSQL
- syspolicy_system_health_state
dev_langs: TSQL
helpviewer_keywords: syspolicy_system_health_state view
ms.assetid: 00815106-9fe4-481d-a9e1-a256101887f4
caps.latest.revision: "22"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e3aa7ef860f35917adc330b6c8c49b3692b5e6f4
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="syspolicysystemhealthstate-transact-sql"></a>syspolicy_system_health_state (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Muestra una fila para cada combinación de expresión de consulta de destino y directiva de administración basada en directivas. Utilice la vista syspolicy_system_health_state para comprobar mediante programación el estado de directivas del servidor. En la tabla siguiente se describen las columnas de la vista syspolicy_system_health_state.  
  
||  
|-|  
|**Se aplica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a través de la [versión actual](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|health_state_id|**bigint**|Identificador del registro de estado de la directiva de mantenimiento.|  
|policy_id|**int**|Identificador de la directiva.|  
|last_run_date|**datetime**|Fecha y hora en que la directiva se ejecutó por última vez.|  
|target_query_expression_with_id|**nvarchar (400)**|Expresión de destino, con los valores asignados a las variables de identidad, que define el destino con el que se evalúa la directiva.|  
|target_query_expression|**nvarchar(max)**|Expresión que define el destino con el que se evalúa la directiva.|  
|result|**bit**|Estado de mantenimiento de este destino con respecto a la directiva:<br /><br /> 0 = Error<br /><br /> 1 = Correcto|  
  
## <a name="remarks"></a>Comentarios  
 La vista syspolicy_system_health_state muestra el estado más reciente de la expresión de consulta de destino para cada directiva activa (habilitada). El Explorador de objetos de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] y la página Detalles del Explorador de objetos agregan el estado de la directiva de mantenimiento en esta vista para mostrar el estado crítico.  
  
## <a name="permissions"></a>Permissions  
 Requiere la pertenencia al rol PolicyAdministratorRole en la base de datos msdb.  
  
## <a name="see-also"></a>Vea también  
 [Administrar servidores mediante administración basada en directivas](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Vistas de administración basada en directivas &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
