---
title: Información rápida (IntelliSense) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology:
- database-engine
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Quick Info option [IntelliSense]
- declarations [IntelliSense]
- IntelliSense [SQL Server], Quick Info
- identifier declarations [IntelliSense]
ms.assetid: 3c8b59f4-1922-4bde-844f-5f2306514d96
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 63d8d03156bb3d6aef313b0b33c19f81c625ca61
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="quick-info-intellisense"></a>Información rápida (IntelliSense)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  La opción [!INCLUDE[msCoName](../../includes/msconame-md.md)] Información rápida **de** IntelliSense muestra la declaración completa de cualquier identificador del código. Al mover el puntero del mouse sobre un identificador, su declaración se muestra en una ventana emergente de color amarillo. En [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], **Quick Info** está disponible en los Editores de Consulta XML y Motor de base de datos.  
  
## <a name="transact-sql-quick-info"></a>Quick Info de Transact-SQL  
 **Quick Info** muestra dos tipos de información en el Editor de consultas del [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Cuando no está en modo de depuración, **Quick Info** muestra la declaración de la expresión. Cuando está en modo de depuración, **Quick Info** muestra en cambio el nombre de la expresión y su valor actual.  
  
 En el Editor de consultas de [!INCLUDE[ssDE](../../includes/ssde-md.md)] , la opción **Información rápida** solo está disponible para las partes de la sintaxis de [!INCLUDE[tsql](../../includes/tsql-md.md)] que IntelliSense admite. Por ejemplo, si mueve el puntero del mouse sobre el identificador de un objeto que tiene un tipo de datos que IntelliSense no admite, la ventana emergente **Información rápida** muestra un mensaje que indica que no se admite el tipo de datos.  
  
## <a name="see-also"></a>Ver también  
 [Sintaxis de Transact-SQL compatible con IntelliSense](../../relational-databases/scripting/transact-sql-syntax-supported-by-intellisense.md)  
  
  
