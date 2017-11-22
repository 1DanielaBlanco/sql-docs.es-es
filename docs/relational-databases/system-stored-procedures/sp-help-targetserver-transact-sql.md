---
title: sp_help_targetserver (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/06/2017
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
- sp_help_targetserver_TSQL
- sp_help_targetserver
dev_langs: TSQL
helpviewer_keywords: sp_help_targetserver
ms.assetid: f841d3bd-901a-4980-ad0b-1c6eeba3f717
caps.latest.revision: "35"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1542bc54c6c40b44f0738e249b4f609ac36b3b67
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="sphelptargetserver-transact-sql"></a>sp_help_targetserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Muestra todos los servidores de destino en una lista.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_help_targetserver   
     [ [ @server_name = ] 'server_name' ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@server_name=** ] **'***nombre_servidor***'**  
 Nombre del servidor cuya información se va a devolver. *nombre_servidor* es **nvarchar (30)**, su valor predeterminado es null.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
 Si *nombre_servidor* no se especifica, **sp_help_targetserver** devuelve este conjunto de resultados.  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|Número de identificación del servidor.|  
|**nombre_servidor**|**nvarchar (30)**|Nombre de servidor.|  
|**ubicación**|**nvarchar (200)**|Ubicación del servidor especificado.|  
|**time_zone_adjustment**|**int**|Ajuste de zona horaria, en horas, según la hora del meridiano de Greenwich (GMT).|  
|**enlist_date**|**datetime**|Fecha de alta del servidor especificado.|  
|**last_poll_date**|**datetime**|Fecha del último sondeo del servidor en busca de trabajos.|  
|**status**|**int**|Estado del servidor especificado.|  
|**unread_instructions**|**int**|Indica si el servidor tiene instrucciones no leídas. Si se han descargado todas las filas, esta columna es **0**.|  
|**local_time**|**datetime**|Fecha y hora locales del servidor de destino, que están basadas en la hora local del servidor de destino según el último sondeo del servidor maestro.|  
|**enlisted_by_nt_user**|**nvarchar (100)**|Usuario de Microsoft Windows dado de alta en el servidor de destino.|  
|**poll_interval**|**int**|Frecuencia, en segundos, con la que el servidor de destino sondea el servicio SQLServerAgent principal para descargar trabajos y cargar el estado de los trabajos.|  
  
## <a name="permissions"></a>Permissions  
 Para ejecutar este procedimiento almacenado, un usuario debe ser miembro del rol fijo de servidor **sysadmin** .  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-listing-information-for-all-registered-target-servers"></a>A. Presentar información de todos los servidores de destino registrados  
 En este ejemplo se presenta información de todos los servidores de destino registrados.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_targetserver ;  
GO  
```  
  
### <a name="b-listing-information-for-a-specific-target-server"></a>B. Presentar información de un servidor de destino específico  
 En este ejemplo se presenta información del servidor de destino `SEATTLE2`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_targetserver N'SEATTLE2' ;  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [sp_add_targetservergroup &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-add-targetservergroup-transact-sql.md)   
 [sp_delete_targetserver &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-delete-targetserver-transact-sql.md)   
 [sp_delete_targetservergroup &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-delete-targetservergroup-transact-sql.md)   
 [sp_update_targetservergroup &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-update-targetservergroup-transact-sql.md)   
 [dbo.sysdownloadlist &#40; Transact-SQL &#41;](../../relational-databases/system-tables/dbo-sysdownloadlist-transact-sql.md)   
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
