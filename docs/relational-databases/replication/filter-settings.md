---
title: Configuración del filtro | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.filtersettings.f1
ms.assetid: 1b401d7d-db8a-4ba1-acb1-b8dec14e3311
caps.latest.revision: 6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ced3fd26c7391eb481366200385235ab5d699c80
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2018
ms.locfileid: "37356377"
---
# <a name="filter-settings"></a>Configuración del filtro
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  El cuadro de diálogo **Configuración del filtro** permite definir los filtros para las cuadrículas del Monitor de replicación. Por ejemplo, para mostrar únicamente las suscripciones activas en la pestaña **Todas las suscripciones** , seleccione **Estado** en la columna **Nombre de columna** , **Es igual a** en la columna **Operador** y **Activo** en la columna **Valor1** . Después de definir un filtro basado en una o más columnas, se aplica el filtro para que la cuadrícula muestre solo el subconjunto de filas que coinciden con los criterios de filtro.  
  
## <a name="options"></a>Opciones  
 **Nombre de la columna**  
 Seleccione el nombre de la columna en la que desea filtrar. Puede basar un filtro en una o más columnas.  
  
 **Operador**  
 Seleccione un operador para el filtro, como por ejemplo **Menor o igual que**.  
  
 **Valor1** y **Valor2**  
 Escriba o seleccione un valor para el filtro. La mayoría de los operadores solo requieren un valor en la columna **Valor1** ; sin embargo, los operadores **Entre** y **No entre** también requieren un valor en la do columna **Valor2** .  
  
 **Borrar filtro**  
 Haga clic en este botón para borrar todos los filtros definidos. Para quitar un único filtro, seleccione el filtro y presione la tecla Supr.  
  
## <a name="see-also"></a>Ver también  
 [Supervisar la replicación](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
