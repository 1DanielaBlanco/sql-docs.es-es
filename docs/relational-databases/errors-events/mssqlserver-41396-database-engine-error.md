---
title: MSSQLSERVER_41396 | Microsoft Docs
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
- 41396 (Database Engine error)
ms.assetid: 4ff04042-8367-46f3-8a16-c94682d6eedb
caps.latest.revision: 8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 805655824825fbb628803698b8a6c8d1379fc7ec
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver41396"></a>MSSQLSERVER_41396
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Identificador del evento|41396|  
|Origen del evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|MAX_SORT_ROWS_EXCEEDED|  
|Texto del mensaje|La operación de ordenación ha superado el límite del búfer. La ejecución del procedimiento almacenado se anuló. Consulte los Libros en pantalla de SQL Server para obtener más información.|  
  
## <a name="explanation"></a>Explicación  
Los procedimientos almacenados compilados de forma nativa realizan operaciones de ordenación en memoria. Hay un límite en cuanto al tamaño del búfer de ordenación. Este error indica que el tamaño del búfer de ordenación supera este límite. La operación de ordenación y la ejecución del procedimiento almacenado se han anulado.  
  
El tamaño de cada fila o entrada del búfer de ordenación lo determinan el número de filas ordenadas junto con el número de combinaciones y el número y el tipo de funciones de agregado de la consulta. Si simplifica la consulta, puede reducir el tamaño de cada fila, con lo que cabrán más filas en el búfer de ordenación. El tamaño de las filas de las tablas base no afecta al tamaño de cada fila o entrada del búfer de ordenación.  
  
## <a name="user-action"></a>Acción del usuario  
Seleccione menos filas o reduzca la complejidad de la consulta quitando combinaciones o funciones de agregado.  
  
## <a name="see-also"></a>Ver también  
[OLTP en memoria &#40;optimización en memoria&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
