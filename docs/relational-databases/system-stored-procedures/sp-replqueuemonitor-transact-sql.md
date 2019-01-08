---
title: sp_replqueuemonitor (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replqueuemonitor
- sp_replqueuemonitor_TSQL
helpviewer_keywords:
- sp_replqueuemonitor
ms.assetid: 6909a3f1-43a2-4df5-a6a5-9e6f347ac841
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e8eb21085625c7f2f0071c18da80501774088fdc
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2018
ms.locfileid: "52789377"
---
# <a name="spreplqueuemonitor-transact-sql"></a>sp_replqueuemonitor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enumera los mensajes en cola desde un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cola o [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queue Server para suscripciones de actualización en cola a una publicación específica. Si se utilizan colas de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], el procedimiento almacenado se ejecuta en el suscriptor de la base de datos de suscripciones. Si se utiliza Message Queue Server, este procedimiento almacenado se ejecuta en el distribuidor de la base de datos de distribución.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_replqueuemonitor [ @publisher = ] 'publisher'  
    [ , [ @publisherdb = ] 'publisher_db' ]  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @tranid = ] 'tranid' ]  
    [ , [ @queuetype = ] 'queuetype' ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [ **@publisher** =] **'***publisher***'**  
 Es el nombre del publicador. *publicador* es **sysname**, su valor predeterminado es null. El servidor debe estar configurado para publicación. Su valor es NULL para todos los publicadores.  
  
 [ **@publisherdb** =] **'***publisher_db***'** ]  
 Es el nombre de la base de datos de publicación. *publisher_db* es **sysname**, su valor predeterminado es null. Su valor es NULL para todas las bases de datos de publicaciones.  
  
 [ **@publication** =] **'***publicación***'** ]  
 Es el nombre de la publicación. *publicación*es **sysname**, su valor predeterminado es null. Su valor es NULL para todas las publicaciones.  
  
 [ **@tranid** =] **'***la transacción***'** ]  
 Es el identificador de la transacción. *la transacción*es **sysname**, su valor predeterminado es null. Su valor es NULL para todas las transacciones.  
  
 [**@queuetype=** ] **'***queuetype***'** ]  
 Es el tipo de cola que almacena las transacciones. *queuetype* es **tinyint** con un valor predeterminado de **0**, y puede tener uno de estos valores.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|**0**|Todos los tipos de colas|  
|**1**|Message Queue Server|  
|**2**|Cola de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Comentarios  
 **sp_replqueuemonitor** se usa en la replicación de instantáneas o replicación transaccional con suscripciones de actualización en cola. No muestra los mensajes de la cola que no contienen comandos SQL o que forman parte de un comando SQL múltiple.  
  
## <a name="permissions"></a>Permisos  
 Solo los miembros de la **sysadmin** rol fijo de servidor o **db_owner** rol fijo de base de datos se puede ejecutar **sp_replqueuemonitor**.  
  
## <a name="see-also"></a>Vea también  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
