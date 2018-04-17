---
title: sp_dropsubscription (Transact-SQL) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_dropsubscription
- sp_dropsubscription_TSQL
helpviewer_keywords:
- sp_dropsubscription
ms.assetid: 7551f345-5510-4684-ab53-f9057249d13a
caps.latest.revision: 23
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 85d2d9188f84d4d2dac6167180013d1e659de3de
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="spdropsubscription-transact-sql"></a>sp_dropsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Quita las suscripciones a un artículo, publicación o conjunto de suscripciones específico del publicador. Este procedimiento almacenado se ejecuta en el publicador de la base de datos de publicación.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_dropsubscription [ [ @publication= ] 'publication' ]  
    [ , [ @article= ] 'article' ]  
        , [ @subscriber= ] 'subscriber'  
    [ , [ @destination_db= ] 'destination_db' ]  
    [ , [ @ignore_distributor = ] ignore_distributor ]  
    [ , [ @reserved= ] 'reserved' ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@publication=** ] **'***publicación***'**  
 Es el nombre de la publicación asociada. *publicación* es **sysname**, su valor predeterminado es null. Si **todos los**, se cancelan todas las suscripciones de todas las publicaciones del suscriptor indicado. *publicación* es un parámetro necesario.  
  
 [  **@article=** ] **'***artículo***'**  
 Es el nombre del artículo. *artículo* es **sysname**, su valor predeterminado es null. Si **todos los**, especifican suscripciones a todos los artículos de cada publicación y suscriptor se quitan. Use **todos los** para publicaciones que permiten la inmediatas de actualización.  
  
 [  **@subscriber=** ] **' ***suscribirse*r**' **  
 Es el nombre del suscriptor cuyas suscripciones se van a quitar. *suscriptor* es **sysname**, no tiene ningún valor predeterminado. Si **todos los**, se quitan todas las suscripciones para todos los suscriptores.  
  
 [  **@destination_db=** ] **'***destination_db***'**  
 Es el nombre de la base de datos de destino. *destination_db* es **sysname**, su valor predeterminado es null. Cuando es NULL, se quitan todas las suscripciones del suscriptor indicado.  
  
 [  **@ignore_distributor =** ] *ignore_distributor*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@reserved=** ] **'***reservada***'**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Comentarios  
 **sp_dropsubscription** se utiliza en la replicación de instantáneas y transaccional.  
  
 Si quita la suscripción a un artículo de una publicación de sincronización inmediata, no podrá volverla a agregar, a menos que quite las suscripciones a todos los artículos de la publicación y las agregue de nuevo todas a la vez.  
  
## <a name="example"></a>Ejemplo  
 [!code-sql[HowTo#sp_droptransubscription](../../relational-databases/replication/codesnippet/tsql/sp-dropsubscription-tran_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 Solo los miembros de la **sysadmin** rol fijo de servidor, el **db_owner** rol fijo de base de datos o el usuario que creó la suscripción puede ejecutar **sp_dropsubscription**.  
  
## <a name="see-also"></a>Vea también  
 [Eliminar una suscripción de inserción](../../relational-databases/replication/delete-a-push-subscription.md)   
 [sp_addsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_changesubstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubstatus-transact-sql.md)   
 [sp_helpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
