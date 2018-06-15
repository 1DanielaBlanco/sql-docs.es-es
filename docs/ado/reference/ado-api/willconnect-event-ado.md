---
title: Evento WillConnect (ADO) | Documentos de Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- WillConnect
- Connection::WillConnect
helpviewer_keywords:
- WillConnect event [ADO]
ms.assetid: da561d58-eb58-446c-a4fd-1838c76073c0
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6a2ddca516e9c5141e0e874074660579e8144ba7
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35282874"
---
# <a name="willconnect-event-ado"></a>Evento WillConnect (ADO)
El **WillConnect** eventos se llama antes de iniciar una conexión.  
  
 **Se aplica a:** [objeto Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
WillConnect ConnectionString, UserID, Password, Options, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Parámetros  
 *connectionString*  
 A **cadena** que contiene información de conexión para la conexión pendiente.  
  
 *Identificador de usuario*  
 A **cadena** que contiene un nombre de usuario para la conexión pendiente.  
  
 *Contraseña*  
 A **cadena** que contiene una contraseña para la conexión pendiente.  
  
 *Opciones*  
 A **largo** valor que indica cómo el proveedor debe evaluar la *ConnectionString*. La única opción es **adAsyncOpen**.  
  
 *adStatus*  
 Un [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) valor de estado.  
  
 Cuando se llama a este evento, este parámetro se establece en **adStatusOK** de forma predeterminada. Se establece en **adStatusCantDeny** si el evento no puede solicitar la cancelación de la operación pendiente.  
  
 Antes de que se devuelve este evento, establezca este parámetro en **adStatusUnwantedEvent** para impedir notificaciones posteriores. Establezca este parámetro en **adStatusCancel** para solicitar la operación de conexión que provocó la cancelación de esta notificación.  
  
 *pConnection*  
 El [conexión](../../../ado/reference/ado-api/connection-object-ado.md) el objeto para el que se aplica esta notificación de eventos. Cambios en los parámetros de la **conexión** por el **WillConnect** controlador de eventos no tiene ningún efecto el **conexión**.  
  
## <a name="remarks"></a>Notas  
 Cuando **WillConnect** se llama, el *ConnectionString*, *UserID*, *contraseña*, y *opciones* parámetros se establecen en los valores establecidos por la operación que produjo este evento (la conexión pendiente) y se puede cambiar antes de que el evento vuelva. **WillConnect** puede devolver una solicitud de cancelación de la conexión pendiente.  
  
 Cuando se cancela este evento, **ConnectComplete** se llamará con su *adStatus* parámetro establecido en **adStatusErrorsOccurred**.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de modelo de eventos de ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Conexión ADO y los eventos de conjunto de registros](../../../ado/guide/data/ado-event-handler-summary.md)
