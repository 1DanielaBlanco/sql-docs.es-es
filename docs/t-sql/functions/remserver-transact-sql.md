---
title: '@@REMSERVER (Transact-SQL) | Microsoft Docs'
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
- '@@REMSERVER'
- '@@REMSERVER_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- logins [SQL Server], remote servers
- remote servers [SQL Server], logins
- '@@REMSERVER function'
ms.assetid: 0bb451a9-3866-4064-963d-b74a2f864049
caps.latest.revision: 23
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7b8d3ff79467cd38f8057e121d151c8e765794b1
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38031815"
---
# <a name="x40x40remserver-transact-sql"></a>&#x40;&#x40;REMSERVER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Utilice servidores vinculados y procedimientos almacenados de servidores vinculados en su lugar.  
  
 Devuelve el nombre del servidor de base de datos remoto de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], tal y como aparece en el registro de inicio de sesión.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
@@REMSERVER  
```  
  
## <a name="return-types"></a>Tipos devueltos  
 **nvarchar(128)**  
  
## <a name="remarks"></a>Notas  
 @@REMSERVER permite a un procedimiento almacenado comprobar el nombre del servidor de base de datos desde el que se ejecuta.  
  
## <a name="examples"></a>Ejemplos  
 En el siguiente ejemplo se crea el procedimiento `usp_CheckServer` que devuelve el nombre del servidor remoto.  
  
```  
CREATE PROCEDURE usp_CheckServer  
AS  
SELECT @@REMSERVER;  
```  
  
 El siguiente procedimiento almacenado se crea en el servidor local `SEATTLE1`. El usuario inicia una sesión en un servidor remoto, `LONDON2`, y ejecuta `usp_CheckServer`.  
  
```  
EXEC SEATTLE1...usp_CheckServer;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
---------------  
LONDON2  
```  
  
## <a name="see-also"></a>Ver también  
 [Funciones de configuración &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [Servidores remotos](../../database-engine/configure-windows/remote-servers.md)  
  
  
