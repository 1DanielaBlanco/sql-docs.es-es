---
title: FT:Crawl Started (clase de eventos) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: event-classes
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Crawl Started event class
ms.assetid: 2535b856-97e8-4fb2-8ba0-5d5446355fa6
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 935bb327adbc64bb6a8ff66b85d8e87c7815bbd4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="ftcrawl-started-event-class"></a>FT:Crawl Started (clase de eventos)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  La clase de eventos **FT:Crawl Started** indica que se ha iniciado un rastreo de texto completo (llenado). Utilice esta clase de eventos para comprobar si las tareas de trabajo están recogiendo una solicitud de rastreo.  
  
## <a name="ft-crawl-started-event-class-data-columns"></a>Columnas de datos de la clase de eventos FT:Crawl Started  
  
|Nombre de columna de datos|Tipo de datos|Description|Identificador de columna|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|Id. de la base de datos en el que se ha iniciado el rastreo de texto completo. Determina el valor de una base de datos mediante la función DB_ID.|3|Sí|  
|**EventClass**|**int**|Tipo de evento = 155.|27|no|  
|**EventSequence**|**int**|Secuencia de un evento determinado de la solicitud.|51|no|  
|**IsSystem**|**int**|Indica si el evento ha ocurrido en un proceso del sistema o en un proceso de usuario. 1 = sistema, 0 = usuario.|60|Sí|  
|**ObjectID**|**int**|Identificador del objeto asignado por el sistema. El rastreo de texto completo se ha iniciado en el índice de texto completo de este objeto.|22|Sí|  
|**SessionLoginName**|**nvarchar**|Nombre de inicio de sesión del usuario que originó la sesión. Por ejemplo, si se conecta a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando inicioDeSesión1 y ejecuta una instrucción como inicioDeSesión2, **SessionLoginName** muestra inicioDeSesión1 y **LoginName** muestra inicioDeSesión2. En esta columna se muestran los inicios de sesión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.|64|Sí|  
|**SPID**|**int**|Identificador de la sesión en la que se produjo el evento.|12|Sí|  
|**StartTime**|**datetime**|Hora a la que se inició el evento, si está disponible.|14|Sí|  
|**TextData**|**ntext**|Tipo de rastreo de texto completo. El valor puede ser Completo, Incremental, Manual o Automático.|1|Sí|  
|**TransactionID**|**bigint**|Id. de la transacción asignado por el sistema.|4|Sí|  
  
## <a name="see-also"></a>Ver también  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
