---
title: Limitaciones del uso de los cursores controlados por conjunto de claves | Documentos de Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], cursors
- keyset-driven cursors [ODBC]
ms.assetid: 59d86fed-387c-4719-9550-36343e74da44
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f6661ca9104e683cdac84cb3d533736d3a02f42f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="limitations-of-using-keyset-driven-cursors"></a>Limitaciones del uso de los cursores controlados por conjunto de claves
> [!IMPORTANT]  
>  Esta característica se quitará en una versión futura de Windows. Evite utilizar esta característica en nuevos trabajos de desarrollo y tenga previsto modificar las aplicaciones que actualmente la utilizan. En su lugar, utilice el controlador ODBC proporcionado por Oracle.  
  
 Debe ser capaz de recuperar una sola columna ROWID para la tabla de consulta. No se puede usar un cursor controlado por conjunto de claves en combinaciones, las consultas o instrucciones que contienen DISTINCT, GROUP BY, UNION, INTERSECT o menos cláusulas.  
  
 Además, si la aplicación utiliza el alias de tabla, los cursores dinámicos no funcionará; se requieren tipos de cursor de solo avance o estático. Con el conjunto de claves tipo de cursor con alias de tabla hará que el siguiente error: "[Microsoft] [controlador ODBC para Oracle] no puede usar el cursor controlado por conjunto de claves en una combinación con union, intersect o conjunto de resultados de menos o de solo lectura."  
  
> [!NOTE]  
>  Debido al modo en que el controlador administra la instrucción SQL que se envía al servidor de Oracle, Oracle internamente devuelve el siguiente mensaje de error: "ORA-00964: tabla nombre no está en la de la lista."
