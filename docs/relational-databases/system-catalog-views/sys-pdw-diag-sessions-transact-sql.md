---
title: sys.pdw_diag_sessions (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 4d23688a-cddb-4eed-8231-ecde2a0b0e65
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 91ad46c8f8bc0391bab933d2033d54e43626a6cc
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2018
---
# <a name="syspdwdiagsessions-transact-sql"></a>sys.pdw_diag_sessions (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Contiene información sobre las distintas sesiones de diagnóstico que se han creado en el sistema.  
  
|Nombre de la columna|Tipo de datos|Description|Intervalo|  
|-----------------|---------------|-----------------|-----------|  
|**Nombre**|**nvarchar(255)**|Nombre de la sesión de diagnóstico.<br /><br /> Clave para esta vista.||  
|**xml_data**|**nvarchar(4000)**|Carga XML que describe la sesión.||  
|**is_active**|**bit**|Marca que indica si el indicador está activo.||  
|**host_address**|**nvarchar(255)**|Dirección de la máquina que hospeda la definición de la sesión (nodo de Control).||  
|**principal_id**|**int**|Id. del usuario que creó la sesión en el nivel de base de datos.||  
|**database_id**|**int**|Id. de la base de datos que es el ámbito de la sesión de diagnóstico.|  
  
## <a name="see-also"></a>Vea también  
 [Almacenamiento de datos SQL y vistas de catálogo del almacén de datos en paralelo](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
