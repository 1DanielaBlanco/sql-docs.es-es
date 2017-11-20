---
title: Ejemplos de la tarea de script | Documentos de Microsoft
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-scripting-task-examples
ms.reviewer: 
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], examples
- examples [Integration Services]
- SSIS Script task, examples
ms.assetid: b0dd77ee-ee11-4cd9-87aa-61dd67f2fe1c
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f7732abe880aa5eeaab2030da423e18d1977d64a
ms.contentlocale: es-es
ms.lasthandoff: 09/26/2017

---
# <a name="script-task-examples"></a>Ejemplos de tarea Script
  La tarea Script es una herramienta con varias funciones que puede utilizar en un paquete para satisfacer casi cualquier requisito que no cumplan las tareas incluidas con [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. En este tema se enumeran los ejemplos de código de la tarea Script que muestran alguna de las funciones disponibles.  
  
> [!NOTE]  
>  Si desea crear tareas que pueda reutilizar más fácilmente en varios paquetes, considere la posibilidad de utilizar el código de estos ejemplos de tarea Script como punto inicial de las tareas personalizadas. Para más información, vea [Desarrollar una tarea personalizada](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="in-this-section"></a>En esta sección  
  
### <a name="example-topics"></a>Temas de ejemplo  
 Esta sección contiene ejemplos de código que muestran varios usos de las clases de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] que puede incorporar en una tarea Script de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [Detectar un archivo plano vacío con la tarea Script](../../integration-services/extending-packages-scripting-task-examples/detecting-an-empty-flat-file-with-the-script-task.md)  
 Comprueba un archivo plano para determinar si contiene filas de datos, y guarda el resultado en una variable para su uso en una bifurcación del flujo de control.  
  
 [Recopilar una lista para el bucle ForEach con la tarea Script](../../integration-services/extending-packages-scripting-task-examples/gathering-a-list-for-the-foreach-loop-with-the-script-task.md)  
 Recopila una lista de archivos que cumplen los criterios especificados por el usuario y rellena una variable para su uso posterior por parte del enumerador de variable para Foreach.  
  
 [Consultar Active Directory con la tarea Script](../../integration-services/extending-packages-scripting-task-examples/querying-the-active-directory-with-the-script-task.md)  
 Recupera información de usuario de Active Directory basándose en el valor de un [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] variable, mediante las clases en el espacio de nombres System.DirectoryServices.  
  
 [Supervisar los contadores de rendimiento con la tarea Script](../../integration-services/extending-packages-scripting-task-examples/monitoring-performance-counters-with-the-script-task.md)  
 Crea un contador de rendimiento personalizado que puede usarse para realizar un seguimiento del progreso de la ejecución de un [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] paquete, mediante las clases en el espacio de nombres System.Diagnostics.  
  
 [Trabajar con imágenes con la tarea Script](../../integration-services/extending-packages-scripting-task-examples/working-with-images-with-the-script-task.md)  
 Comprime las imágenes en formato JPEG y crea las imágenes en miniatura de los mismos, mediante las clases en el espacio de nombres System.Drawing.  
  
 [Buscar impresoras instaladas con la tarea Script](../../integration-services/extending-packages-scripting-task-examples/finding-installed-printers-with-the-script-task.md)  
 Busca las impresoras instaladas que admiten un tamaño de papel específico, mediante el uso de clases en el espacio de nombres System.Drawing.Printing.  
  
 [Enviar un mensaje de correo electrónico HTML con la tarea Script](../../integration-services/extending-packages-scripting-task-examples/sending-an-html-mail-message-with-the-script-task.md)  
 Envía un mensaje de correo en formato HTML en lugar de texto simple.  
  
 [Trabajar con archivos de Excel con la tarea Script](../../integration-services/extending-packages-scripting-task-examples/working-with-excel-files-with-the-script-task.md)  
 Enumera las hojas de cálculo de un archivo de Excel y comprueba la existencia de una hoja de cálculo concreta.  
  
 [Enviar a una cola de mensajes privada remota con la tarea Script](../../integration-services/extending-packages-scripting-task-examples/sending-to-a-remote-private-message-queue-with-the-script-task.md)  
 Envía un mensaje a una cola de mensajes privada remota.  
  
### <a name="other-examples"></a>Otros ejemplos  
 Los siguientes temas también contienen ejemplos de código para su uso con la tarea Script.  
  
 [Usar variables en la tarea Script](../../integration-services/extending-packages-scripting/task/using-variables-in-the-script-task.md)  
 Solicita al usuario confirmación de si el paquete debe continuar ejecutándose, basándose en el valor de una variable de paquete que puede superar el límite especificado en otra variable.  
  
 [Conectarse a orígenes de datos de la tarea Script](../../integration-services/extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md)  
 Recupera una conexión o información de conexión de los administradores de conexión definidos en el paquete.  
  
 [Provocar eventos en la tarea Script](../../integration-services/extending-packages-scripting/task/raising-events-in-the-script-task.md)  
 Produce un error, una advertencia o un mensaje informativo basándose en el estado de conexión a Internet en el servidor.  
  
 [Registrar en la tarea Script](../../integration-services/extending-packages-scripting/task/logging-in-the-script-task.md)  
 Registra el número de elementos procesados por la tarea para los proveedores de registro habilitados.  
  
  

