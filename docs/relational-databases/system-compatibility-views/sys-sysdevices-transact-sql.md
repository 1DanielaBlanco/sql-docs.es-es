---
title: Sys.sysdevices (Transact-SQL) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysdevices
- sysdevices_TSQL
- sys.sysdevices
- sys.sysdevices_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysdevices compatibility view
- sysdevices system table
ms.assetid: ac5bcaf4-8fb6-4855-8856-d7643f469361
caps.latest.revision: 24
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 61a587fbb92e46686e7fe73cd8a69d5468240f20
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="syssysdevices-transact-sql"></a>sys.sysdevices (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una fila por cada archivo de copia de seguridad en disco, archivo de copia de seguridad en cinta y archivo de base de datos.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**Nombre**|**sysname**|Nombre lógico del archivo de copia de seguridad o de base de datos.|  
|**size**|**int**|Tamaño del archivo en páginas de 2 KB.|  
|**Baja**|**int**|Se mantiene únicamente por compatibilidad con versiones anteriores.|  
|**Alta**|**int**|Se mantiene únicamente por compatibilidad con versiones anteriores.|  
|**status**|**smallint**|Mapa de bits que indica el tipo de dispositivo:<br /><br /> 1 = Disco predeterminado<br /><br /> 2 = Disco físico<br /><br /> 4 = Disco lógico<br /><br /> 8 = Omitir encabezado<br /><br /> 16 = Archivo de copia de seguridad<br /><br /> 32 = Escrituras en serie<br /><br /> 4096 = Solo lectura|  
|**CntrlType**|**smallint**|Tipo de controlador:<br /><br /> 0 = Archivo de base de datos que no está en CD-ROM<br /><br /> 2 = Archivo de copia de seguridad en disco<br /><br /> 3 - 4 = Archivo de copia de seguridad en disquete<br /><br /> 5 = Archivo de copia de seguridad en cinta<br /><br /> 6 = Archivo de canalización con nombre|  
|**phyname**|**nvarchar(260)**|Nombre del archivo físico.|  
  
## <a name="see-also"></a>Vea también  
 [Asignar tablas del sistema a vistas del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Vistas de compatibilidad &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
