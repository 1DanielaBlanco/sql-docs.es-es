---
title: Sys.fn_helpcollations (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 08/23/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- fn_helpcollations
- fn_helpcollations_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_helpcollations function
- collations [SQL Server], supported
- fn_helpcollations function
ms.assetid: b5082e81-1fee-4e2c-b567-5412eaee41c1
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bc85244ca2f3ee810001b685a08960c2e4355998
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="sysfnhelpcollations-transact-sql"></a>sys.fn_helpcollations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  Devuelve una lista de todas las intercalaciones admitidas.  
  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
fn_helpcollations ()  
```  
  
## <a name="tables-returned"></a>Tablas devueltas  
 **fn_helpcollations** devuelve la siguiente información.  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|Nombre|**sysname**|Nombre de intercalación estándar|  
|Description|**nvarchar(1000)**|Descripción de la intercalación|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] es compatible con las intercalaciones de Windows. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] también admite un número limitado (<80) de las intercalaciones denominadas intercalaciones de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que se desarrollaron antes de que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] admitiera intercalaciones de Windows. Las intercalaciones de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se siguen admitiendo por compatibilidad con versiones anteriores, pero no se deben utilizar en nuevos trabajos de desarrollo. Para obtener más información acerca de las intercalaciones de Windows, vea [nombre de intercalación de Windows &#40; Transact-SQL &#41; ](../../t-sql/statements/windows-collation-name-transact-sql.md). Para obtener más información acerca de las intercalaciones, vea [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  

## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se devuelven todos los nombres de intercalación que comienzan por la letra `L` y que son intercalaciones de orden binario.  
  
```  
SELECT Name, Description FROM fn_helpcollations()  
WHERE Name like 'L%' AND Description LIKE '% binary sort';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```   
 Name                   Description  
 -------------------    ------------------------------------  
 Lao_100_BIN            Lao-100, binary sort  
 Latin1_General_BIN     Latin1-General, binary sort  
 Latin1_General_100_BIN Latin1-General-100, binary sort  
 Latvian_BIN            Latvian, binary sort  
 Latvian_100_BIN        Latvian-100, binary sort  
 Lithuanian_BIN         Lithuanian, binary sort  
 Lithuanian_100_BIN     Lithuanian-100, binary sort  
  
 (7 row(s) affected)  
 ```    
  
## <a name="see-also"></a>Vea también  
[COLLATE &#40;Transact-SQL&#41;](~/t-sql/statements/collations.md)   
[COLLATIONPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/collation-functions-collationproperty-transact-sql.md)  
[Compatibilidad con la intercalación de base de datos de almacenamiento de datos de SQL Azure](https://azure.microsoft.com/blog/database-collation-support-for-azure-sql-data-warehouse-2)  

