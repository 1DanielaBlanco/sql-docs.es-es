---
title: Catalog Metadata (objeto de SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance-monitor
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Catalog Metadata
ms.assetid: 665e63e6-4bd2-4091-92a5-327364db2f8d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 84a8e5324d5dcb1f2727fbc73d3a9c1f75fda618
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2018
ms.locfileid: "51558372"
---
# <a name="sql-server-catalog-metadata-object"></a>SQL Server, objeto de metadatos de catálogo
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
El objeto de rendimiento **Metadatos de SQLServer:Catalog** proporciona contadores para los metadatos de catálogo de SQL Server.

En la tabla siguiente se describen los objetos de rendimiento de **metadatos de catálogo** de SQL Server.


|**Contadores de metadatos de catálogo de SQL Server**|Descripción|  
|-------------|-----------------|  
|**Catalog Metadata Object**|Número de entradas en la caché de metadatos de catálogo.|
|**Cache Entries Pinned Count**|Número de entradas de caché de metadatos de catálogo que están fijadas.|
|**Frecuencia de aciertos de caché**|Proporción entre aciertos de caché de metadatos de catálogo y búsquedas.|
|**Base de frecuencia de aciertos de caché**|Exclusivamente para uso interno.|

Hay una instancia del contador para cada base de datos.

## <a name="see-also"></a>Ver también  
[Supervisar el uso de recursos (Monitor de sistema)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)
