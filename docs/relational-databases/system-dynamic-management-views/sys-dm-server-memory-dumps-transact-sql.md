---
title: Sys.dm_server_memory_dumps (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_server_memory_dumps_TSQL
- dm_server_memory_dumps_TSQL
- dm_server_memory_dumps
- sys.dm_server_memory_dumps
dev_langs: TSQL
helpviewer_keywords: sys.dm_server_memory_dumps dynamic management view
ms.assetid: 41782719-f54d-4e11-941a-c050c7576e23
caps.latest.revision: "6"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cd4af6e42415814c6fc0771346f94a5283a41730
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmservermemorydumps-transact-sql"></a>sys.dm_server_memory_dumps (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve una fila por cada archivo de volcado de memoria generado por [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Use esta vista de administración dinámica para solucionar problemas potenciales.  
 
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**nombre de archivo**|**nvarchar(256)**|Ruta de acceso y nombre del archivo de volcado de memoria. No puede ser null.|  
|**creation_time**|**DateTimeOffset(7)**|Fecha y hora en que se creó el archivo. No puede ser null.|  
|**size_in_bytes**|**bigint**|Tamaño (en bytes) del archivo. Acepta valores NULL.|  
  
## <a name="general-remarks"></a>Notas generales  
 El tipo de volcado de memoria puede ser un minivolcado de memoria, un volcado de memoria de todos los subprocesos o un volcado de memoria completo. Los archivos tienen una extensión .mdmp.  
  
## <a name="security"></a>Seguridad  
 Los archivos de volcado de memoria pueden contener información confidencial. Para proteger la información confidencial, puede utilizar una lista de control de acceso (ACL) con objeto de restringir el acceso a los archivos o copiarlos en una carpeta con acceso restringido. Por ejemplo, antes de enviar que los archivos de depuración a Microsoft de servicios de soporte técnico, se recomienda que quite cualquier información sensible o confidencial.  
  
### <a name="permissions"></a>Permissions  
 Requiere el permiso VIEW SERVER STATE.  
  
  
