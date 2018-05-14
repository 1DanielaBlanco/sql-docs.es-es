---
title: MSSQLSERVER_41399 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 41399 (Database Engine error)
ms.assetid: 5e5acb07-16ca-4329-8210-cd2bab0c904f
caps.latest.revision: 6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7d7485b7bb5d392a371aac51ace9e6a52aa9ed99
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver41399"></a>MSSQLSERVER_41399
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Identificador del evento|41399|  
|Origen del evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|MAX_SORT_ROW_WIDTH_EXCEEDED|  
|Texto del mensaje|La operación de ordenación es demasiado compleja. Consulte los Libros en pantalla de SQL Server para obtener más información.|  
  
## <a name="explanation"></a>Explicación  
Ordenar el resultado de las operaciones de combinación y agregación aumenta la complejidad de la operación de ordenación, ya que aumenta el tamaño de la fila en el búfer de ordenación. Este error indica que el tamaño de la fila es mayor que el tamaño máximo admitido por el operador sort en los procedimientos almacenados compilados de forma nativa. Tenga en cuenta que el tamaño de una fila en el búfer de ordenación solo lo determinan el número de combinaciones y el número y el tipo de funciones de agregado. El tamaño de las filas de las tablas base no afecta al tamaño de la fila en e búfer.  
  
## <a name="user-action"></a>Acción del usuario  
Reduzca la complejidad de la consulta quitando combinaciones o funciones de agregado.  
  
## <a name="see-also"></a>Ver también  
[OLTP en memoria &#40;optimización en memoria&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
