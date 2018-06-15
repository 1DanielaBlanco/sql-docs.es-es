---
title: Sys.remote_logins (Transact-SQL) | Documentos de Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.remote_logins_TSQL
- remote_logins
- remote_logins_TSQL
- sys.remote_logins
dev_langs:
- TSQL
helpviewer_keywords:
- sys.remote_logins catalog view
ms.assetid: 38477e91-d084-4df7-b1de-b930c5580189
caps.latest.revision: 22
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: df40db329851fbe931cb96f5b1aac99905d705c4
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33179511"
---
# <a name="sysremotelogins-transact-sql"></a>sys.remote_logins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve una fila por cada asignación de inicio de sesión remoto. Esta vista de catálogo se utiliza para asignar inicios de sesión locales entrantes originados en el servidor correspondiente para un inicio de sesión local real.  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|Id. del servidor en **sys.servers**. Este nombre es suministrado por la conexión desde el servidor "remoto".|  
|**remote_name**|**sysname**|Nombre de inicio de sesión que suministra la conexión para su asignación. Si el valor es NULL, se utiliza el nombre de inicio de sesión especificado en la conexión.|  
|**local_principal_id**|**int**|Id. de la entidad de seguridad del servidor a la que se asigna el inicio de sesión. Si el valor es 0, el inicio de sesión remoto se asigna al inicio de sesión con el mismo nombre.|  
|**modify_date**|**datetime**|Fecha en que se cambió el inicio de sesión vinculado por última vez.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Para obtener más información, consulte [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vea también  
 [Vistas de catálogo de servidores vinculados &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/linked-servers-catalog-views-transact-sql.md)   
 [Vistas de catálogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
