---
title: 'Paso 3: Probar el paquete del tutorial de la lección 3 | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 1096a476-93cf-4474-86f5-27d6357eb380
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8bad683dc5ad0b49ac464ab3efcb90a652d45aa9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47760823"
---
# <a name="lesson-3-3---testing-the-lesson-3-tutorial-package"></a>Lección 3-3: Probar el paquete del tutorial de la lección 3
En esta tarea, ejecutará el paquete Lesson 3.dtsx. Al ejecutar el paquete, en la ventana Registrar eventos se mostrará una lista de las entradas del registro que se escriben en el archivo de registro. Una vez que haya finalizado la ejecución del paquete, comprobará el contenido del archivo de registro generado por el proveedor de registro.  
  
## <a name="checking-the-package-layout"></a>Comprobar el diseño del paquete  
Antes de probar el paquete, debe comprobar que los flujos de datos y de control de la lección 3 contienen los objetos mostrados en los diagramas siguientes. El flujo de control debe ser idéntico al flujo de datos de la lección 2. El flujo de datos debe ser idéntico al flujo de datos de las lecciones 1 y 2.  
  
**Flujo de control**  
  
![Flujo de control del paquete](../integration-services/media/task4lesson2control.gif "Control flow in package")  
  
**Flujo de datos**  
  
![Flujo de datos del paquete](../integration-services/media/task9lesson1data.gif "Data flow in package")  
  
### <a name="to-run-the-lesson-4-tutorial-package"></a>Para ejecutar el paquete de tutorial de la lección 4  
  
1.  En el menú SSIS, haga clic en Registrar eventos.  
  
2.  En el menú **Depurar** , haga clic en **Iniciar depuración**.  
  
3.  Una vez que se haya completado la ejecución del paquete, en el menú **Depurar** , haga clic en **Detener depuración**.  
  
### <a name="to-examine-the-generated-log-file"></a>Para examinar el archivo de registro generado  
  
-   Mediante el Bloc de notas o cualquier otro editor de texto, abra el archivo TutorialLog.log.  
  
-   Aunque la semántica de la información generada para los eventos **PipelineExecutionPlan** y **PipelineExecutionTrees** queda fuera del ámbito de este tutorial, puede ver que la primera línea enumera los campos de información especificados en la pestaña **Detalles** del cuadro de diálogo **Configurar registros de SSIS** . Además, puede comprobar que los dos eventos que ha seleccionado, PipelineExecutionPlan y PipelineExecutionTrees, se han registrado para cada iteración del bucle Foreach.  
  
## <a name="next-lesson"></a>Lección siguiente  
[Lección 4: Agregar redirección de flujo de errores con SSIS](../integration-services/lesson-4-add-error-flow-redirection-with-ssis.md)  
  
  
  
