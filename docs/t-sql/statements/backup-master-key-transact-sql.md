---
title: BACKUP MASTER KEY (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- BACKUP MASTER KEY
- DUMP_MASTER_KEY_TSQL
- BACKUP_MASTER_KEY_TSQL
- DUMP MASTER KEY
dev_langs:
- TSQL
helpviewer_keywords:
- BACKUP MASTER KEY statement
- exporting Database Master Keys
- encryption [SQL Server], Database Master Key
- cryptography [SQL Server], Database Master Key
- backing up master keys [SQL Server]
- database master key [SQL Server], exporting
ms.assetid: 0e25fe22-2536-4d7e-ba4a-1921e880f367
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 53a7ad02a9553859bbf44288038dcb1b9e48538b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="backup-master-key-transact-sql"></a>BACKUP MASTER KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Exporta la clave maestra de base de datos.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
BACKUP MASTER KEY TO FILE = 'path_to_file'   
    ENCRYPTION BY PASSWORD = 'password'  
```  
  
## <a name="arguments"></a>Argumentos  
 FILE ='*path_to_file*'  
 Especifica la ruta de acceso completa, incluido el nombre de archivo, al archivo al que se exportará la clave maestra. Puede ser una ruta local o una ruta UNC a una ubicación de red.  
  
 PASSWORD ='*password*'  
 Es la contraseña utilizada para cifrar la clave maestra del archivo. Esta contraseña se somete a comprobaciones de complejidad. Para obtener más información, vea [Password Policy](../../relational-databases/security/password-policy.md).  
  
## <a name="remarks"></a>Notas  
 Es necesario abrir la clave maestra y, por tanto, descifrarla antes de realizar una copia de seguridad de la misma. Si está cifrada con la clave maestra de servicio, no es necesario abrir explícitamente la clave maestra. Pero si la clave maestra solo está cifrada con una contraseña, debe abrirse explícitamente.  
  
 Se recomienda realizar una copia de seguridad de la clave maestra inmediatamente después de crearla y guardarla en un lugar seguro y alejado de las instalaciones.  
  
## <a name="permissions"></a>Permisos  
 Necesita el permiso CONTROL en la base de datos.  
  
## <a name="examples"></a>Ejemplos  
 En el siguiente ejemplo se crea una copia de seguridad de la clave maestra de `AdventureWorks2012`. Dado que la clave maestra no está cifrada con la clave maestra de servicio, es necesario especificar una contraseña para abrirla.  
  
```  
USE AdventureWorks2012;  
OPEN MASTER KEY DECRYPTION BY PASSWORD = 'sfj5300osdVdgwdfkli7';  
BACKUP MASTER KEY TO FILE = 'c:\temp\exportedmasterkey'   
    ENCRYPTION BY PASSWORD = 'sd092735kjn$&adsg';  
GO   
```  
  
## <a name="see-also"></a>Ver también  
 [CREATE MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-master-key-transact-sql.md)   
 [OPEN MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/open-master-key-transact-sql.md)   
 [CLOSE MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/close-master-key-transact-sql.md)   
 [RESTORE MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-master-key-transact-sql.md)   
 [ALTER MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-master-key-transact-sql.md)   
 [DROP MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-master-key-transact-sql.md)   
 [Jerarquía de cifrado](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
