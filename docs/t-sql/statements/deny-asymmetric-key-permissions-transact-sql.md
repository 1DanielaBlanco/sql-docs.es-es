---
title: DENY (permisos de clave asimétrica de Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- denying permissions [SQL Server], asymmetric keys
- encryption [SQL Server], asymmetric keys
- permissions [SQL Server], asymmetric keys
- asymmetric keys [SQL Server], permissions
- DENY statement, asymmetric keys
- cryptography [SQL Server], asymmetric keys
ms.assetid: dd7d8cd5-536b-460c-ab5b-cb4752bbdfaa
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: e8724bbb6ed005fb23e51b875372b49fbb9639ad
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="deny-asymmetric-key-permissions-transact-sql"></a>DENY permisos de clave asimétrica (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Deniega permisos sobre una clave asimétrica.  
   
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
DENY { permission  [ ,...n ] }   
    ON ASYMMETRIC KEY :: asymmetric_key_name   
        TO database_principal [ ,...n ]  
    [ CASCADE ]  
        [ AS denying_principal ]  
```  
  
## <a name="arguments"></a>Argumentos  
 *permission*  
 Especifica un permiso que se puede denegar para una clave asimétrica. Se muestra a continuación.  
  
 ON ASYMMETRIC KEY **::***asymmetric_key_name*  
 Especifica la clave asimétrica para la que se deniega el permiso. Es preciso utilizar el calificador de ámbito "::".  
  
 *database_principal*  
 Especifica la entidad de seguridad a la que se deniega el permiso. Uno de los siguientes:  
  
-   usuario de base de datos  
  
-   rol de base de datos  
  
-   rol de aplicación  
  
-   usuario de base de datos asignado a un inicio de sesión de Windows  
  
-   usuario de base de datos asignado a un grupo de Windows  
  
-   usuario de base de datos asignado a un certificado  
  
-   usuario de base de datos asignado a una clave asimétrica  
  
-   usuario de base de datos no asignado a una entidad de seguridad del servidor  
  
 CASCADE  
 Indica que el permiso que se va a denegar también se denegará a otras entidades de seguridad a las que esta entidad de seguridad ha concedido permisos.  
  
 *denying_principal*  
 Especifica una entidad de seguridad de la que la entidad de seguridad que ejecuta esta consulta deriva su derecho de denegar el permiso. Uno de los siguientes:  
  
-   usuario de base de datos  
  
-   rol de base de datos  
  
-   rol de aplicación  
  
-   usuario de base de datos asignado a un inicio de sesión de Windows  
  
-   usuario de base de datos asignado a un grupo de Windows  
  
-   usuario de base de datos asignado a un certificado  
  
-   usuario de base de datos asignado a una clave asimétrica  
  
-   usuario de base de datos no asignado a una entidad de seguridad del servidor  
  
## <a name="remarks"></a>Notas  
 Una clave asimétrica es un elemento protegible de nivel de base de datos que contiene la base de datos que es su entidad primaria en la jerarquía de permisos. A continuación, se enumeran los permisos más específicos y limitados que se pueden conceder para una clave asimétrica, además de los permisos más generales que los incluyen implícitamente.  
  
|Permiso de clave asimétrica|Implícito en el permiso de clave asimétrica|Implícito en el permiso de base de datos|  
|-------------------------------|------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY ASYMMETRIC KEY|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permisos  
 Requiere permiso CONTROL en la clave asimétrica. Si se utiliza la cláusula AS, la entidad de seguridad especificada debe poseer la clave asimétrica.  
  
## <a name="see-also"></a>Ver también  
 [DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)   
 [Permisos &#40;motor de base de datos&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Entidades de seguridad &#40;motor de base de datos&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [Jerarquía de cifrado](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
