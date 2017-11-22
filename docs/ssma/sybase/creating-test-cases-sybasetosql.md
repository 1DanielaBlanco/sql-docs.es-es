---
title: Crear casos de prueba (SybaseToSQL) | Documentos de Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords: Tester component,Test Case Wizard
ms.assetid: b52dfd93-95af-4299-bc8f-83f2a7a6a518
caps.latest.revision: "5"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ca77f14885313248bec2fde1a23c6eb8aa92daf7
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="creating-test-cases-sybasetosql"></a>Crear casos de prueba (SybaseToSQL)
Utilice al Asistente de caso de prueba para crear una prueba. Este asistente le permite crear casos de prueba eligiendo probados y comprobados los objetos y especificando los parámetros de pruebas.  
  
## <a name="starting-the-test-case-wizard"></a>Para iniciar al Asistente de caso de prueba  
Para iniciar el Asistente de caso de prueba, haga clic **nuevo caso de prueba...** desde el **Tester** menú.  
  
Cuando inicia, el asistente busca ssmatester2005db de base de datos o ssmatester2008db (dependiendo del tipo de proyecto) en el servidor de Sybase de origen. Es el esquema de extensión de evaluador utilizado para almacenar los objetos auxiliares. Si el Asistente de caso de prueba no se puede encontrar ssmatester2005db o ssmatester2008db, muestra una ventana de cuadro de diálogo que propone para crear la base de datos de extensión de evaluador. (Esta situación normalmente se produce durante la primera ejecución del evaluador de SSMA.)  
  
Si aparece el cuadro de diálogo, haga clic en **Sí** para crear la base de datos de Sybase evaluador en el servidor de origen. A continuación, una nueva ventana del cuadro de diálogo aparecerá en el que debe agregar uno o varios dispositivos en los que se va a buscar la nueva base de datos de evaluador. Haga clic en **agregar** para agregar un dispositivo. En el **asignación de espacio para la base de datos de evaluador** cuadro de diálogo Elegir el dispositivo y especifique el tamaño de la base de datos de evaluador. Además, puede establecer el dispositivo independiente para los registros de base de datos. Tenga en cuenta que debe tener privilegios de Sybase para crear bases de datos.  
  
## <a name="overview-of-creating-test-cases-using-the-wizard"></a>Información general de creación de casos de prueba mediante el Asistente  
El proceso de creación de un caso de prueba consta de cinco pasos:  
  
1.  [Inicialización de casos de prueba &#40; SybaseToSQL &#41; ](../../ssma/sybase/initializing-test-cases-sybasetosql.md).  
  
2.  [Seleccionar y configurar los objetos a prueba &#40; SybaseToSQL &#41; ](../../ssma/sybase/selecting-and-configuring-objects-to-test-sybasetosql.md).  
  
3.  [Seleccionar y configurar los objetos afectados &#40; SybaseToSQL &#41; ](../../ssma/sybase/selecting-and-configuring-affected-objects-sybasetosql.md).  
  
4.  [Personalizar el orden de las llamadas &#40; SybaseToSQL &#41; ](../../ssma/sybase/customizing-calls-order-sybasetosql.md).  
  
5.  [Preparación de caso de prueba acabado &#40; SybaseToSQL &#41; ](../../ssma/sybase/finishing-test-case-preparation-sybasetosql.md).  
  
## <a name="see-also"></a>Vea también  
[Pruebas migran objetos de base de datos &#40; SybaseToSQL &#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
