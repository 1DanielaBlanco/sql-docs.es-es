---
title: Reversión del historial de revisiones de miembro (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: ''
ms.component: non-specific
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d39d3474-20e7-429f-9c8d-fcc4eb0854fc
caps.latest.revision: 5
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3b4291383c9f2f1d41ea13997f2feeb6e7c1014d
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="rollback-member-revision-history-master-data-services"></a>Reversión del historial de revisiones de miembro (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Cada vez que se cambia un miembro, se registra un historial de revisiones de miembro. Se puede revertir un historial de revisiones de miembro a una versión anterior.  
  
## <a name="prerequisites"></a>Prerequisites  
  
-   Debe tener permiso para actualizar al menos uno de los atributos del miembro seleccionado. Al revertir un historial de revisiones, todos los valores de atributo que se puedan actualizar se revertirán a los valores de la versión anterior.  
  
-   El historial de revisiones solo está disponible cuando el tipo de registro de transacciones de la entidad es miembro.  
  
 **Para revertir el historial de revisiones de miembro**  
  
1.  En Master Data Manager, haga clic en Explorador.  
  
2.  Elija la entidad y el miembro de la reversión.  
  
3.  Haga clic en **Ver historial**.  
  
4.  Elija la revisión para revertir y luego haga clic en **Revertir**.  
  
## <a name="see-also"></a>Ver también  
 [Historial de revisiones de miembro &#40;Master Data Services&#41;](../master-data-services/member-revision-history-master-data-services.md)   
 [Cambio del tipo de registro de transacciones de entidad &#40;Master Data Services&#41;](../master-data-services/change-the-entity-transaction-log-type-master-data-services.md)  
  
  
