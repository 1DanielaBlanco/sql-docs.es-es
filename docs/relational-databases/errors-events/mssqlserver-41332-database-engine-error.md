---
title: MSSQLSERVER_41332 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 41332 (Database Engine error)
ms.assetid: d3403c3e-d178-4006-b6c9-c18609562db5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1aeee0fabb065252ce3fe7221d867ab06db717ad
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47764303"
---
# <a name="mssqlserver41332"></a>MSSQLSERVER_41332
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Identificador del evento|41332|  
|Origen del evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|SQL_SNAPSHOT_NOT_SUPPORTED|  
|Texto del mensaje|No se puede tener acceso ni crear tablas optimizadas en memoria ni procedimientos almacenados compilados de forma nativa cuando la configuración de TRANSACTION ISOLATION LEVEL para la sesión se ha establecido en SNAPSHOT.|  
  
## <a name="explanation"></a>Explicación  
La transacción se inició con el nivel de aislamiento de instantánea y luego se intentó utilizar una función incompatible.  
  
## <a name="user-action"></a>Acción del usuario  
Inicie la transacción con otro nivel de aislamiento. Para obtener más información, vea [OLTP en memoria &#40;optimización en memoria&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Ver también  
[OLTP en memoria &#40;optimización en memoria&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
