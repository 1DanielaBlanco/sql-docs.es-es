---
title: Categoría de eventos de informes de progreso | Documentos de Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: trace-events
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d4722ea18e493a243e6adaf64555c4e90ec4b165
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
---
# <a name="progress-reports-event-category"></a>informes de progreso, categoría de eventos
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  La categoría de eventos Informes de progreso tiene las clases de eventos que se describen en la siguiente tabla.  
  
|Clase de eventos|Identificador del evento|Description|  
|-----------------|--------------|-----------------|  
|Progress Report Begin|5|Recopila todos los eventos de inicio de informe de progreso desde que se inició el seguimiento.|  
|Progress Report End|6|Recopila todos los eventos de fin de informe de progreso desde que se inició el seguimiento.|  
|Progress Report Current|7|Recopila todos los eventos actuales de informe de progreso desde que se inició el seguimiento. Por ejemplo, durante el procesamiento, los informes actuales incluyen información de procesamiento acerca de los objetos que se están procesando (dimensiones, particiones, cubos, etc.).|  
|Progress Report Error|8|Recopila todos los eventos de error de informe de progreso desde que se inició el seguimiento.|  
  
 Todos los eventos Progress Report Begin se inician con un flujo de eventos de progreso y finalizan con un evento Progress Report End. El flujo puede incluir cualquier número de eventos Progress Report Current y Progress Report Error.  
  
 Para obtener información sobre las columnas asociadas a cada una de las clases de evento de Informes de progreso, vea [Progress Reports Data Columns](../../analysis-services/trace-events/progress-reports-data-columns.md).  
  
## <a name="see-also"></a>Vea también  
 [Eventos de seguimiento de Analysis Services](../../analysis-services/trace-events/analysis-services-trace-events.md)  
  
  
