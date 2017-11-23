---
title: Sys.pdw_diag_events (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 59bb3e9c-2829-49a0-b382-652ed1f54f88
caps.latest.revision: "7"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3c2eac163e114716e0b7d40f3d14608954280fd4
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="syspdwdiagevents-transact-sql"></a>Sys.pdw_diag_events (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Contiene información sobre los eventos que pueden incluirse en las sesiones de diagnóstico en el sistema.  
  
|Nombre de la columna|Tipo de datos|Description|Intervalo|  
|-----------------|---------------|-----------------|-----------|  
|**Nombre**|**nvarchar(255)**|Nombre del evento diagnósticos específicos.||  
|**origen**|**nvarchar(255)**|Origen del evento (motor, general, dms, etcetera.)||  
|**is_enabled**|**bit**|Si se publica el evento.||  
  
## <a name="see-also"></a>Vea también  
 [Almacenamiento de datos SQL y vistas de catálogo del almacén de datos en paralelo](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
