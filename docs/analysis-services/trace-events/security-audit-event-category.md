---
title: Categoría de eventos de auditoría de seguridad | Documentos de Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 87463030a2d36ef49bbe219f8c59e876d944d4ad
ms.sourcegitcommit: 1aedef909f91dc88dc741748f36eabce3a04b2b1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="security-audit-event-category"></a>Auditoría de seguridad (categoría de eventos)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  La categoría de eventos Auditoría de seguridad tiene las clases de eventos que se describen en la siguiente tabla.  
  
|Clase de eventos|Identificador del evento|Description|  
|-----------------|--------------|-----------------|  
|Audit Login|1|Registra todos los nuevos eventos de conexión desde que se inició el seguimiento, como cuando un cliente solicitó una conexión a un servidor que ejecuta una instancia de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|Audit Logout|2|Registra todos los nuevos eventos de desconexión desde que se inició el seguimiento, como cuando un cliente envía un comando de desconexión.|  
|Audit Server Starts and Stops|4|Registra las actividades de cierre, inicio y pausa de los servicios.|  
|Audit Object Permission Event|18|Registra todos los cambios de permiso de un objeto.|  
|Audit Admin Operations Event|19|Registra las operaciones de servidor de copia de seguridad, restauración, sincronización, operaciones de adjuntar o separar, carga de imágenes y guardado de imágenes.|  
  
 Para obtener más información acerca de las columnas asociadas a cada una de las clases de evento de Auditoría de seguridad, vea [Security Audit Data Columns](../../analysis-services/trace-events/security-audit-data-columns.md).  
  
## <a name="see-also"></a>Vea también  
 [Eventos de seguimiento de Analysis Services](../../analysis-services/trace-events/analysis-services-trace-events.md)  
  
  
