---
title: sys.dm_pdw_nodes (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/07/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 93966909-d758-4d50-950b-f5066d104fa6
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 48539364beb107a54621bbdfaa7555583e0e30ce
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmpdwnodes-transact-sql"></a>sys.dm_pdw_nodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contiene información acerca de todos los nodos en [!INCLUDE[ssAPS](../../includes/ssaps-md.md)]. Muestra una fila por cada nodo en el dispositivo.  
  
|Nombre de la columna|Tipo de datos|Description|Intervalo|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Identificador numérico único asociado al nodo.<br /><br /> Clave para esta vista.|Único en el dispositivo, independientemente del tipo.|  
|tipo|**nvarchar(32)**|Tipo del nodo.|'COMPUTE', 'CONTROL', 'ADMINISTRACIÓN'|  
|name|**nvarchar(32)**|Nombre lógico del nodo.|Cualquier cadena de longitud apropiada.|  
|address|**nvarchar(32)**|Dirección IP de este nodo.|En el formato de [0-255]. [0-255]. [0-255]. [0-255].|  
|is_passive|**int**|Indica si la máquina virtual ejecuta el nodo se ejecuta en el servidor asignado o haya conmutado por error en el servidor de reserva.|0 – máquina virtual del nodo se está ejecutando en el servidor original.<br /><br /> 1: máquina virtual del nodo se está ejecutando en el servidor de reserva.|  
|región|**nvarchar(32)**|La región donde se está ejecutando el nodo.|'PDW', 'HDINSIGHT'|  
  
## <a name="see-also"></a>Vea también  
 [Almacenamiento de datos SQL y vistas de administración dinámica de almacenamiento de datos en paralelo &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
