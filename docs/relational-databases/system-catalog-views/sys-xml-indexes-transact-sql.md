---
title: Sys.xml_indexes (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.xml_indexes_TSQL
- xml_indexes_TSQL
- sys.xml_indexes
- xml_indexes
dev_langs: TSQL
helpviewer_keywords: sys.xml_indexes catalog view
ms.assetid: 3408de72-b067-4fda-b5d5-8e856dfd9db3
caps.latest.revision: "34"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 23c5fc72f377b08e77b8b2c8167919bcbc707ec3
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="sysxmlindexes-transact-sql"></a>sys.xml_indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve una fila por índice XML.  
  
||  
|-|  
|**Se aplica a:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] hasta la [versión actual](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].|  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**\<hereda columnas >**||Hereda columnas de [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).|  
|**using_xml_index_id**|**int**|NULL = Índice XML principal.<br /><br /> Nonnull = Índice XML secundario.<br /><br /> Nonnull es una referencia de autocombinación al índice XML principal.|  
|**secondary_type**|**Char (1)**|Descripción del tipo del índice secundario:<br /><br /> P = Índice XML secundario de PATH<br /><br /> V = Índice XML secundario de VALUE<br /><br /> R = Índice XML secundario de PROPERTY<br /><br /> NULL = Índice XML principal|  
|**secondary_type_desc**|**nvarchar (60)**|Descripción del tipo del índice secundario:<br /><br /> PATH = Índice XML secundario de PATH<br /><br /> VALUE = Índice XML secundario de VALUE<br /><br /> PROPERTY = Índices XML secundarios de PROPERTY.<br /><br /> NULL = Índice XML principal|  
|**xml_index_type**|**tinyint**|Tipo de índice:<br /><br /> 0 = Índice XML principal<br /><br /> 1 = Índice XML secundario<br /><br /> 2 = Índice XML selectivo<br /><br /> 3 = Índice XML selectivo secundario|  
|**xml_index_type_description**|**nvarchar (60)**|Descripción del tipo de índice:<br /><br /> PRIMARY_XML<br /><br /> Índice XML secundario<br /><br /> Índice XML selectivo<br /><br /> Índice XML selectivo secundario|  
|**de path_id**|**int**|NULL para todos los índices XML, salvo el índice XML selectivo secundario.<br /><br /> También es el identificador de la ruta de acceso promovida en la que se va a generar el índice XML selectivo secundario. Este valor es el mismo que el de path_id de la vista del sistema sys.selective_xml_index_paths.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Para obtener más información, consulte [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vea también  
 [Vistas de catálogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Vistas de catálogo de objetos &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  
  
  
