---
title: Sys.dm_io_cluster_shared_drives (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_io_cluster_shared_drives_TSQL
- sys.dm_io_cluster_shared_drives
- dm_io_cluster_shared_drives_TSQL
- dm_io_cluster_shared_drives
dev_langs: TSQL
helpviewer_keywords: sys.dm_io_cluster_shared_drives dynamic management view
ms.assetid: c8fcced8-c780-49dc-99bd-6beb3ca532c4
caps.latest.revision: "30"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 66e4e1de40aee22313bd8950986079e176f5278d
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmioclustershareddrives-transact-sql"></a>sys.dm_io_cluster_shared_drives (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  Esta vista devuelve el nombre de cada unidad compartida si la instancia de servidor actual es un servidor en clúster. Si la instancia del servidor actual no es una instancia en clúster, devuelve un conjunto de filas vacío.  
  
> [!NOTE]  
>  Para llamar a esta desde [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], use el nombre **sys.dm_pdw_nodes_io_cluster_shared_drives**.  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**DriveName**|**nchar(2)**|Nombre de la unidad (la letra de unidad) que representa un disco individual que forma parte de la matriz de discos compartida del clúster. La columna no acepta valores NULL.|  
|**pdw_node_id**|**int**|**Se aplica a**: ssPDW<br /><br /> El identificador para el nodo que se encuentra en esta distribución.|  
  
## <a name="remarks"></a>Comentarios  
 Cuando se habilita la agrupación en clústeres, la instancia en clúster de conmutación por error requiere que los archivos de datos y de registro estén en discos compartidos para que puedan estar accesibles después de que la instancia realice una conmutación por error a otro nodo. Cada una de las filas de esta vista representa un único disco compartido que utiliza esta instancia en clúster de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Para almacenar archivos de registros o datos de esta instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] solo se pueden utilizar los discos enumerados en esta vista. Los discos enumerados en esta vista son los que están en el grupo de recursos del clúster asociado a la instancia.  
  
> [!NOTE]  
>  Esta vista quedará desusada en una versión futura. Se recomienda que use [sys.dm_io_cluster_valid_path_names &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-io-cluster-valid-path-names-transact-sql.md) en su lugar.  
  
## <a name="permissions"></a>Permissions  
 El usuario debe tener permiso VIEW SERVER STATE para la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se utiliza sys.dm_io_cluster_shared_drives para determinar las unidades compartidas en una instancia de servidor en clúster:  
  
```  
SELECT * FROM sys.dm_io_cluster_shared_drives;  
```  
  
 Éste es el conjunto de resultados:  
  
 DriveName  
  
 --------\-  
  
 m  
  
 n  
  
## <a name="see-also"></a>Vea también  
 [Sys.dm_io_cluster_valid_path_names &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-io-cluster-valid-path-names-transact-sql.md)   
 [Sys.dm_os_cluster_nodes &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-cluster-nodes-transact-sql.md)   
 [Sys.fn_servershareddrives &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-servershareddrives-transact-sql.md)   
 [Funciones y vistas de administración dinámica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  
