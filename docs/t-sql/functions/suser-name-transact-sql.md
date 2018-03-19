---
title: SUSER_NAME (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SUSER_NAME
- SUSER_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- security identification names [SQL Server]
- logins [SQL Server], users
- identification names for logins [SQL Server]
- users [SQL Server], logins
- SUSER_NAME function
- logins [SQL Server], names
- names [SQL Server], logins
ms.assetid: ae598d9f-9baa-49b8-b1c1-042854206de4
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: cb236dc3ae7f74ad77ba398e328d4a0bf93a079b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="susername-transact-sql"></a>SUSER_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-xxx-md.md)]

  Devuelve el nombre de identificación de inicio de sesión del usuario.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
SUSER_NAME ( [ server_user_id ] )   
```  
  
## <a name="arguments"></a>Argumentos  
 *server_user_id*  
 Es el número de identificación de inicio de sesión del usuario. *server_user_id*, que es opcional, es de tipo **int**. *server_user_id* puede ser el número de identificación de inicio de sesión de cualquier inicio de sesión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o de cualquier usuario o grupo de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows que tenga permiso para conectarse a una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si no se especifica *server_user_id*, se devuelve el nombre de identificación de inicio de sesión para el usuario actual. Si el parámetro contiene la palabra NULL, se devolverá NULL.  
  
## <a name="return-types"></a>Tipos devueltos  
 **nvarchar(128)**  
  
## <a name="remarks"></a>Notas  
 En [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versión 7.0, el número de identificación de seguridad (SID) reemplaza al número de identificación de usuario del servidor (SUID).  
  
 SUSER_NAME solo devuelve un nombre de un inicio de sesión que tenga una entrada en la tabla del sistema **syslogins**.  
  
 SUSER_NAME se puede utilizar en una lista de selección, en una cláusula WHERE y en cualquier lugar donde se admita una expresión, pero deberá ir seguido siempre de paréntesis, incluso si no se especifica ningún parámetro.  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se devuelve el nombre de identificación de inicio de sesión del usuario con el número de identificación de inicio de sesión `1`.  
  
```  
SELECT SUSER_NAME(1);  
```  
  
## <a name="see-also"></a>Ver también  
 [SUSER_ID &#40;Transact-SQL&#41;](../../t-sql/functions/suser-id-transact-sql.md)   
 [Entidades de seguridad &#40;motor de base de datos&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
