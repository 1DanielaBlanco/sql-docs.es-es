---
title: MSSQLSERVER_1904 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 1904 (Database Engine error)
ms.assetid: 2a35d57d-74e2-45a2-8f67-3f2e51d69712
caps.latest.revision: "9"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: cab1fca2c32b104dc95b8bfd63deb705f786b361
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver1904"></a>MSSQLSERVER_1904
  
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|SQL Server|  
|Identificador del evento|1904|  
|Origen del evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|KEYCOUNT|  
|Texto del mensaje|%S_MSG '%.*ls' en la tabla '%.\*ls' tiene %d nombres de columna en la lista de claves %S_MSG. El límite máximo para la lista de columnas de clave de índice o estadísticas es %d.|  
  
## <a name="explanation"></a>Explicación  
La lista de columnas de clave para el índice o estadística especificados supera el número máximo permitido de columnas.  
  
## <a name="user-action"></a>Acción del usuario  
Modifique la lista de columnas de clave para que no incluya más columnas del número máximo especificado.  
  
Con los índices no clúster, considere utilizar la cláusula INCLUDE en la instrucción CREATE INDEX para agregar columnas al índice como columnas sin clave. Este método impide superar la limitación de tamaño de índice actual de 16 columnas de clave como máximo. Para más información, consulte [Create Indexes with Included Columns](~/relational-databases/indexes/create-indexes-with-included-columns.md).  
  
## <a name="see-also"></a>Vea también  
[CREATE INDEX &#40;Transact-SQL&#41;](~/t-sql/statements/create-index-transact-sql.md)  
[CREATE STATISTICS &#40;Transact-SQL&#41;](~/t-sql/statements/create-statistics-transact-sql.md)  
  
