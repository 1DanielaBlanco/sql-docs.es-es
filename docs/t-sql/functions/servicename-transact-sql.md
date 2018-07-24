---
title: '@@SERVICENAME (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- '@@SERVICENAME_TSQL'
- '@@SERVICENAME'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@SERVICENAME function'
- names [SQL Server], registry keys
- registry keys [SQL Server]
ms.assetid: 5b0b35be-50ae-411d-a607-bf7464b73624
caps.latest.revision: 23
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 457749a5374f208e78cf26f495fdf026779a80f4
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38052093"
---
# <a name="x40x40servicename-transact-sql"></a>&#x40;&#x40;SERVICENAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Devuelve el nombre de la clave del Registro bajo la cual se ejecuta [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. @@SERVICENAME devuelve 'MSSQLSERVER' si la instancia actual es la predeterminada; esta función devuelve el nombre de la instancia si la instancia actual es una instancia con nombre.  

[!INCLUDE[ssMIlimitation](../../includes/sql-db-mi-limitation.md)]

 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
@@SERVICENAME  
```  
  
## <a name="return-types"></a>Tipos devueltos  
 **nvarchar**  
  
## <a name="remarks"></a>Notas  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se ejecuta como un servicio denominado MSSQLServer.  
  
## <a name="examples"></a>Ejemplos  
 En el siguiente ejemplo se muestra la forma de utilizar `@@SERVICENAME`.  
  
```  
SELECT @@SERVICENAME AS 'Service Name';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Service Name                    
------------------------------  
MSSQLSERVER                     
```  
  
## <a name="see-also"></a>Ver también  
 [Funciones de configuración &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [Administrar el servicio del motor de base de datos](../../database-engine/configure-windows/manage-the-database-engine-services.md)  
  
  
