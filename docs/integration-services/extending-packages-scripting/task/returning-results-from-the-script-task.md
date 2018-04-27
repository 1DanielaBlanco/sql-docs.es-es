---
title: Devolver los resultados de la tarea Script | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: extending-packages-scripting
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], status information
- ExecutionValue property
- status information [Integration Services]
- TaskResult property
- SSIS Script task, status information
ms.assetid: ac06805b-c2db-44bd-af5c-5a0debe36dd7
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d35de3c0c4b715058ff2032a5ada6a6298c25fd2
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="returning-results-from-the-script-task"></a>Devolver los resultados de la tarea Script
  La tarea Script utiliza las propiedades <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> y <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> opcional para devolver información de estado al módulo ejecutable de [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] que se puede utilizar para determinar la ruta de acceso del flujo de trabajo después de que la tarea Script ha finalizado.  
  
## <a name="taskresult"></a>TaskResult  
 La propiedad <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> notifica si la tarea tuvo éxito o no. Por ejemplo:  
  
 `Dts.TaskResult = ScriptResults.Success`  
  
## <a name="executionvalue"></a>ExecutionValue  
 La propiedad <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> devuelve, de manera opcional, un objeto definido por el usuario que cuantifica o proporciona más información sobre si se ha realizado correctamente la tarea Script o ha dado un error. Por ejemplo, la tarea FTP utiliza la propiedad <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> para devolver el número de archivos transferidos. La tarea Ejecutar SQL devuelve el número de filas afectadas por la tarea. <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> también se puede utilizar para determinar la ruta de acceso del flujo de trabajo. Por ejemplo:  
  
 `Dim rowsAffected as Integer`  
  
 `...`  
  
 `rowsAffected = 1000`  
  
 `Dts.ExecutionValue = rowsAffected`  
