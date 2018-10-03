---
title: Sys.database_scoped_configurations (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- database_scoped_configurations
- database_scoped_configurations_TSQL
- sys.database_scoped_configurations
- sys.database_scoped_configurations_TSQL
helpviewer_keywords:
- sys.database_scoped_configurations catalog view
ms.assetid: 8899310a-3464-4d38-9f2f-88396c4e7dc2
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 350f3af1bfd6e2765f74d074727577541378d2e2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47733843"
---
# <a name="sysdatabasescopedconfigurations-transact-sql"></a>sys.database_scoped_configurations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Contiene una fila por cada configuración. 
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**configuration_id**|**int**|Id. de la opción de configuración.|  
|**Nombre**|**nvarchar(60)**|El nombre de la opción de configuración. Para obtener información acerca de las configuraciones posibles, vea [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).|  
|**Valor**|**SQLVARIANT**|El valor establecido para esta opción de configuración para la réplica principal.|  
|**value_for_secondary**|**SQLVARIANT**|El valor establecido para esta opción de configuración para las réplicas secundarias.|  
|**elevate_online**|**nvarchar(60)** |Conjunto predeterminado de la opción para las operaciones de índice en línea con ámbito de la base de datos |
|**elevate_resumable**|nvarchar(60)|Conjunto predeterminado de la opción para las operaciones de índice reanudable con ámbito de la base de datos| 
  
##  <a name="Permissions"></a> Permissions  
 Debe pertenecer al rol **public** .  
  
## <a name="remarks"></a>Comentarios  
 Cuando se devuelve NULL como el valor de **value_for_secondary**, esto significa que se establece la base de datos secundaria a principal.  
 
 Las opciones de configuración con ámbito de base de datos se transfieren con la base de datos. Esto significa que cuando se restaura o adjunta una base de datos, se conservan las opciones de configuración existentes.
  
## <a name="see-also"></a>Vea también  
 [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)  
  
  
