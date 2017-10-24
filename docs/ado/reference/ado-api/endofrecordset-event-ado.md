---
title: Evento EndOfRecordset (ADO) | Documentos de Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- EndOfRecordset
- Recordset::EndOfRecordset
helpviewer_keywords:
- EndOfRecordset event [ADO]
ms.assetid: 475de5e2-f634-4954-9edf-0027a6ba38d6
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4cf00efb278f6ea9937bd0fa87f929d45b8294cb
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="endofrecordset-event-ado"></a>Evento EndOfRecordset (ADO)
El **EndOfRecordset** evento se invoca cuando hay un intento para desplazarse a una fila más allá del final de la [conjunto de registros](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
EndOfRecordset fMoreData, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Parámetros  
 *fMoreData*  
 A **VARIANT_BOOL** valor que, si se establece en VARIANT_TRUE, indica que se ha agregado más filas a la **conjunto de registros**.  
  
 *adStatus*  
 Un [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) valor de estado.  
  
 Cuando **EndOfRecordset** es llama, este parámetro se establece en **adStatusOK** si la operación que provocó el evento se realizó correctamente. Se establece en **adStatusCantDeny** si este evento no puede solicitar la cancelación de la operación que produjo este evento.  
  
 Antes de **EndOfRecordset** devuelve resultados, establezca este parámetro en **adStatusUnwantedEvent** para impedir notificaciones posteriores.  
  
 *Connection*  
 A **Recordset** objeto. El **conjunto de registros** para la que se produjo este evento.  
  
## <a name="remarks"></a>Comentarios  
 Un **EndOfRecordset** evento puede producirse si la [MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) operación provocará un error.  
  
 Se llama a este controlador de eventos cuando se realiza un intento para desplazarse más allá del final de la **Recordset** objeto, quizás como resultado de llamar a **MoveNext**. Sin embargo, mientras que en este caso, podría recuperar más registros de una base de datos y agregarlos al final de la **conjunto de registros**. En ese caso, establezca *fMoreData* en VARIANT_TRUE y devuelven de **EndOfRecordset**. A continuación, llame a **MoveNext** otra vez para tener acceso a los registros recién recuperados.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de modelo de eventos de ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Resumen del controlador de eventos de ADO](../../../ado/guide/data/ado-event-handler-summary.md)

