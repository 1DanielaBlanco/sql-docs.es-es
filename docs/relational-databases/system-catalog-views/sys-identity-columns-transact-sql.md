---
title: Sys.identity_columns (Transact-SQL) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- identity_columns
- sys.identity_columns
- sys.identity_columns_TSQL
- identity_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.identity_columns catalog view
ms.assetid: 97ee01e6-9c9e-4fd9-884b-68b4084669d5
caps.latest.revision: 44
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 21749d2f0f8f2db22399700031f17f4f2bc65132
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="sysidentitycolumns-transact-sql"></a>sys.identity_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Contiene una fila por cada columna que es una columna de identidad.  
  
 El **sys.identity_columns** vista hereda las filas de la **sys.columns** vista. El **sys.identity_columns** vista devuelve las columnas de la **sys.columns** vista, además de la interfaz **seed_value**, **increment_value**, **last_value**, y **is_not_for_replication** columnas. Para obtener más información, vea [Vistas de catálogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md).  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**\<las columnas que se heredaron de sys.columns >**||El **sys.identity_columns** vista devuelve todas las columnas de la **sys.columns** vista. También devuelve las columnas adicionales descritas a continuación. Para obtener una descripción de las columnas que la **sys.identity_columns** vista se hereda de **sys.columns**, consulte [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md).|  
|**seed_value**|**sql_variant**|Valor de inicialización de esta columna de identidad. El tipo de datos del valor de inicialización es el mismo que el de la propia columna.|  
|**increment_value**|**sql_variant**|Valor de incremento de esta columna de identidad. El tipo de datos del valor de inicialización es el mismo que el de la propia columna.|  
|**last_value**|**sql_variant**|Último valor generado para esta columna de identidad. El tipo de datos del valor de inicialización es el mismo que el de la propia columna.|  
|**is_not_for_replication**|**bit**|La columna de identidad se declara NOT FOR REPLICATION.|  
  
> [!NOTE]  
>  Para crear un número que se incremente automáticamente y que se pueda usar en varias tablas, o que se pueda llamar desde las aplicaciones sin hacer referencia a ninguna tabla, vea [Números de secuencia](../../relational-databases/sequence-numbers/sequence-numbers.md).  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Para obtener más información, consulte [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vea también  
 [Object Catalog Views &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  (Vistas de catálogo de objetos [Transact-SQL])  
 [Vistas de catálogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Preguntas frecuentes sobre consultas del catálogo de sistema de SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
