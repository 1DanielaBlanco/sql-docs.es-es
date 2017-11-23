---
title: USER_ID (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- USER_ID
- USER_ID_TSQL
dev_langs: TSQL
helpviewer_keywords:
- USER_ID function
- identification numbers [SQL Server]
- IDs [SQL Server], databases
- users [SQL Server], database ID numbers
- database IDs [SQL Server]
- identification numbers [SQL Server], databases
ms.assetid: 67fd29bc-eda9-4d4d-b148-5d3659181a43
caps.latest.revision: "31"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c8c8e07d6d58b6615ff5e4528556bf08e0b72c13
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="userid-transact-sql"></a>USER_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Devuelve el número de identificación para un usuario de la base de datos.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Use [DATABASE_PRINCIPAL_ID](../../t-sql/functions/database-principal-id-transact-sql.md) en su lugar.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
USER_ID ( [ 'user' ] )  
```  
  
## <a name="arguments"></a>Argumentos  
 *usuario*  
 Es el nombre de usuario que se va a emplear. *usuario* es **nchar**. Si un **char** valor se especifica, se convierte implícitamente en **nchar**. Es obligatorio utilizar paréntesis.  
  
## <a name="return-types"></a>Tipos devueltos  
 **int**  
  
## <a name="remarks"></a>Comentarios  
 Cuando *usuario* es se omite, se supone que el usuario actual. Si el parámetro contiene la palabra NULL, devolverá NULL. Cuando se llama a USER_ID después de EXECUTE AS, USER_ID devuelve el identificador del contexto suplantado.  
  
 Cuando una entidad de seguridad de Windows que no se ha asignado a un usuario específico de base de datos tiene acceso a una base de datos en forma de pertenencia a un grupo, USER_ID devuelve 0 (el identificador de público). Si este tipo de entidad de seguridad crea un objeto sin especificar un esquema, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] creará un usuario implícito y un esquema asignados a dicha entidad. El usuario creado en casos como éste no se puede utilizar para conectarse a la base de datos. Las llamadas a USER_ID efectuadas por la entidad de seguridad de Windows asignada a un usuario implícito devolverán el identificador de éste.  
  
 Se puede utilizar USER_ID en una lista de selección, en una cláusula WHERE y en cualquier lugar en el que se permita una expresión. Para obtener más información, vea [Expresiones &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md).  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se devuelve el número de identificación para el usuario `AdventureWorks2012` de `Harold`.  
  
```  
USE AdventureWorks2012;  
SELECT USER_ID('Harold');  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [User_name &#40; Transact-SQL &#41;](../../t-sql/functions/user-name-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [DATABASE_PRINCIPAL_ID &#40; Transact-SQL &#41;](../../t-sql/functions/database-principal-id-transact-sql.md)   
 [Funciones de seguridad &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  
