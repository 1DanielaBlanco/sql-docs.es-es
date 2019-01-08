---
title: sysarticlecolumns (vista del sistema) (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysarticlecolumns
- sysarticlecolumns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysarticlecolumns view
ms.assetid: a8dd8d13-c827-45c4-87ba-802725301382
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1ffa8c9c45e1810fb4a81deed34f7c6c2e4a0ca0
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2018
ms.locfileid: "52756553"
---
# <a name="sysarticlecolumns-system-view-transact-sql"></a>sysarticlecolumns (vista del sistema) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  El **sysarticlecolumns** vista expone información adicional acerca de las columnas de los artículos publicados. Esta vista se almacena en la base de datos de distribución.  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|Identifica un artículo.|  
|**colid**|**int**|Identifica una columna de un artículo.|  
|**is_udt**|**int**|Indica si la columna es una columna de un tipo de datos definido por el usuario (UDT). Un valor de **1** indica una columna UDT.|  
|**is_xml**|**int**|Indica si la columna es una **xml** columna. Un valor de **1** indica un **xml** columna.|  
|**is_max**|**int**|Indica si la columna es una columna de tipo de datos de valor grande (**varchar (max)**, **nvarchar (max)** o **varbinary (max)**). Un valor de **1** indica una columna de valor grande.|  
  
## <a name="see-also"></a>Vea también  
 [sp_articlecolumn &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sysarticlecolumns &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysarticlecolumns-transact-sql.md)  
  
  
