---
title: "Reinicializar suscripciones: Todas las suscripciones | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.reinit.all.f1"
helpviewer_keywords: 
  - "Reinicializar suscripciones, cuadro de diálogo"
ms.assetid: e1122018-9f74-43e3-8489-7eae33ff23d9
caps.latest.revision: 11
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 11
---
# Reinicializar suscripciones: Todas las suscripciones
  El **reinicializar suscripciones** cuadro de diálogo le permite marcar todas las suscripciones a una publicación para su reinicialización. La reinicialización implica aplicar una instantánea a cada suscriptor; la realiza el Agente de distribución para las suscripciones a publicaciones transaccionales y el Agente de mezcla para las suscripciones a publicaciones de combinación.  
  
## Opciones  
 **Utilizar la instantánea actual**  
 Seleccione esta opción para aplicar la instantánea actual a cada suscriptor la próxima vez que ejecute el Agente de distribución o el Agente de mezcla para la suscripción. Si no hay ninguna instantánea válida disponible, esta opción no puede seleccionarse.  
  
 **Utilizar una instantánea nueva**  
 Seleccione esta opción para reinicializar todas las suscripciones con una instantánea nueva. La instantánea solo puede aplicarse a cada suscriptor tras haber sido generada por el Agente de instantáneas. Si el Agente de instantáneas está configurado para ejecutarse de forma programada, las suscripciones no se reinicializarán hasta la siguiente ejecución programada del mismo.  
  
 Seleccione **Generar la nueva instantánea ahora** para iniciar el Agente de instantáneas de forma inmediata.  
  
 **Cargar los cambios no sincronizados antes de reinicializar**  
 Solo replicación de mezcla. Seleccione esta opción para cargar los cambios pendientes de las bases de datos de suscripciones antes de sobrescribir los datos de los suscriptores con una instantánea.  
  
 Si se agrega, quita o modifica un filtro con parámetros, los cambios pendientes en el suscriptor no se pueden cargar en el publicador durante la reinicialización. Si desea cargar los cambios pendientes, sincronice todas las suscripciones antes de cambiar el filtro.  
  
 **Marcar para reinicializar**  
 Haga clic en esta opción para marcar cada suscripción para reinicializarla. Una vez que hay una instantánea disponible, se aplicará dicha instantánea al suscriptor la próxima vez que se ejecute el Agente de distribución o el Agente de mezcla para la suscripción.  
  
## Vea también  
 [Reinicializar suscripciones](../../relational-databases/replication/reinitialize-subscriptions.md)  
  
  