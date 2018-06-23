---
title: MSSQLSERVER_5554 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 5554 (Database Engine error)
ms.assetid: 7134bbe5-d240-4a98-85ce-b13cc8ae9b0e
caps.latest.revision: 11
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: a340576c20387fa0620815759aa966e59d139897
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36104464"
---
# <a name="mssqlserver5554"></a>MSSQLSERVER_5554
    
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|MSSQLSERVER|  
|Identificador del evento|5554|  
|Origen del evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|FS_MINIVER_OVERFLOW|  
|Texto del mensaje|El número total de versiones para un único archivo ha alcanzado el límite máximo establecido por el sistema de archivos.|  
  
## <a name="explanation"></a>Explicación  
 En conjuntos de resultados activos múltiples (MARS) o escenarios de desencadenador, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usa la miniversión especificada por el sistema operativo.  
  
## <a name="user-action"></a>Acción del usuario  
 Intente evitar las actualizaciones repetidas en los datos de la misma transacción.  
  
  