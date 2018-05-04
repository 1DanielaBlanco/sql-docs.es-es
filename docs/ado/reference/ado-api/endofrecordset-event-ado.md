---
title: Evento EndOfRecordset (ADO) | Documentos de Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
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
manager: craigg
ms.openlocfilehash: f035d61d2e8526c21960761be2db5a900666083c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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
  
 *pRecordset*  
 A **Recordset** objeto. El **conjunto de registros** para la que se produjo este evento.  
  
## <a name="remarks"></a>Comentarios  
 Un **EndOfRecordset** evento puede producirse si la [MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) operación provocará un error.  
  
 Se llama a este controlador de eventos cuando se realiza un intento para desplazarse más allá del final de la **Recordset** objeto, quizás como resultado de llamar a **MoveNext**. Sin embargo, mientras que en este caso, podría recuperar más registros de una base de datos y agregarlos al final de la **conjunto de registros**. En ese caso, establezca *fMoreData* en VARIANT_TRUE y devuelven de **EndOfRecordset**. A continuación, llame a **MoveNext** otra vez para tener acceso a los registros recién recuperados.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de modelo de eventos de ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Conexión ADO y los eventos de conjunto de registros](../../../ado/guide/data/ado-event-handler-summary.md)
