---
title: Editor de la tarea de lector de datos WMI (página Opciones de WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmidatareadertask.wmiquery.f1
helpviewer_keywords:
- WMI Data Reader Task Editor
ms.assetid: 4b8d4716-882d-41b0-b77e-e0e2741a2cd5
caps.latest.revision: 39
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c4af6d3458cba6e622c117ace4add62127670f13
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37152416"
---
# <a name="wmi-data-reader-task-editor-wmi-options-page"></a>Editor de la tarea Lector de datos WMI (página Opciones WMI)
  Use la página **Opciones WMI** del cuadro de diálogo **Editor de la tarea Lector de datos WMI** para especificar el origen de la consulta WQL (Lenguaje de consulta de Instrumental de administración de Windows) y el destino del resultado de la consulta.  
  
 Para obtener información acerca de esta tarea, vea [WMI Data Reader Task](control-flow/wmi-data-reader-task.md). Para obtener más información sobre WQL (Lenguaje de consulta de WMI), vea el tema de Instrumental de administración de Windows sobre cómo [realizar consultas con WQL](http://go.microsoft.com/fwlink/?LinkId=79045)en MSDN Library.  
  
## <a name="static-options"></a>Opciones estáticas  
 **WMIConnectionName**  
 Seleccione un administrador de conexiones WMI de la lista o haga clic en \<**Nueva conexión WMI…**> para crear un administrador de conexiones.  
  
 **Temas relacionados**: [Administrador de conexiones WMI](connection-manager/wmi-connection-manager.md), [Editor del administrador de conexiones WMI](../../2014/integration-services/wmi-connection-manager-editor.md).  
  
 **WQLQuerySourceType**  
 Seleccione el tipo de origen de la consulta WQL que ejecuta la tarea. Esta propiedad presenta las opciones indicadas en la siguiente tabla.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|**Entrada directa**|Establezca el origen en una consulta WQL. Al seleccionar este valor se muestra la opción dinámica **WQLQuerySourceType**.|  
|**Conexión de archivos**|Seleccione el archivo que contiene la consulta WQL. Al seleccionar este valor se muestra la opción dinámica **WQLQuerySourceType**.|  
|**Variable**|Establezca el origen en una variable que defina la consulta WQL. Al seleccionar este valor se muestra la opción dinámica **WQLQuerySourceType**.|  
  
 **OutputType**  
 Especifique si la salida debe ser una tabla de datos, un valor de propiedad o un valor y nombre de propiedad.  
  
 **OverwriteDestination**  
 Especifica si mantener, sobrescribir o anexar a los datos originales en el archivo de destino o variable.  
  
 **DestinationType**  
 Seleccione el tipo de destino de la consulta WQL que ejecuta la tarea. Esta propiedad presenta las opciones indicadas en la siguiente tabla.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|**Conexión de archivos**|Seleccione un archivo donde guardar los resultados de la consulta WQL. Al seleccionar este valor se muestra la opción dinámica **DestinationType**.|  
|**Variable**|Establezca la variable donde almacenar los resultados de la consulta WQL. Al seleccionar este valor se muestra la opción dinámica **DestinationType**.|  
  
## <a name="wqlquerysourcetype-dynamic-options"></a>Opciones dinámicas WQLQuerySourceType  
  
### <a name="wqlquerysourcetype--direct-input"></a>WQLQuerySourceType = Entrada directa  
 **WQLQuerySource**  
 Proporcione una consulta o haga clic en los puntos suspensivos (…) y escriba una consulta mediante el cuadro de diálogo **Consulta WQL** .  
  
### <a name="wqlquerysourcetype--file-connection"></a>WQLQuerySourceType = Conexión de archivos  
 **WQLQuerySource**  
 Seleccione un administrador de conexiones de archivos de la lista, o bien haga clic en \<**Nueva conexión…**> para crear un administrador de conexiones.  
  
 **Temas relacionados:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="wqlquerysourcetype--variable"></a>WQLQuerySourceType = Variable  
 **WQLQuerySource**  
 Seleccione una variable de la lista o haga clic en \<**Nueva variable…**> para crear una.  
  
 **Temas relacionados:** [Variables de Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md), [Agregar variable](../../2014/integration-services/add-variable.md)  
  
## <a name="destinationtype-dynamic-options"></a>Opciones dinámicas DestinationType  
  
### <a name="destinationtype--file-connection"></a>DestinationType = Conexión de archivos  
 **Destino**  
 Seleccione un administrador de conexiones de archivos de la lista, o bien haga clic en \<**Nueva conexión…**> para crear un administrador de conexiones.  
  
 **Temas relacionados:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="destinationtype--variable"></a>DestinationType = Variable  
 **Destino**  
 Seleccione una variable de la lista o haga clic en \<**Nueva variable…**> para crear una.  
  
 **Temas relacionados:** [Variables de Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md), [Agregar variable](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>Vea también  
 [Referencia de mensajes y Error de Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor de tareas de lector de datos WMI &#40;página General&#41;](general-page-of-integration-services-designers-options.md)   
 [Página expresiones](expressions/expressions-page.md)   
 [Tarea Monitor de eventos WMI](control-flow/wmi-event-watcher-task.md)  
  
  
