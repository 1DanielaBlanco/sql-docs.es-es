---
title: Crear clave de cifrado de base de datos (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 08/24/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATABASE_ENCRYPTION_KEY_TSQL
- ENCRYPTION_KEY_TSQL
- sql13.swb.dbencryptionkeyo.f1
- ENCRYPTION KEY
- DATABASE ENCRYPTION KEY
- CREATE_DATABASE_ENCRYPTION_KEY_TSQL
- CREATE DATABASE ENCRYPTION KEY
- sql13.swb.dbencryptionkeyg.f1
- CREATE DATABASE ENCRYPTION
- CREATE_DATABASE_ENCRYPTION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database encryption key
- CREATE DATABASE ENCRYPTION KEY statement
- database encryption key, create
ms.assetid: 2ee95a32-5140-41bd-9ab3-a947b9990688
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 559e85cf5ba8e565a6afc86d3537b476365bd980
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="create-database-encryption-key-transact-sql"></a>CREATE DATABASE ENCRYPTION KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

 Crea una clave de cifrado que se utiliza para cifrar de forma transparente una base de datos. Para obtener más información acerca del cifrado de base de datos transparente, consulte [cifrado de datos transparente &#40; TDE &#41; ](../../relational-databases/security/encryption/transparent-data-encryption.md).  
  
![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
-- Syntax for SQL Server  

CREATE DATABASE ENCRYPTION KEY  
       WITH ALGORITHM = { AES_128 | AES_192 | AES_256 | TRIPLE_DES_3KEY }  
   ENCRYPTION BY SERVER   
    {  
        CERTIFICATE Encryptor_Name |  
        ASYMMETRIC KEY Encryptor_Name  
    }  
[ ; ]  
```  
  
```  
-- Syntax for Parallel Data Warehouse  

CREATE DATABASE ENCRYPTION KEY  
       WITH ALGORITHM = { AES_128 | AES_192 | AES_256 | TRIPLE_DES_3KEY }  
   ENCRYPTION BY SERVER CERTIFICATE Encryptor_Name   
[ ; ]  
```  
  
## <a name="arguments"></a>Argumentos  
WITH ALGORITHM = { AES_128 | AES_192 | AES_256 | TRIPLE_DES_3KEY  }  
Especifica el algoritmo de cifrado utilizado para la clave de cifrado.   
>  [!NOTE]
>    A partir de SQL Server 2016, todos los algoritmos AES_128, AES_192 y AES_256 están en desuso. Para usar algoritmos anteriores (no se recomienda), debe establecer la base de datos en el nivel de compatibilidad de base de datos 120 o inferior.  
  
CIFRADO de Encryptor_Name de certificado de servidor  
Especifica el nombre del sistema de cifrado utilizado para cifrar la clave de cifrado.  
  
CIFRADO de Encryptor_Name de clave ASIMÉTRICA de servidor  
Especifica el nombre de la clave asimétrica que se usa para cifrar la clave de cifrado de base de datos. Para cifrar la clave de cifrado de la base de datos con una clave asimétrica, la clave asimétrica debe residir en un proveedor extensible de administración de claves.  
  
## <a name="remarks"></a>Comentarios  
Se requiere una clave de cifrado de base de datos antes de que una base de datos se puede cifrar mediante *cifrado de base de datos transparente* (TDE). Cuando se cifra una base de datos de forma transparente, toda la base de datos se cifra en el nivel de archivo, sin ninguna modificación especial de código. El certificado o la clave asimétrica que se usa para cifrar la clave de cifrado de base de datos se debe ubicar en la base de datos maestra del sistema.  
  
Las instrucciones de cifrado de la base de datos se permiten únicamente en bases de datos de usuario.  
  
La clave de cifrado de la base de datos no se puede exportar de la base de datos. Solo está disponible para el sistema, para los usuarios que tienen los permisos de depuración en el servidor y para los usuarios que tienen acceso a los certificados que cifran y descifran la clave de cifrado de la base de datos.  
  
La clave de cifrado de base de datos no tiene que regenerarse cuando se cambia el propietario de la base de datos (dbo).  
  
Una clave de cifrado de base de datos se crea automáticamente un [!INCLUDE[ssSDS](../../includes/sssds-md.md)] base de datos. No es necesario crear una clave mediante la instrucción CREATE DATABASE ENCRYPTION KEY.  
  
## <a name="permissions"></a>Permissions  
Requiere el permiso CONTROL en la base de datos y el permiso VIEW DEFINITION en el certificado o la clave asimétrica utilizados para cifrar la clave de cifrado de base de datos.  
  
## <a name="examples"></a>Ejemplos  
Para obtener más ejemplos con TDE, vea [cifrado de datos transparente &#40; TDE &#41; ](../../relational-databases/security/encryption/transparent-data-encryption.md), [Habilitar TDE en SQL Server con EKM](../../relational-databases/security/encryption/enable-tde-on-sql-server-using-ekm.md), y [administración Extensible de claves con almacén de claves de Azure &#40; SQL Server &#41; ](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md).  
  
En el siguiente ejemplo se crea una clave de cifrado de base de datos mediante el algoritmo `AES_256` y se protege la clave privada con un certificado denominado `MyServerCert`.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE DATABASE ENCRYPTION KEY  
WITH ALGORITHM = AES_256  
ENCRYPTION BY SERVER CERTIFICATE MyServerCert;  
GO  
```  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Ejemplos:[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
Para obtener más ejemplos con TDE, vea [cifrado de datos transparente (SQL Server PDW)](http://msdn.microsoft.com/en-us/b82ad21d-09dd-43dd-8fab-bcf2c8c3ac6d).  
  
En el siguiente ejemplo se crea una clave de cifrado de base de datos mediante el algoritmo `AES_256` y se protege la clave privada con un certificado denominado `MyServerCert`.  
  
```  
-- Uses AdventureWorks  
  
CREATE DATABASE ENCRYPTION KEY  
WITH ALGORITHM = AES_256  
ENCRYPTION BY SERVER CERTIFICATE MyServerCert;  
GO  
```  
  
## <a name="see-also"></a>Vea también  
[Cifrado de datos transparente &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md)   
[Cifrado de SQL Server](../../relational-databases/security/encryption/sql-server-encryption.md)   
[SQL Server y claves de cifrado de base de datos &#40;motor de base de datos&#41;](../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)   
[Jerarquía de cifrado](../../relational-databases/security/encryption/encryption-hierarchy.md)   
[Opciones de ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
[ALTER DATABASE ENCRYPTION KEY &#40; Transact-SQL &#41;](../../t-sql/statements/alter-database-encryption-key-transact-sql.md)   
[DROP DATABASE ENCRYPTION KEY &#40; Transact-SQL &#41;](../../t-sql/statements/drop-database-encryption-key-transact-sql.md)   
[sys.dm_database_encryption_keys &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md)  
    

