---
title: LockTypeEnum | Documentos de Microsoft
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
apitype: COM
f1_keywords: LockTypeEnum
helpviewer_keywords: LockTypeEnum enumeration [ADO]
ms.assetid: d2894eaf-4450-4ace-aa51-c8b875fd3010
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 48c9909bf228a6bad0ad7e6d44415a1499fd5ea5
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="locktypeenum"></a>LockTypeEnum
Especifica el tipo de bloqueo colocado en registros durante la edición.  
  
|Constante|Valor|Description|  
|--------------|-----------|-----------------|  
|**adLockBatchOptimistic**|4|Indica actualizaciones optimistas por lotes. Se requiere para el modo de actualización por lotes.|  
|**adLockOptimistic**|3|Indica un bloqueo optimista, registro por registro. El proveedor utiliza bloqueo optimista, bloquear registros sólo cuando se llama a la [actualización](../../../ado/reference/ado-api/update-method.md) método.|  
|**adLockPessimistic**|2|Indica un bloqueo pesimista, registro por registro. El proveedor no lo que es necesario para garantizar la modificación correcta de los registros, normalmente bloqueando los registros en el origen de datos inmediatamente después de editar.|  
|**adLockReadOnly**|1|Indica los registros de solo lectura. No se puede modificar los datos.|  
|**adLockUnspecified**|-1|No especifica un tipo de bloqueo. Para clones, el clon se crea con el mismo tipo de bloqueo que el original.|  
  
## <a name="adowfc-equivalent"></a>Equivalente ADO/WFC  
 Paquete: **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.LockType.BATCHOPTIMISTIC|  
|AdoEnums.LockType.OPTIMISTIC|  
|AdoEnums.LockType.PESSIMISTIC|  
|AdoEnums.LockType.READONLY|  
|AdoEnums.LockType.UNSPECIFIED|  
  
## <a name="applies-to"></a>Se aplica a  
  
|||  
|-|-|  
|[Clone (método) (ADO)](../../../ado/reference/ado-api/clone-method-ado.md)|[Propiedad LockType (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)|  
|[Open (método) (conjunto de registros ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|[Evento WillExecute (ADO)](../../../ado/reference/ado-api/willexecute-event-ado.md)|
