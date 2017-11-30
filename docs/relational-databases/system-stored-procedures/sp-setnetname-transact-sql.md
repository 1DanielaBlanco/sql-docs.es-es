---
title: sp_setnetname (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_setnetname
- sp_setnetname_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_setnetname
ms.assetid: f416ba81-3835-4588-b0a3-2fe75589490e
caps.latest.revision: "31"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7e9f439854cc1d3af3ca5db09981f2eba2af7a4f
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/27/2017
---
# <a name="spsetnetname-transact-sql"></a>sp_setnetname (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Establece los nombres de red **sys.servers** a sus nombres de red del equipo actuales para las instancias remotas de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Este procedimiento puede utilizarse para habilitar la ejecución de llamadas a procedimientos almacenados remotos a equipos cuyos nombres de red contienen identificadores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no válidos.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_setnetname  
@server = 'server',   
     @netname = 'network_name'  
```  
  
## <a name="arguments"></a>Argumentos  
 **@server= '** *server* **'**  
 Es el nombre del servidor remoto tal como se ha especificado en la sintaxis de llamada a procedimiento almacenado remoto codificada por el usuario. Exactamente una fila en **sys.servers** ya debe existir para poder usar este *server*. *server* es de tipo **sysname**y no tiene ningún valor predeterminado.  
  
 **@netname='** *nombre_red* **'**  
 Es el nombre de red del equipo en el que se realizan las llamadas a procedimiento almacenado remoto. *nombre_red* es **sysname**, no tiene ningún valor predeterminado.  
  
 Este nombre debe coincidir con el nombre del equipo con [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows y puede incluir caracteres que no estén admitidos en los identificadores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 0 (correcto) o 1 (error)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
 Ninguno  
  
## <a name="remarks"></a>Comentarios  
 Algunas llamadas a procedimientos almacenados remotos a equipos que ejecutan Windows pueden experimentar problemas si el nombre del equipo contiene identificadores no válidos.  
  
 Debido a que los servidores vinculados y los servidores remotos residen en el mismo espacio de nombres, no pueden tener el mismo nombre. Sin embargo, puede definir un servidor vinculado y un servidor remoto en un servidor especificado asignando nombres distintos y utilizando **sp_setnetname** para establecer el nombre de red de uno de ellos en el nombre de red del servidor subyacente.  
  
```  
--Assume sqlserv2 is actual name of SQL Server   
--database server  
EXEC sp_addlinkedserver 'sqlserv2';  
GO  
EXEC sp_addserver 'rpcserv2';  
GO  
EXEC sp_setnetname 'rpcserv2', 'sqlserv2';  
```  
  
> [!NOTE]  
>  Usar **sp_setnetname** señalar el servidor local de un servidor vinculado no se admite. Los servidores a los que se hace referencia de esta forma no pueden participar en una transacción distribuida.  
  
## <a name="permissions"></a>Permissions  
 Debe pertenecer a la **sysadmin** y **setupadmin** roles fijos de servidor.  
  
## <a name="examples"></a>Ejemplos  
 En el siguiente ejemplo se muestra una secuencia administrativa habitual que se utiliza en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para emitir la llamada a procedimiento almacenado remoto.  
  
```  
USE master;  
GO  
EXEC sp_addserver 'Win_1';  
EXEC sp_setnetname 'Win_1','Win-1';  
EXEC Win_1.master.dbo.sp_who;  
```  
  
## <a name="see-also"></a>Vea también  
 [Motor de base de datos almacenados procedimientos &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_addserver &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
