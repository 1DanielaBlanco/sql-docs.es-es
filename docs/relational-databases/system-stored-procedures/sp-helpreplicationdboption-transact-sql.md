---
title: sp_helpreplicationdboption (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
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
- sp_helpreplicationdboption_TSQL
- sp_helpreplicationdboption
helpviewer_keywords:
- sp_helpreplicationdboption
ms.assetid: 143ce689-108b-49d7-9892-fd3a86897f38
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c67c6c6f6f74d3cedf2aa8acc4232886b6d52a9f
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "43038757"
---
# <a name="sphelpreplicationdboption-transact-sql"></a>sp_helpreplicationdboption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Indica si las bases de datos del publicador están habilitadas para la replicación. Este procedimiento almacenado se ejecuta en el publicador de cualquier base de datos. *No se admite para publicadores de Oracle.*  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_helpreplicationdboption [ [ @dbname =] 'dbname' ]  
    [ , [ @type = ] 'type' ]  
    [ , [ @reserved = ] reserved ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@dbname=**] **'***dbname***'**  
 Es el nombre de la base de datos. *dbname* es **sysname**, su valor predeterminado es **%**. Si **%**, a continuación, el conjunto de resultados contiene todas las bases de datos en el publicador, en caso contrario, solo en la base de datos especificado se devuelve información. No se devuelve ninguna información para las bases de datos en que el usuario no tiene los permisos correspondientes según se describe a continuación.  
  
 [  **@type=**] **'***tipo***'**  
 Restringe el conjunto de resultados para contener solo las bases de datos en el que la opción de replicación especificado *tipo* se ha habilitado el valor. *tipo* es **sysname**, y puede tener uno de los siguientes valores.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|**publicar**|La replicación transaccional está permitida.|  
|**publicación de mezcla**|La replicación de mezcla está permitida.|  
|**permitidos la replicación** (valor predeterminado)|La replicación transaccional o de mezcla están permitidas.|  
  
 [  **@reserved=** ] *reservado*  
 Especifica si la información sobre las publicaciones y suscripciones existentes se devuelve. *reservado* es **bit**, con un valor predeterminado de 0. Si **1**, el conjunto de resultados incluye información sobre si la base de datos especificada tiene publicaciones existentes o las suscripciones.  
  
## <a name="result-sets"></a>Conjuntos de resultados  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**Nombre**|**sysname**|Nombre de la base de datos.|  
|**id**|**int**|Identificador de la base de datos.|  
|**transpublish**|**bit**|Si se ha habilitado la base de datos de instantánea o publicación transaccional; el valor **1** significa que la publicación transaccional o instantáneas está habilitada.|  
|**mergepublish**|**bit**|Si se ha habilitado la base de datos para la combinación de publicación; el valor **1** significa que la publicación de combinación está habilitada.|  
|**dbowner**|**bit**|Si el usuario es miembro de la **db_owner** fijo de base de datos; el valor **1** indica que el usuario es miembro de este rol.|  
|**dbReadOnly**|**bit**|Es si la base de datos está marcado como de solo lectura. el valor **1** significa que la base de datos es de solo lectura.|  
|**haspublications**|**bit**|Indica si la base de datos tiene publicaciones existentes; el valor **1** significa que hay publicaciones existentes.|  
|**haspullsubscriptions**|**bit**|Indica si la base de datos tiene las suscripciones de extracción existentes; el valor **1** significa que existen las suscripciones de extracción.|  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Notas  
 **sp_helpreplicationdboption** se utiliza en instantáneas, transaccional y replicación de mezcla.  
  
## <a name="permissions"></a>Permisos  
 Los miembros de la **sysadmin** rol fijo de servidor puede ejecutar **sp_helpreplicationdboption** para cualquier base de datos. Los miembros de la **db_owner** rol fijo de base de datos se puede ejecutar **sp_helpreplicationdboption** para esa base de datos.  
  
## <a name="see-also"></a>Vea también  
 [sp_replicationdboption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md)   
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
