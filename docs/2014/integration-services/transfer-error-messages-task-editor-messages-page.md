---
title: Transferir el Editor de tareas de mensajes de Error (página mensajes) | Documentos de Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.transfererrormessagestask.errormessages.F1
helpviewer_keywords:
- Transfer Error Messages Task Editor
ms.assetid: cb2226a0-3037-4fdf-966f-81eabc0da9cf
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 833f092574c85ab83f6a384b77e7f8c99c91b2c3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36112501"
---
# <a name="transfer-error-messages-task-editor-messages-page"></a>Editor de la tarea Transferir mensajes de error (página Mensajes)
  Use la página**Mensajes** del cuadro de diálogo **Editor de la tarea Transferir mensajes de error** para especificar propiedades para copiar uno o varios mensajes de error definidos por el usuario de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] de una instancia de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] a otra. Para obtener más información acerca de esta tarea, vea [Transfer Error Messages Task](control-flow/transfer-error-messages-task.md).  
  
## <a name="options"></a>Opciones  
 **SourceConnection**  
 Seleccione un administrador de conexiones SMO de la lista, o bien haga clic en **\<Nueva conexión…>** para crear una conexión al servidor de origen.  
  
 **DestinationConnection**  
 Seleccione un administrador de conexiones SMO de la lista o haga clic en **\<Nueva conexión…>** para crear una conexión al servidor de destino.  
  
 **IfObjectExists**  
 Seleccione si la tarea debe sobrescribir mensajes de error definidos por el usuario existentes, omitir mensajes existentes o generar un error si existen ya mensajes de error con el mismo nombre en el servidor de destino.  
  
 **TransferAllErrorMessages**  
 Seleccione si la tarea debe copiar todos los mensajes definidos por el usuario o solo los especificados del servidor de origen al de destino.  
  
 Esta propiedad presenta las opciones indicadas en la siguiente tabla:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|**True**|Copiar todos los mensajes definidos por el usuario.|  
|**False**|Copiar solo los mensajes definidos por el usuario especificados.|  
  
 **ErrorMessagesList**  
 Haga clic en el botón para examinar **(…)** para seleccionar los mensajes de error que se van a copiar.  
  
> [!NOTE]  
>  Para poder seleccionar los mensajes de error que se van a copiar, debe especificar el parámetro **SourceConnection** .  
  
 **ErrorMessageLanguagesList**  
 Haga clic en el botón para examinar **(…)** para seleccionar los idiomas para los que se van a copiar mensajes de error definidos por el usuario al servidor de destino. Debe existir una versión en us_english (página de códigos 1033) del mensaje en el servidor de destino para poder transferir versiones en otros idiomas del mensaje a ese servidor.  
  
> [!NOTE]  
>  Para poder seleccionar los mensajes de error que se van a copiar, debe especificar el parámetro **SourceConnection** .  
  
## <a name="see-also"></a>Vea también  
 [Referencia de mensajes y Error de Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Tareas de Integration Services](control-flow/integration-services-tasks.md)   
 [Transferir mensajes de Error, Editor de tareas &#40;página General&#41;](general-page-of-integration-services-designers-options.md)   
 [Administrador de conexiones SMO.](connection-manager/smo-connection-manager.md)   
 [Transferir mensajes de Error, Editor de tareas &#40;página General&#41;](general-page-of-integration-services-designers-options.md)   
 [Administrador de conexiones SMO](connection-manager/smo-connection-manager.md)  
  
  