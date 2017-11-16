---
title: "Especificar que no se debe realizar un seguimiento de las eliminaciones para los artículos de mezcla | Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: TSQL
helpviewer_keywords:
- conditional delete tracking [SQL Server replication]
- merge replication [SQL Server replication], conditional delete tracking
ms.assetid: 0fe330ca-5fb5-422e-ad6f-92fb5d6a3b6c
caps.latest.revision: "34"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 37186bd7f51d2091133b15dbbb3bc88398e9b9cf
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="specify-that-deletes-should-not-be-tracked-for-merge-articles"></a>Especificar que no se debe realizar un seguimiento de las eliminaciones para los artículos de mezcla
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 De forma predeterminada, la replicación de mezcla sincroniza los comandos DELETE entre el Publicador y Suscriptor. La replicación de mezcla le permite conservar filas en la base de datos de suscripciones incluso cuando se han eliminado de la publicación, y viceversa. Puede especificar mediante programación que se omitan los comandos DELETE al crear un nuevo artículo o puede habilitar esta funcionalidad en un momento posterior usando los procedimientos almacenados de replicación.  
  
> [!IMPORTANT]  
>  Al habilitar esta funcionalidad se producirá la no convergencia, lo que significa que los datos presentes en el Suscriptor no reflejarán con precisión los datos en el Publicador. Debe implementar su propio mecanismo para quitar manualmente las filas eliminadas.  
  
### <a name="to-specify-that-deletes-be-ignored-for-a-new-merge-article"></a>Para especificar que se omitan las eliminaciones para un nuevo artículo de mezcla  
  
1.  En la base de datos de publicación del publicador, ejecute [sp_addmergearticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Especifique un valor de **false** para **@delete_tracking**. Para más información, consulte [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
    > [!NOTE]  
    >  Si la tabla de origen de un artículo ya está publicada en otra publicación, el valor de **delete_tracking** debe ser el mismo en los dos artículos.  
  
### <a name="to-specify-that-deletes-be-ignored-for-an-existing-merge-article"></a>Para especificar que se omitan las eliminaciones para un artículo de mezcla existente  
  
1.  Para determinar si la compensación de errores está habilitada para un artículo, ejecute [sp_helpmergearticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md) y observe el valor de **delete_tracking** en el conjunto de resultados. Si este valor es **0**, ya se están omitiendo las eliminaciones.  
  
2.  Si el valor del paso 1 es **1**, ejecute [sp_changemergearticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) en la base de datos de publicación del publicador. Especifique un valor de **delete_tracking** para **@property**y un valor de **false** para **@value**.  
  
    > [!NOTE]  
    >  Si la tabla de origen de un artículo ya está publicada en otra publicación, el valor de **delete_tracking** debe ser el mismo en los dos artículos.  
  
## <a name="see-also"></a>Vea también  
 [Optimizar el rendimiento de la replicación de mezcla con seguimiento condicional de eliminaciones](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-conditional-delete-tracking.md)  
  
  
