---
title: Extender el paquete con la tarea Script | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- scripts [Integration Services]
- SSIS Script task
- tasks [Integration Services], scripts
- Script task [Integration Services], about Script task
- scripts [Integration Services], about Script task with packages
- SSIS Script task, about Script task
ms.assetid: 911e6d26-a6fd-4fc3-a111-bf5f048e9bff
caps.latest.revision: 57
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b2e0b0a933568f8313cefd2f1d6dbdd02f5d3cbc
ms.contentlocale: es-es
ms.lasthandoff: 08/03/2017

---
# <a name="extending-the-package-with-the-script-task"></a>Extender el paquete con la tarea Script
  La tarea Script amplía las capacidades de tiempo de ejecución de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] paquetes con código personalizado escrito en [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic o [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# que se compila y ejecuta en tiempo de ejecución del paquete. La tarea Script simplifica el desarrollo de una tarea personalizada en tiempo de ejecución cuando las tareas incluidas con [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] no satisfacen totalmente sus requisitos. La tarea Script escribe todo el código de infraestructura necesario, lo que le permite centrarse exclusivamente en el código que se requiere para el procesamiento personalizado.  
  
 Una tarea Script interactúa con el paquete contenedor a través de la información global de **Dts** (objeto), una instancia de la <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> clase que se expone en el entorno de scripting. Puede escribir el código de una tarea Script que modifica los valores almacenados en variables de [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]; más adelante, el paquete puede utilizar esos valores actualizados para determinar la ruta de acceso del flujo de trabajo. La tarea Script también puede utilizar el espacio de nombres de [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] y la biblioteca de clases de [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], además de los ensamblados personalizados, para implementar la funcionalidad personalizada.  
  
 La tarea Script y el código de infraestructura que genera simplifican significativamente el proceso de desarrollar una tarea personalizada. Sin embargo, para entender cómo funciona la tarea Script, quizá le resulte útil leer la sección [desarrollar una tarea personalizada](../../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md) a comprender los pasos que intervienen en el desarrollo de una tarea personalizada.  
  
 Si crea una tarea que piensa reutilizar en varios paquetes, considere desarrollar una tarea personalizada en lugar de utilizar la tarea Script. Para obtener más información, consulte [comparar soluciones de Scripting y objetos personalizados](../../../integration-services/extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md).  
  
## <a name="in-this-section"></a>En esta sección  
 Los temas siguientes proporcionan más información sobre la tarea Script.  
  
 [Configurar la tarea de secuencia de comandos en el Editor de la tarea de secuencia de comandos](../../../integration-services/extending-packages-scripting/task/configuring-the-script-task-in-the-script-task-editor.md)  
 Explica cómo las propiedades que se configura en el **Editor de la tarea de secuencia de comandos** afectan a las capacidades y el rendimiento del código de la tarea de secuencia de comandos.  
  
 [Codificar y depurar la tarea de secuencia de comandos](../../../integration-services/extending-packages-scripting/task/coding-and-debugging-the-script-task.md)  
 Explica cómo usar [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools para aplicaciones (VSTA) para desarrollar los scripts que se encuentran en la tarea de secuencia de comandos.  
  
 [Uso de Variables en la tarea de secuencia de comandos](../../../integration-services/extending-packages-scripting/task/using-variables-in-the-script-task.md)  
 Explica cómo utilizar las variables a través de la propiedad <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A>.  
  
 [Conectarse a orígenes de datos de la tarea de secuencia de comandos](../../../integration-services/extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md)  
 Explica cómo utilizar las conexiones a través de la propiedad <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A>.  
  
 [Generar eventos en la tarea de secuencia de comandos](../../../integration-services/extending-packages-scripting/task/raising-events-in-the-script-task.md)  
 Explica cómo provocar los eventos a través de la propiedad <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A>.  
  
 [Registro en la tarea de secuencia de comandos](../../../integration-services/extending-packages-scripting/task/logging-in-the-script-task.md)  
 Explica cómo registrar información a través del método <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A>.  
  
 [Devolver los resultados de la tarea de secuencia de comandos](../../../integration-services/extending-packages-scripting/task/returning-results-from-the-script-task.md)  
 Explica cómo devolver los resultados mediante las propiedades <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> y <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A>.  
  
 [Ejemplos de la tarea de secuencia de comandos](../../../integration-services/extending-packages-scripting-task-examples/script-task-examples.md)  
 Proporciona ejemplos simples que muestran varios posibles usos de una tarea Script.  
  
## <a name="see-also"></a>Vea también  
 [Tarea de secuencia de comandos](../../../integration-services/control-flow/script-task.md)   
 [Comparación de la tarea Script y el componente de Script](../../../integration-services/extending-packages-scripting/comparing-the-script-task-and-the-script-component.md)  
  
  
