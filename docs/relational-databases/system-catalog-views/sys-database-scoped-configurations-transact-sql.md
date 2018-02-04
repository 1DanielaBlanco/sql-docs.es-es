---
title: sys.database_scoped_configurations (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 01/16/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- database_scoped_configurations
- database_scoped_configurations_TSQL
- sys.database_scoped_configurations
- sys.database_scoped_configurations_TSQL
helpviewer_keywords:
- sys.database_scoped_configurations catalog view
ms.assetid: 8899310a-3464-4d38-9f2f-88396c4e7dc2
caps.latest.revision: 
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 84a4da130f637e85e4ebc950db5568f1fa8876f2
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2018
---
# <a name="sysdatabasescopedconfigurations-transact-sql"></a>sys.database_scoped_configurations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Contiene una fila por cada configuración. 
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**configuration_id**|**int**|Id. de la opción de configuración.|  
|**Nombre**|**nvarchar(60)**|El nombre de la opción de configuración. Para obtener información acerca de las configuraciones posibles, consulte [ALTER DATABASE SCOPED CONFIGURATION &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).|  
|**value**|**sqlvariant**|El valor establecido para esta opción de configuración para la réplica principal.|  
|**value_for_secondary**|**sqlvariant**|El valor establecido para esta opción de configuración para las réplicas secundarias.|  
  
##  <a name="Permissions"></a> Permisos  
 Debe pertenecer al rol **public** .  
  
## <a name="remarks"></a>Comentarios  
 Cuando se devuelve NULL como el valor de **value_for_secondary**, esto significa que la base de datos secundaria está establecido en principal.  
 
 El ámbito de base de datos de configuración se transferirán a con la base de datos de configuración. Esto significa que cuando se restaura o adjunta una base de datos, las opciones de configuración existentes permanecen.
  
## <a name="see-also"></a>Vea también  
 [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)  
  
  
