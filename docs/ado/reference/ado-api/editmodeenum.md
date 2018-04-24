---
title: EditModeEnum | Documentos de Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- EditModeEnum
helpviewer_keywords:
- EditModeEnum enumeration [ADO]
ms.assetid: 45d54b6e-db2c-4553-9fd0-528147d6da2f
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7d3734f8edbb23eb37a28a0e98eff4fad9097a67
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="editmodeenum"></a>EditModeEnum
Especifica el estado de edición de un registro.  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adEditNone**|0|No indica que no hay ninguna operación de edición en curso.|  
|**adEditInProgress**|1|Indica que se ha modificado pero no se guardan los datos en el registro actual.|  
|**adEditAdd**|2|Indica que la [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) ha llamado al método y el registro actual en el búfer de copia es un nuevo registro que no se ha guardado en la base de datos.|  
|**adEditDelete**|4|Indica que se ha eliminado el registro actual.|  
  
## <a name="adowfc-equivalent"></a>Equivalente ADO/WFC  
 Paquete: **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.EditMode.NONE|  
|AdoEnums.EditMode.INPROGRESS|  
|AdoEnums.EditMode.ADD|  
|AdoEnums.EditMode.DELETE|  
  
## <a name="applies-to"></a>Se aplica a  
 [Propiedad EditMode](../../../ado/reference/ado-api/editmode-property.md)
