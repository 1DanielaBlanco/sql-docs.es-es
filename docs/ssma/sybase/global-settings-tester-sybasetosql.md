---
title: "Configuración global (Tester) (SybaseToSQL) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-sybase
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 6f0b9cea-5a24-4e42-8bbf-c4516b00da23
caps.latest.revision: "7"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a08108be504ebe901f6e202af2fd8c1d757c198c
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2017
---
# <a name="global-settings-tester-sybasetosql"></a>Configuración global (Tester) (SybaseToSQL)
Use la página de herramienta de comprobación de la **configuración Global** cuadro de diálogo para especificar la configuración de pruebas de SSMA.  
  
Para acceder a la configuración de la herramienta de comprobación, en la **herramientas** menú, seleccione **configuración Global**y haga clic en **Tester** en la parte inferior del panel izquierdo.  
  
## <a name="options"></a>Opciones  
**Análisis de objeto pueden someterse a prueba**  
Esta configuración especifica si se debe realizar el análisis de los objetos pueden someterse a prueba. Seleccione **Sí** si desea que el evaluador de SSMA para analizar y buscar automáticamente los objetos dependientes. Conjunto de opciones de forma predeterminada es **Sí**.  
  
Las siguientes opciones están disponibles para esta configuración:  
  
1.  Sí  
  
2.  No  
  
**Tablas auxiliares de modo de ahorro**  
Esta configuración especifica cómo guardar las tablas auxiliares internas creadas durante la ejecución del caso de prueba. Siguientes opciones se pueden establecer para esta configuración concreta:  
  
1.  Eliminar siempre  
  
2.  Guarde siempre  
  
3.  Guardar si produce un error de comparación de la tabla  
  
4.  Pida el usuario si la comparación de la tabla no se pudo  
  
La opción establecida de forma predeterminada es: **siempre eliminar**.  
  
**Realizar la reversión de datos**  
Esta configuración especifica si se debe realizar una operación de reversión después de ejecutar cada caso de prueba. Conjunto de opciones de forma predeterminada es **No**.  
  
Las siguientes opciones están disponibles para esta configuración:  
  
1.  Sí  
  
2.  No  
  
**Detener la ejecución de prueba tras el primer error**  
Esta configuración especifica si se debe detener la ejecución de caso de prueba actual, si se ha producido un error durante la ejecución. Conjunto de opciones de forma predeterminada es **Sí**.  
  
Las siguientes opciones están disponibles para esta configuración:  
  
1.  Sí  
  
2.  No  
  
## <a name="see-also"></a>Vea también  
[Preparación de caso de prueba acabado &#40; SybaseToSQL &#41;](../../ssma/sybase/finishing-test-case-preparation-sybasetosql.md)  
  
