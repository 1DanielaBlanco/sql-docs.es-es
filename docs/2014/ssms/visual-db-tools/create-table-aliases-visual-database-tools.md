---
title: Crear alias de tabla (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- table aliases [SQL Server]
- aliases [SQL Server], tables
ms.assetid: 49e61e85-8abf-4ca7-8c70-7e9f8f1078bd
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 75eaebe7ca2faf459f7f60700b3b2ef1d725db4c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36201725"
---
# <a name="create-table-aliases-visual-database-tools"></a>Crear alias de tabla (Visual Database Tools)
  Los alias facilitan el trabajo con nombres de tabla. El uso de alias es útil cuando:  
  
-   Desea acortar la instrucción del [panel SQL](visual-database-tools.md) y facilitar su lectura.  
  
-   La consulta hace referencia varias veces a un nombre de tabla (como en el caso de los nombres completos de columnas) y desea asegurarse de que la longitud de la consulta no superará un límite específico de caracteres. (Algunas bases de datos imponen una longitud máxima a las consultas.)  
  
-   Trabaja con varias instancias de la misma tabla (como en el caso de una autocombinación) y necesita una forma de hacer referencia a cada instancia.  
  
 Por ejemplo, puede crear un alias `"e"` para el nombre de tabla `employee`_`information`y, a continuación, hacer referencia a la tabla como `"e"` en el resto de la consulta.  
  
### <a name="to-create-an-alias-for-a-table-or-table-valued-object"></a>Para crear un alias para una tabla o un objeto con valores de tabla  
  
1.  Agregue la tabla o el objeto con valores de tabla a la consulta.  
  
2.  En el **panel Diagrama**, haga clic con el botón derecho en el objeto para el que desea crear un alias y después elija **Propiedades** en el menú contextual.  
  
3.  En la ventana **Propiedades** , escriba el alias en el campo **Alias** .  
  
## <a name="see-also"></a>Vea también  
 [Agregar tablas a las consultas &#40;Visual Database Tools&#41;](add-tables-to-queries-visual-database-tools.md)   
 [Ordenar y agrupar los resultados de consulta &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md)   
 [Resumir los resultados de la consulta &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md)   
 [Realizar operaciones básicas con consultas (Visual Database Tools)](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  