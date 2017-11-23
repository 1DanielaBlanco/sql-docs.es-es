---
title: sp_helpserver (Transact-SQL) | Documentos de Microsoft
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
- sp_helpserver
- sp_helpserver_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_helpserver
ms.assetid: e8f42de7-c738-41c3-8bf5-dbd559dc7184
caps.latest.revision: "21"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 31e66de5957e55dfe3676a30ec435c303df910f0
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="sphelpserver-transact-sql"></a>sp_helpserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Presenta información acerca de un servidor remoto o de replicación concreto, o acerca de todos los servidores de los dos tipos. Proporciona la siguiente información sobre el servidor: nombre, nombre de red, estado de replicación, número de identificación y nombre de intercalación. Asimismo proporciona valores de tiempo de espera para conectarse a servidores vinculados o para realizar consultas en los mismos.  
  
||  
|-|  
|**Se aplica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a través de la [versión actual](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_helpserver [ [ @server = ] 'server' ]   
  [ , [ @optname = ] 'option' ]   
  [ , [ @show_topology = ] 'show_topology' ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@server =** ] **'***server***'**  
 Es el servidor cuya información se va a presentar. Cuando *server* no se especifica, los informes sobre todos los servidores de **master.sys.servers**. *servidor* es **sysname**, su valor predeterminado es null.  
  
 [  **@optname =** ] **'***opción***'**  
 Es la opción que describe al servidor. *opción* es **varchar (**35**)**, su valor predeterminado es null y debe ser uno de estos valores.  
  
|Valor|Description|  
|-----------|-----------------|  
|**intercalación compatible**|Afecta a la ejecución de consultas distribuidas sobre servidores vinculados. Si esta opción se establece en TRUE,|  
|**acceso a datos**|Habilita y deshabilita un servidor vinculado para el acceso a consultas distribuidas.|  
|**Dist**|Distribuidor.|  
|**dpub**|Publicador remoto de este distribuidor.|  
|**validación diferida de esquema**|Omite la comprobación del esquema de las tablas remotas al comienzo de la consulta.|  
|**pub**|Publicador.|  
|**RPC**|Habilita RPC desde el servidor especificado.|  
|**RPC fuera**|Habilita RPC en el servidor especificado.|  
|**Sub**|Suscriptor.|  
|**sistema**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**Usar intercalación remota**|Usa la intercalación de una columna remota en lugar de la del servidor local.|  
  
 [  **@show_topology =** ] **'***show_topology***'**  
 Es la relación del servidor especificado con otros servidores. *show_topology* es **varchar (**1**)**, su valor predeterminado es null. Si *show_topology* no es igual a **t** o es NULL, **sp_helpserver** devuelve columnas enumeradas en la sección de conjuntos de resultados. Si *show_topology* es igual a **t**, además de las columnas enumeradas en los conjuntos de resultados, **sp_helpserver** también devuelve **topx** y **topy** información.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 0 (correcto) o 1 (error).  
  
## <a name="result-sets"></a>Conjuntos de resultados  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**Nombre**|**sysname**|Nombre de servidor.|  
|**nombre_red**|**sysname**|El nombre de red del servidor.|  
|**status**|**varchar (**70**)**|Estado del servidor.|  
|**id**|**Char (**4**)**|Número de identificación del servidor.|  
|**collation_name**|**sysname**|Intercalación del servidor.|  
|**connect_timeout**|**int**|Valor del tiempo de espera para conectar a un servidor vinculado.|  
|**query_timeout**|**int**|Valor del tiempo de espera para consultas sobre un servidor vinculado.|  
  
## <a name="remarks"></a>Comentarios  
 Un servidor puede tener varios estados.  
  
## <a name="permissions"></a>Permissions  
 No se comprueba ningún permiso.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-displaying-information-about-all-servers"></a>A. Presentar información acerca de todos los servidores  
 En este ejemplo se presenta información acerca de todos los servidores mediante el uso de `sp_helpserver` sin parámetros.    
  
```  
USE master;  
GO  
EXEC sp_helpserver;  
```  
  
### <a name="b-displaying-information-about-a-specific-server"></a>B. Presentar información acerca de un servidor específico  
 En este ejemplo se presenta toda la información acerca del servidor `SEATTLE2`.  
  
```  
USE master;  
GO  
EXEC sp_helpserver 'SEATTLE2';  
```  
  
## <a name="see-also"></a>Vea también  
 [Motor de base de datos almacenados procedimientos &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_adddistpublisher &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_addserver &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [sp_addsubscriber &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addsubscriber-transact-sql.md)   
 [sp_changesubscriber &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql.md)   
 [sp_dropserver &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dropserver-transact-sql.md)   
 [sp_dropsubscriber &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dropsubscriber-transact-sql.md)   
 [sp_helpdistributor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [sp_helpremotelogin &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpremotelogin-transact-sql.md)   
 [sp_helpsubscriberinfo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md)   
 [sp_serveroption &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-serveroption-transact-sql.md)   
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
