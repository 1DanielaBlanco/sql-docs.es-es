---
title: ALTER CERTIFICATE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/18/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ALTER_CERTIFICATE_TSQL
- ALTER CERTIFICATE
dev_langs:
- TSQL
helpviewer_keywords:
- ENCRYPTION BY PASSWORD option
- encryption [SQL Server], certificates
- modifying certificates
- private keys [SQL Server]
- ALTER CERTIFICATE statement
- certificates [SQL Server], modifying
ms.assetid: da4dc25e-72e0-4036-87ce-22de83160836
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bba8adc043d5fa98f1d9c1773952f6366518823b
ms.sourcegitcommit: c6e71ed14198da67afd7ba722823b1af9b4f4e6f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54326706"
---
# <a name="alter-certificate-transact-sql"></a>ALTER CERTIFICATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-pdw-md.md)]

  Cambia la clave privada que se utiliza para cifrar un certificado o agrega una si no existe. Cambia la disponibilidad de un certificado a [!INCLUDE[ssSB](../../includes/sssb-md.md)].  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
ALTER CERTIFICATE certificate_name   
      REMOVE PRIVATE KEY  
    | WITH PRIVATE KEY ( <private_key_spec> [ ,... ] )  
    | WITH ACTIVE FOR BEGIN_DIALOG = [ ON | OFF ]  
  
<private_key_spec> ::=   
      FILE = 'path_to_private_key'   
    | DECRYPTION BY PASSWORD = 'key_password'   
    | ENCRYPTION BY PASSWORD = 'password'   
```  
  
```  
-- Syntax for Parallel Data Warehouse  
  
ALTER CERTIFICATE certificate_name   
{  
      REMOVE PRIVATE KEY  
    | WITH PRIVATE KEY (   
        FILE = '<path_to_private_key>',  
        DECRYPTION BY PASSWORD = '<key password>' )
}  
```  
  
## <a name="arguments"></a>Argumentos  
 *certificate_name*  
 Nombre único por el que se conoce al certificado en la base de datos.  
  
 FILE **='**_path\_to\_private\_key_**'**  
 Especifica la ruta de acceso completa a la clave privada, incluido el nombre de archivo. Este parámetro puede ser una ruta de acceso local o una ruta de acceso UNC a una ubicación de red. Se obtiene acceso a este archivo dentro del contexto de seguridad de la cuenta del servicio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cuando utilice esta opción, asegúrese de que la cuenta de servicio tenga acceso al archivo especificado.  
  
 DECRYPTION BY PASSWORD **='**_key\_password_**'**  
 Especifica la contraseña necesaria para descifrar la clave privada.  
  
 ENCRYPTION BY PASSWORD **='**_password_**'**  
 Especifica la contraseña que se usa para cifrar la clave privada del certificado en la base de datos. *password* debe cumplir los requisitos de la directiva de contraseñas de Windows del equipo que ejecuta la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Para obtener más información, vea [Password Policy](../../relational-databases/security/password-policy.md).  
  
 REMOVE PRIVATE KEY  
 Indica que no debe seguir manteniéndose la clave privada en la base de datos.  
  
 ACTIVE FOR BEGIN_DIALOG **=** { ON | OFF }  
 Hace que el certificado esté disponible para el iniciador de una conversación de diálogo de [!INCLUDE[ssSB](../../includes/sssb-md.md)].  
  
## <a name="remarks"></a>Notas  
 La clave privada debe corresponderse con la clave pública especificada por *certificate_name*.  
  
 Puede omitir la cláusula DECRYPTION BY PASSWORD si la contraseña del archivo está protegida mediante una contraseña NULL.  
  
 Cuando la clave privada de un certificado que ya existe en la base de datos se importa desde un archivo, esta clave privada se protegerá automáticamente mediante la clave maestra de la base de datos. Para proteger la clave privada con una contraseña, utilice la frase ENCRYPTION BY PASSWORD.  
  
 La opción REMOVE PRIVATE KEY eliminará de la base de datos la clave privada del certificado. Puede quitar la clave privada cuando el certificado se utilice para comprobar firmas o en escenarios de [!INCLUDE[ssSB](../../includes/sssb-md.md)] que no necesiten una clave privada. No elimine la clave privada de un certificado que proteja una clave simétrica.  
  
 No es necesario especificar una contraseña de descifrado cuando la clave privada se ha cifrado mediante la clave maestra de la base de datos.  
  
> [!IMPORTANT]  
>  Haga siempre una copia de archivo de una clave privada antes de quitarla de una base de datos. Para obtener más información, vea [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/backup-certificate-transact-sql.md).  
  
 La opción WITH PRIVATE KEY no está disponible en una base de datos independiente.  
  
## <a name="permissions"></a>Permisos  
 Requiere el permiso ALTER en el certificado.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-changing-the-password-of-a-certificate"></a>A. Cambiar la contraseña de un certificado  
  
```  
ALTER CERTIFICATE Shipping04   
    WITH PRIVATE KEY (DECRYPTION BY PASSWORD = 'pGF$5DGvbd2439587y',  
    ENCRYPTION BY PASSWORD = '4-329578thlkajdshglXCSgf');  
GO  
```  
  
### <a name="b-changing-the-password-that-is-used-to-encrypt-the-private-key"></a>b. Cambiar la contraseña utilizada para cifrar una clave privada  
  
```  
ALTER CERTIFICATE Shipping11   
    WITH PRIVATE KEY (ENCRYPTION BY PASSWORD = '34958tosdgfkh##38',  
    DECRYPTION BY PASSWORD = '95hkjdskghFDGGG4%');  
GO  
```  
  
### <a name="c-importing-a-private-key-for-a-certificate-that-is-already-present-in-the-database"></a>C. Importar una clave privada para un certificado que ya existe en la base de datos  
  
```  
ALTER CERTIFICATE Shipping13   
    WITH PRIVATE KEY (FILE = 'c:\\importedkeys\Shipping13',  
    DECRYPTION BY PASSWORD = 'GDFLKl8^^GGG4000%');  
GO  
```  
  
### <a name="d-changing-the-protection-of-the-private-key-from-a-password-to-the-database-master-key"></a>D. Cambiar la protección de una clave privada, desde una contraseña a la clave maestra de la base de datos  
  
```  
ALTER CERTIFICATE Shipping15   
    WITH PRIVATE KEY (DECRYPTION BY PASSWORD = '95hk000eEnvjkjy#F%');  
GO  
```  
  
## <a name="see-also"></a>Consulte también  
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [DROP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-certificate-transact-sql.md)   
 [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/backup-certificate-transact-sql.md)   
 [Jerarquía de cifrado](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

