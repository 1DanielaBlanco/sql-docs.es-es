---
title: "Definición de filtros | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.replconflictviewer.definefilters.f1
helpviewer_keywords:
- Define Filters dialog box
ms.assetid: 1fa71d22-ce5a-4aae-ba05-4d755842aeac
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c1db30c8f31236cf3a106abd230f29454361ce43
ms.contentlocale: es-es
ms.lasthandoff: 06/22/2017

---
# <a name="define-filters"></a>Definir filtros
  El cuadro de diálogo **Definir filtros** permite definir filtros que posteriormente se aplican a conflictos de datos para obtener un subconjunto de conflictos en la cuadrícula. Para definir un filtro, elija un operador del cuadro de lista desplegable **Operador** y, a continuación, especifique un valor. Por ejemplo, si desea mostrar solamente los conflictos en los que el perdedor del conflicto es el servidor **ReplTest1**, seleccione **Igual a** en el cuadro de lista desplegable **Operador** y especifique **ReplTest1** en la primera columna **Valor** .  
  
## <a name="options"></a>Opciones  
 **Operador**  
 Seleccione un operador para el filtro, como por ejemplo **Menor o igual que**.  
  
 **Valor**  
 Escriba un valor para el filtro. La mayoría de los operadores solo requiere un valor en la primera columna **Valor** ; sin embargo, los operadores **Entre** y **No entre** requieren un valor en las dos columnas **Valor** .  
  
 **Desactivar**  
 Haga clic en este botón para borrar todos los filtros previamente definidos.  
  
## <a name="see-also"></a>Vea también  
 [Visor de conflictos de replicación de Microsoft &#40;Replicación de mezcla&#41;](../../relational-databases/replication/microsoft-replication-conflict-viewer-merge-replication.md)   
 [Visor de conflictos de replicación de Microsoft &#40;Replicación transaccional&#41;](../../relational-databases/replication/microsoft-replication-conflict-viewer-transactional-replication.md)  
  
  
