---
title: Sys.cryptographic_providers (Transact-SQL) | Documentos de Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- cryptographic_providers
- sys.cryptographic_providers
- sys.cryptographic_providers_TSQL
- cryptographic_providers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.cryptographic_providers catalog view
ms.assetid: 9da0da95-792e-48b4-9f60-47f0729c279c
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: a5a73404425ac5af2afbc103b7c14e0de69509ed
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="syscryptographicproviders-transact-sql"></a>sys.cryptographic_providers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Devuelve una fila para cada proveedor criptográfico registrado.  
    
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**provider_id**|**int**|Número de identificación del proveedor de servicios criptográficos.|  
|**Nombre**|**sysname**|Nombre del proveedor criptográfico.|  
|**GUID**|**uniqueidentifier**|Proveedor único GUID.|  
|**version**|**nvarchar(50)**|Versión del proveedor en el formato '*aa.bb.cccc.dd*'.|  
|**dll_path**|**nvarchar(512)**|Ruta de acceso a DLL que implementa la interfaz de programación de aplicaciones (API) de la Administración extensible de claves (EKM).|  
|**is_enabled**|**bit**|Si el proveedor está habilitado en el servidor o no.<br /><br /> 0 = no habilitado (predeterminado)<br /><br /> 1 = habilitado|  
  
## <a name="remarks"></a>Comentarios  
 El **sys.cryptographic_providers** vista está visible para el público.  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Para obtener más información, consulte [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vea también  
 [Vistas de catálogo de seguridad &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Jerarquía de cifrado](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Administración extensible de claves &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../t-sql/statements/create-cryptographic-provider-transact-sql.md)  
  
  
