---
title: sp_dbmmonitoraddmonitoring (Transact-SQL) | Documentos de Microsoft
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
- sp_dbmmonitoraddmonitoring
- sp_dbmmonitoraddmonitoring_TSQL
dev_langs: TSQL
helpviewer_keywords:
- database mirroring [SQL Server], monitoring
- sp_dbmmonitoraddmonitoring
ms.assetid: 9489dc30-af29-4363-a172-4645947fc95e
caps.latest.revision: "36"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c401798fd012723d59a1aa8aba88b375bafd4a50
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="spdbmmonitoraddmonitoring-transact-sql"></a>sp_dbmmonitoraddmonitoring (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea un trabajo del monitor de creación de reflejos de la base de datos que actualiza periódicamente el estado de creación de reflejos para cada base de datos reflejada en la instancia del servidor.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_dbmmonitoraddmonitoring [ update_period ]  
```  
  
## <a name="arguments"></a>Argumentos  
 *update_period*  
 Especifica el intervalo entre actualizaciones, en minutos. Este valor puede estar entre 1 y 120 minutos. El valor predeterminado es 1 minuto.  
  
> [!NOTE]  
>  Si se establece un período de actualización demasiado corto, podría aumentar el tiempo de respuesta para los clientes.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 Ninguno  
  
## <a name="result-sets"></a>Conjuntos de resultados  
 Ninguno  
  
## <a name="remarks"></a>Comentarios  
 Este procedimiento requiere que se permita la ejecución del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en la instancia del servidor y, para que se ejecute el trabajo del monitor de creación de reflejos de la base de datos, el Agente debe estar ejecutándose.  
  
 Si la creación de reflejo de base de datos se inicia desde [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], **sp_dbmmonitoraddmonitoring** procedimiento se ejecuta automáticamente. Si inicia la creación de reflejos manualmente mediante instrucciones ALTER DATABASE, para supervisar la base de datos reflejada en la instancia del servidor, debe ejecutar **sp_dbmmonitoraddmonitoring** manualmente.  
  
> [!NOTE]  
>  Si ejecuta **sp_dbmmonitoraddmonitoring** antes de configurar la creación de reflejo de base de datos, el trabajo de supervisión se ejecutará, pero no se actualizará la tabla de estado en la base de datos se almacena el historial del monitor de creación de reflejo.  
  
## <a name="permissions"></a>Permissions  
 Requiere la pertenencia al rol fijo de servidor **sysadmin** .  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se inicia la supervisión con un período de actualización de `3` minutos.  
  
```  
EXEC sp_dbmmonitoraddmonitoring 3;  
```  
  
## <a name="see-also"></a>Vea también  
 [Supervisar la creación de reflejo de la base de datos &#40;SQL Server&#41;](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)   
 [sp_dbmmonitorchangemonitoring &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorchangemonitoring-transact-sql.md)   
 [sp_dbmmonitordropmonitoring &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitordropmonitoring-transact-sql.md)   
 [sp_dbmmonitorhelpmonitoring &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorhelpmonitoring-transact-sql.md)   
 [sp_dbmmonitorresults &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql.md)  
  
  
