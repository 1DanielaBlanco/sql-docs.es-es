---
title: DECRYPTBYCERT (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DecryptByCert_TSQL
- DECRYPTBYCERT
dev_langs:
- TSQL
helpviewer_keywords:
- certificates [SQL Server], decryption
- decryption [SQL Server], certificates
- DECRYPTBYCERT function
ms.assetid: 4950d787-40fa-4e26-bce8-2cb2ceca12fb
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b49bdceb3d27af9c252739938ca9ec309f1510ec
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="decryptbycert-transact-sql"></a>DECRYPTBYCERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Descifra datos con la clave privada de un certificado.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
DecryptByCert ( certificate_ID , { 'ciphertext' | @ciphertext }   
    [ , { 'cert_password' | @cert_password } ] )  
```  
  
## <a name="arguments"></a>Argumentos  
 *certificate_ID*  
 Es el identificador de un certificado de la base de datos. *certificate*_ID es **int**.  
  
 *ciphertext*  
 Es una cadena de datos que se ha cifrado con la clave pública del certificado.  
  
 @ciphertext  
 Es una variable de tipo **varbinary** que contiene los datos que se han cifrado con el certificado.  
  
 *cert_password*  
 Es la contraseña utilizada para cifrar la clave privada del certificado. Debe ser Unicode.  
  
 @cert_password  
 Es una variable de tipo **nchar** o **nvarchar** que contiene la contraseña usada para cifrar la clave privada del certificado. Debe ser Unicode.  
  
## <a name="return-types"></a>Tipos devueltos  
 **varbinary** con un tamaño máximo de 8000 bytes.  
  
## <a name="remarks"></a>Notas  
 Esta función descifra datos con la clave privada de un certificado. Las transformaciones cifradas que utilizan claves asimétricas consumen gran cantidad de recursos. Por tanto, EncryptByCert y DecryptByCert no resultan adecuados para el cifrado rutinario de datos de usuario.  
  
## <a name="permissions"></a>Permisos  
 Requiere el permiso CONTROL en el certificado.  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se seleccionan filas de `[AdventureWorks2012].[ProtectedData04]` marcadas como `data encrypted by certificate JanainaCert02`. En el ejemplo se descifra el texto cifrado con la clave privada del certificado `JanainaCert02`, que se descifra previamente con la contraseña del certificado, `pGFD4bb925DGvbd2439587y`. Los datos descifrados se convierten de **varbinary** a **nvarchar**.  
  
```  
SELECT convert(nvarchar(max), DecryptByCert(Cert_Id('JanainaCert02'),  
    ProtectedData, N'pGFD4bb925DGvbd2439587y'))  
FROM [AdventureWorks2012].[ProtectedData04]   
WHERE Description   
    = N'data encrypted by certificate '' JanainaCert02''';  
GO  
```  
  
## <a name="see-also"></a>Ver también  
 [ENCRYPTBYCERT &#40;Transact-SQL&#41;](../../t-sql/functions/encryptbycert-transact-sql.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [ALTER CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [DROP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-certificate-transact-sql.md)   
 [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/backup-certificate-transact-sql.md)   
 [Jerarquía de cifrado](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
