---
title: "Crear consultas de búsqueda de texto completo (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CONTAINS predicate (Transact-SQL)
- queries [full-text search], creating
- full-text queries [SQL Server], creating
ms.assetid: 537fa556-390e-4c88-9b8e-679848d94abc
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fa1f7e8edb48287dfc393192b4c714491488e949
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="create-full-text-search-queries-visual-database-tools"></a>Crear consultas de búsqueda de texto completo (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Las búsquedas de texto completo usan el predicado CONTAINS para buscar las filas que contienen el texto especificado en una columna determinada. Las búsquedas de texto completo solo pueden realizarse en las columnas que tienen índices de texto completo activos. Si intenta utilizar la cláusula CONTAINS en una columna que no tiene un índice de texto completo activo, recibirá un error. Para más información sobre los índices de texto completo y la cláusula CONTAINS, consulte [Búsqueda de texto completo (SQL Server)](http://msdn.microsoft.com/en-us/a0ce315d-f96d-4e5d-b4eb-ff76811cab75) y [CONTAINS (Transact-SQL)](http://msdn.microsoft.com/en-us/996c72fc-b1ab-4c96-bd12-946be9c18f84).  
  
### <a name="to-create-a-full-text-search-query"></a>Para crear una consulta de búsqueda de texto completo  
  
1.  Abra una consulta del Explorador de soluciones o cree una nueva.  
  
2.  Utilice la función CONTAINS en la cláusula WHERE de su consulta para buscar una columna de texto completo.  
  
## <a name="see-also"></a>Ver también  
[Tipos de consultas compatibles &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/supported-query-types-visual-database-tools.md)  
[Temas de procedimientos de diseño de consultas y vistas &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
[Realizar operaciones básicas con consultas (Visual Database Tools)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
