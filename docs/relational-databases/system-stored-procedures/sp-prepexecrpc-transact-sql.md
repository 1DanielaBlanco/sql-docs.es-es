---
title: sp_se (Transact-SQL) | Documentos de Microsoft
ms.custom: ''
ms.date: 06/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_cursor_prepexecrpc
- sp_cursor_prepexecrpc_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_prepexecrpc
ms.assetid: 35d686f2-ef31-4eaa-baa9-9cef5d6c87c2
caps.latest.revision: 5
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 710f6452881284924861cc31cab38adfcaee2dc7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="spprepexecrpc-transact-sql"></a>sp_prepexecrpc (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Prepara y ejecuta una llamada a un procedimiento almacenado con parámetros que se ha especificado mediante un identificador de RPC. sp_se invoca con el identificador 14 en un paquete de flujo TDS.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_prepexecrpc handle OUTPUT, RPCCall  
    [ , bound_param ] [ ,...n]]  
```  
  
## <a name="arguments"></a>Argumentos  
 *Identificador*  
 Es el identificador del controlador preparado generado por [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *controlar* es un parámetro necesario con un **int** valor devuelto.  
  
 *RPCCall*  
 Define la llamada a procedimiento almacenado mediante sintaxis canónica de ODBC. *RPCCall* es un parámetro necesario que requiere un **ntext** valor de cadena de entrada.  
  
 *bound_param*  
 Indica el uso opcional de parámetros adicionales. *bound_param* requiere un valor de entrada de cualquier tipo de datos para designar los parámetros adicionales en uso.  
  
## <a name="see-also"></a>Vea también  
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
