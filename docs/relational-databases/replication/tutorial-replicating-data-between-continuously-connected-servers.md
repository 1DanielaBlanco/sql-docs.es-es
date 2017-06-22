---
title: 'Tutorial: Replicar datos entre servidores conectados de forma continua | Microsoft Docs'
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- tutorials [SQL Server replication]
- replication [SQL Server], tutorials
- wizards [SQL Server replication]
ms.assetid: 7b18a04a-2c3d-4efe-a0bc-c3f92be72fd0
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6090a59e8f831d5d05def6f6ff65ee99a09aea84
ms.contentlocale: es-es
ms.lasthandoff: 06/22/2017

---
# <a name="tutorial-replicating-data-between-continuously-connected-servers"></a>Tutorial: Replicar datos entre servidores conectados de forma continua
La replicación es una buena solución para el problema de mover datos entre servidores conectados de forma continua. La utilización de asistentes para replicación le facilitará la configuración y administración de una topología de replicación. Este tutorial le mostrará cómo configurar una topología de replicación para servidores conectados de forma continua.  
  
## <a name="what-you-will-learn"></a>Aprendizaje  
Este tutorial le mostrará cómo publicar datos de una base de datos a otra con la replicación transaccional. En la primera lección se muestra cómo utilizar [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] para crear una publicación. En las siguientes lecciones se explica cómo crear y validar una suscripción y cómo medir la latencia.  
  
## <a name="requirements"></a>Requisitos  
Este tutorial está destinado a usuarios que están familiarizados con las operaciones básicas de las bases de datos, pero que tienen una experiencia limitada en operaciones de replicación. Para realizar este tutorial, es preciso que haya finalizado el anterior, [Preparar el servidor para replicación](../../relational-databases/replication/tutorial-preparing-the-server-for-replication.md).  
  
Para utilizar este tutorial, el sistema debe contar con los siguientes componentes:  
  
-   En el publicador (servidor de origen):  
  
    -   Cualquier edición de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], excepto Express ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]) o [!INCLUDE[ssEW](../../includes/ssew-md.md)]. Estas ediciones no pueden ser publicadores de replicación.  
  
    -   [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] Base de datos de ejemplo. Con el objeto de mejorar la seguridad, las bases de datos de ejemplo no se instalan de forma predeterminada.  
  
-   En el suscriptor (servidor de destino):  
  
    -   Cualquier edición de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], excepto [!INCLUDE[ssEW](../../includes/ssew-md.md)]. [!INCLUDE[ssEW](../../includes/ssew-md.md)] no puede ser un suscriptor de replicación transaccional.  
  
    > [!NOTE]  
    > La replicación no se instala de forma predeterminada en [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] .  
  
> [!NOTE]  
> En [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], debe conectarse al publicador y al suscriptor con un inicio de sesión que sea miembro del rol fijo de servidor **sysadmin** .  
  
**Tiempo estimado para completar este tutorial: 30 minutos.**  
  
## <a name="lessons-in-this-tutorial"></a>Lecciones de este tutorial  
  
-   [Lección 1: Publicar datos con la replicación transaccional](../../relational-databases/replication/lesson-1-publishing-data-using-transactional-replication.md)  
  
-   [Lección 2: Crear una suscripción a la publicación transaccional](../../relational-databases/replication/lesson-2-creating-a-subscription-to-the-transactional-publication.md)  
  
-   [Lección 3: Validar la suscripción y medir la latencia](../../relational-databases/replication/lesson-3-validating-the-subscription-and-measuring-latency.md)  
  
[Iniciar el tutorial](../../relational-databases/replication/lesson-1-publishing-data-using-transactional-replication.md)  
  
## <a name="see-also"></a>Vea también  
[Conceptos de la programación de replicación](../../relational-databases/replication/concepts/replication-programming-concepts.md)  
  
  
  

