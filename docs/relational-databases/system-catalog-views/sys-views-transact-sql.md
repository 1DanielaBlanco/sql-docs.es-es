---
title: Sys.Views (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- views_TSQL
- views
- sys.views_TSQL
- sys.views
dev_langs:
- TSQL
helpviewer_keywords:
- sys.views catalog view
ms.assetid: f8a8ea39-5a09-4662-801e-b43519467def
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 99f0d003eb304a88f4a2fa656b5ed4e658b1b040
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="sysviews-transact-sql"></a>sys.views (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Contiene una fila por cada objeto de vista, con **sys.objects.type** = V.  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**\<hereda columnas >**||Para obtener una lista de columnas que hereda esta vista, consulte [sys.objects &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)|  
|**is_replicated**|**bit**|1 = La vista está replicada.|  
|**has_replication_filter**|**bit**|1 = La vista tiene un filtro de replicación.|  
|**has_opaque_metadata**|**bit**|1 = Se ha especificado la opción VIEW_METADATA para la vista. Para obtener más información, vea [CREATE VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/create-view-transact-sql.md).|  
|**has_unchecked_assembly_data**|**bit**|1 = La vista contiene datos almacenados que dependen de un ensamblado cuya definición ha cambiado durante la última operación ALTER ASSEMBLY. Se restablece en 0 después de la siguiente operación DBCC CHECKDB o DBCC CHECKTABLE correcta.|  
|**with_check_option**|**bit**|1 = Se ha especificado WITH CHECK OPTION en la definición de la vista.|  
|**is_date_correlation_view**|**bit**|1 = El sistema ha creado la vista automáticamente para almacenar la información de correlación entre las columnas de fecha y hora. La creación de esta vista se ha habilitado al establecer DATE_CORRELATION_OPTIMIZATION en ON.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Para obtener más información, consulte [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vea también  
 [Vistas de catálogo de objetos &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Vistas de catálogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [ALTER ASSEMBLY &#40; Transact-SQL &#41;](../../t-sql/statements/alter-assembly-transact-sql.md)   
 [DBCC CHECKDB &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)   
 [DBCC CHECKTABLE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checktable-transact-sql.md)   
 [Preguntas frecuentes sobre consultas del catálogo de sistema de SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
