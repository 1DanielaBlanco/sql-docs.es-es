---
title: Sys.key_encryptions (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.key_encryptions
- key_encryptions_TSQL
- sys.key_encryptions_TSQL
- key_encryptions
dev_langs: TSQL
helpviewer_keywords: sys.key_encryptions catalog view
ms.assetid: c39cecf8-af63-40b9-98e5-f84a5bf3ae54
caps.latest.revision: "22"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ba1c62078f0400436a21749b28c302d2f8a2509e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="syskeyencryptions-transact-sql"></a>sys.key_encryptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Devuelve una fila por cada cifrado de clave simétrica especificado mediante el uso de la cláusula ENCRYPTION BY de la instrucción CREATE SYMMETRIC KEY.  

  
|Nombres de columna|Tipos de datos|Description|  
|------------------|----------------|-----------------|  
|**valor key_ID**|**int**|Id. de la clave cifrada.|  
|**huella digital**|**varbinary(32)**|Hash SHA-1 del certificado o GUID de la clave simétrica con el que se cifra la clave.|  
|**crypt_type**|**(4)**|Tipo de cifrado:<br /><br /> ESKS = Cifrado mediante clave simétrica<br /><br /> ESKP, ESP2 o ESP3 = cifrado mediante contraseña<br /><br /> EPUC = Cifrado mediante certificado<br /><br /> EPUA = Cifrado mediante clave asimétrica<br /><br /> ESKM = Cifrado mediante clave maestra|  
|**crypt_type_desc**|**nvarchar (60)**|Descripción del tipo de cifrado:<br /><br /> ENCRYPTION BY SYMMETRIC KEY<br /><br /> ENCRYPTION BY PASSWORD <br />(A partir de [!INCLUDE[sssqlv14_md](../../includes/sssqlv14-md.md)], incluye un número de versión para su uso por CSS.)<br /><br /> ENCRYPTION BY CERTIFICATE<br /><br /> ENCRYPTION BY ASYMMETRIC KEY<br /><br /> ENCRYPTION BY MASTER KEY<br /><br /> Nota: Windows DPAPI se utiliza para proteger la clave maestra de servicio.|  
|**crypt_property**|**varbinary(max)**|Bits firmados o cifrados.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Para obtener más información, consulte [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vea también  
 [Vistas de catálogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Vistas de catálogo de seguridad &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Jerarquía de cifrado](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)  
  
  
