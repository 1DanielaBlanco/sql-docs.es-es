---
title: ConnectComplete y desconectar eventos (ADO) | Documentos de Microsoft
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
- Disconnect
- Connection::ConnectComplete
- ConnectComplete
- Connection::Disconnect
helpviewer_keywords:
- Disconnect event [ADO]
- ConnectComplete event [ADO]
ms.assetid: 568f5252-d069-4d99-a01b-2ada87ad1304
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ee97139616af7b632ec2008f916b76d87d7f4bae
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="connectcomplete-and-disconnect-events-ado"></a>ConnectComplete y eventos (ADO) de desconexión
El **ConnectComplete** eventos se llama después de iniciarse una conexión. El **desconexión** eventos se llama después de que finalice una conexión.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
ConnectComplete pError, adStatus, pConnection  
Disconnect adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Parámetros  
 *pError*  
 Un [Error](../../../ado/reference/ado-api/error-object.md) objeto. Describe el error que se ha producido si el valor de *adStatus* es **adStatusErrorsOccurred**; en caso contrario, no se establece.  
  
 *adStatus*  
 Un [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) valor que siempre devuelve **adStatusOK**.  
  
 Cuando **ConnectComplete** es llama, este parámetro se establece en **adStatusCancel** si un **WillConnect** evento ha solicitado la cancelación de la conexión pendiente.  
  
 Antes de que cualquiera evento vuelva, establezca este parámetro en **adStatusUnwantedEvent** para impedir notificaciones posteriores. Sin embargo, cerrar y volver a la [conexión](../../../ado/reference/ado-api/connection-object-ado.md) hace que estos eventos se vuelve a producir.  
  
 *pConnection*  
 El **conexión** el objeto para el que se aplica este evento.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de modelo de eventos de ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Conexión ADO y los eventos de conjunto de registros](../../../ado/guide/data/ado-event-handler-summary.md)
