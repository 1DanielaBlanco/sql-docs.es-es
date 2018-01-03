---
title: "Determinar el modo de edición | Documentos de Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editing data [ADO], edit mode
- ADO, editing data
ms.assetid: 4c7e010d-08cd-4e22-9b32-23c36f02f88c
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2d11cdcaf0c7f56fcce7420b530b8b179f36f514
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="determining-edit-mode"></a>Determinar el modo de edición
ADO mantiene un búfer de edición asociado al registro actual. El **EditMode** propiedad indica si se realizaron cambios en este búfer o si se ha creado un nuevo registro. Use **EditMode** para determinar el estado de edición del registro actual. Puede probar cambios pendientes si un proceso de modificación se ha interrumpido y determinar si necesita usar el **actualización** o **CancelUpdate** método.  
  
 **EditMode** devuelve uno de los **EditModeEnum** constantes, que se enumeran en la tabla siguiente.  
  
|Constante|Description|  
|--------------|-----------------|  
|**adEditNone**|No indica que no hay ninguna operación de edición en curso.|  
|**adEditInProgress**|Indica que se ha modificado pero no se guardan los datos en el registro actual.|  
|**adEditAdd**|Indica que la **AddNew** ha llamado al método y el registro actual en el búfer de copia es un nuevo registro que no se ha guardado en la base de datos.|  
|**adEditDelete**|Indica que se ha eliminado el registro actual.|  
  
 **EditMode** puede devolver un valor válido únicamente si hay un registro actual. **EditMode** devolverá un error si **BOF** o **EOF** es **True** o si se ha eliminado el registro actual.
