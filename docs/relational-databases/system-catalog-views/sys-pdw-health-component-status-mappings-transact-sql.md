---
title: sys.pdw_health_component_status_mappings (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 4272cfad-5ad7-493d-9edd-d9111619bda0
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 02771656dfdb0b7396e62a5bde364b0eea324aa0
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2019
ms.locfileid: "56031196"
---
# <a name="syspdwhealthcomponentstatusmappings-transact-sql"></a>sys.pdw_health_component_status_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Define la asignación entre el [!INCLUDE[ssDW](../../includes/ssdw-md.md)] Estados de los componentes y los nombres de componente definido por el fabricante.  
  
|Nombre de la columna|Tipo de datos|Descripción|Intervalo|  
|-----------------|---------------|-----------------|-----------|  
|property_id|**int**|Identificador único de la propiedad.<br /><br /> identificador property_id IdComponente y physical_name forman la clave para esta vista.|NOT NULL|  
|component_id|**int**|El identificador del componente. Consulte [sys.pdw_health_components &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> identificador property_id IdComponente y physical_name forman la clave para esta vista.|NOT NULL|  
|physical_name|**nvarchar(32)**|Nombre de la propiedad tal como se define por el fabricante.<br /><br /> identificador property_id IdComponente y physical_name forman la clave para esta vista.|NOT NULL|  
|logical_name|**nvarchar(255)**|Nombre de la propiedad tal como se define por [!INCLUDE[ssDW](../../includes/ssdw-md.md)].|NOT NULL<br /><br /> 0: la instancia de dispositivo es único.<br /><br /> 1 - instancia de el dispositivo no es único.|  
  
## <a name="see-also"></a>Vea también  
 [SQL Data Warehouse y vistas de catálogo del almacén de datos en paralelo](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
