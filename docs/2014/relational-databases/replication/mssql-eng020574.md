---
title: MSSQL_ENG020574 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG02574 error
ms.assetid: 4e98f8de-287c-4090-81ee-dc8f80dfa6a1
caps.latest.revision: 10
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 155e309744ce2eb6a832464efbdaf23bf382ede8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37152166"
---
# <a name="mssqleng020574"></a>MSSQL_ENG020574
    
## <a name="message-details"></a>Detalles del mensaje  
  
|||  
|-|-|  
|Nombre del producto|SQL Server|  
|Identificador del evento|20574|  
|Origen del evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nombre simbólico||  
|Texto del mensaje|La suscripción del suscriptor '%s' al artículo '%s' en la publicación '%s' no pasó la validación de datos.|  
  
## <a name="explanation"></a>Explicación  
 Los datos del suscriptor se validaron con los datos del publicador y no coinciden, por lo que se ha generado un error en la validación. Para obtener más información acerca de la validación, consulte [Validate Replicated Data](validate-replicated-data.md).  
  
## <a name="user-action"></a>Acción del usuario  
 Se recomienda que realice lo siguiente:  
  
-   Determine el motivo por el que se ha producido un error en la validación.  
  
-   Corrija el problema subyacente que ha causado el error.  
  
-   Establezca la convergencia de los datos reinicializando la suscripción o mediante otro método.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de errores y eventos &#40;replicación&#41;](errors-and-events-reference-replication.md)  
  
  
