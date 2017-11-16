---
title: Seleccionar filas que no coinciden con un valor (Visual Database Tools) | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- search conditions [SQL Server], rows not matching value
- row not matching value [SQL Server]
- NOT operator [Visual Database Tools]
- search criteria [SQL Server], rows not matching value
ms.assetid: 19898578-7b2f-401c-bb8f-9f2a017efdf7
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 37d9bf886947b98d5f14ec8d67e25c5c5c91e2e9
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="select-rows-that-do-not-match-a-value-visual-database-tools"></a>Seleccionar filas que no coinciden con un valor (Visual Database Tools)
Para buscar filas que no coinciden con un valor, utilice el operador NOT.  
  
### <a name="to-find-rows-that-do-not-match-a-value"></a>Para buscar filas que no coincidan con un valor  
  
1.  Si aún no lo ha hecho, agregue al [panel Criterios](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md)las columnas o expresiones que desee utilizar en la condición de búsqueda.  
  
2.  Busque la fila que contiene la columna de datos o la expresión que desea buscar y, a continuación, en la columna de cuadrícula **Filtro** , escriba el operador NOT seguido de un valor de búsqueda.  
  
Por ejemplo, para buscar todas las filas de una tabla `products` cuyos valores de la columna de código de producto empiecen por un carácter distinto de "A", escriba una condición de búsqueda como la siguiente:  
  
```  
NOT LIKE 'A%'  
```  
  
## <a name="see-also"></a>Vea también  
[Reglas para especificar valores de búsqueda (Visual Database Tools)](../../ssms/visual-db-tools/rules-for-entering-search-values-visual-database-tools.md)  
[Especificar criterios de búsqueda (Visual Database Tools)](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
  
