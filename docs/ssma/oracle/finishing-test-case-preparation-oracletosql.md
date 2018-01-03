---
title: "Finalizar la preparación del caso de prueba (OracleToSQL) | Documentos de Microsoft"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-oracle
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 32f38713-7ae4-48d3-980d-74cadc8545a0
caps.latest.revision: "6"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: f6bf969705a049e03212500a3112e643fbe7654a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="finishing-test-case-preparation-oracletosql"></a>Finalizar la preparación del caso de prueba (OracleToSQL)
Página final del asistente muestra la descripción del caso de prueba y obtener información acerca de los objetos implicados en la prueba. Además, en esta página se pueden establecer la prueba de opciones de ejecución.  
  
El **información casos de prueba** sección muestra el nombre del caso de prueba y la descripción.  
  
El **objetos seleccionado para ser probado** sección contiene la lista con nombre de objetos probados agrupados por tipo de objeto.  
  
El **objetos afectados por prueba que se va a analizar** sección muestra la lista de objetos que se deben comparar los cambios de datos después de la ejecución de objetos probados con nombre.  
  
## <a name="test-case-settings"></a>Configuración de caso de prueba  
En el **configuración de caso de prueba** sección puede establecer la siguiente ejecución de opciones de prueba:  
  
### <a name="stop-test-execution-after-first-failure"></a>Detener la ejecución de prueba tras el primer error  
Especifica que la prueba se interrumpe si se produce un error durante la ejecución de prueba.  
  
-   Si elige **Sí**, interrumpir la ejecución de pruebas si se produce un error.  
  
-   Si elige **n**, continúa la ejecución de pruebas después de un error.  
  
### <a name="perform-data-rollback"></a>Realizar la reversión de datos  
Permite la reversión automática de los datos después de la ejecución de pruebas.  
  
-   Si elige **Sí**, se perderán los cambios de datos después de la ejecución de prueba.  
  
-   Si elige **n**, todos los cambios de datos se guardarán de ejecución de prueba.  
  
### <a name="auxiliary-tables-saving-mode"></a>Tablas auxiliares de modo de ahorro  
Define el modo de guardar para tablas auxiliares creados durante la ejecución de pruebas. Vea la descripción de las tablas auxiliares en el [ejecutar casos de prueba &#40; OracleToSQL &#41;](../../ssma/oracle/running-test-cases-oracletosql.md) tema.  
  
-   Si selecciona **guardar siempre**, siempre se almacenarán datos de la tabla auxiliar para su uso posterior.  
  
-   Si selecciona **guardar si la comparación de la tabla no se pudo**, se almacenarán los datos de la tabla auxiliar solo si se produce un error.  
  
-   Si selecciona **siempre eliminar**, siempre puede eliminar tablas auxiliares después de la ejecución de prueba.  
  
-   Si selecciona **preguntar al usuario si la comparación de la tabla no se pudo**, el usuario puede seleccionar la acción es necesaria si se produce un error.  
  
Haga clic en el **finalizar** botón para guardar el caso de prueba preparada en [repositorios de prueba usando (OracleToSQL)](http://msdn.microsoft.com/en-us/f941cce4-d3e3-4aeb-a88a-4f101a97a9f4).  
  
## <a name="see-also"></a>Vea también  
[Mediante la prueba repositorios &#40; OracleToSQL &#41;](../../ssma/oracle/using-test-repositories-oracletosql.md)  
[Ejecutar casos de prueba &#40; OracleToSQL &#41;](../../ssma/oracle/running-test-cases-oracletosql.md)  
[Pruebas migran objetos de base de datos &#40; OracleToSQL &#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
