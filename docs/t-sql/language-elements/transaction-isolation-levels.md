---
title: "Niveles de aislamiento de transacción | Documentos de Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- locking [SQL Server], hints
- isolation levels [SQL Server], metadata access
- hints [SQL Server], locking
ms.assetid: 02bb71fa-1e92-4782-a9cf-6e256cc1f3ea
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0acd70fad20d0ad1c2727f93da52b2e938ee21fd
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="transaction-isolation-levels"></a>Niveles de aislamiento de transacción
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no garantiza que se respeten las sugerencias de bloqueo en consultas que tengan acceso a metadatos por medio de vistas de catálogo, vistas de compatibilidad, vistas del esquema de información y funciones integradas de emisión de metadatos.  
  
 Internamente, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] solo respeta el nivel de aislamiento READ COMMITTED para el acceso a metadatos. Si una transacción tiene un nivel de aislamiento que es, por ejemplo, SERIALIZABLE, y en la transacción se intenta obtener acceso a metadatos mediante vistas de catálogo o funciones integradas de emisión de metadatos, dichas consultas se ejecutan hasta que finalizan como READ COMMITTED. Sin embargo, en el aislamiento de instantánea, puede que el acceso a metadatos genere un error debido a operaciones DDL simultáneas. Esto se debe a que los metadatos no admiten versiones. Por tanto, puede que en el aislamiento de instantánea se genere un error al obtener acceso a:  
  
-   Vistas de catálogo  
  
-   Vistas de compatibilidad  
  
-   Vistas de esquema de información  
  
-   Funciones integradas de emisión de metadatos  
  
-   **sp_help** grupo de procedimientos almacenados  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Procedimientos de catálogo de cliente nativo  
  
-   Funciones y vistas de administración dinámica  
  
 Para obtener más información acerca de los niveles de aislamiento, consulte [SET TRANSACTION ISOLATION LEVEL &#40; Transact-SQL &#41; ](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md).  
  
 En la siguiente tabla se proporciona un resumen de acceso a metadatos en distintos niveles de aislamiento.  
  
|Nivel de aislamiento|Admitida|Respetado|  
|---------------------|---------------|-------------|  
|READ UNCOMMITTED|No|Sin garantizar|  
|READ COMMITTED|Sí|Sí|  
|REPEATABLE READ|No|No|  
|SNAPSHOT ISOLATION|No|No|  
|SERIALIZABLE|No|No|  
  
  

