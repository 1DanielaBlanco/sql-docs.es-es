---
title: "Reinicializar suscripciones - Una suscripci&#243;n | Microsoft Docs"
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
  - "sql13.rep.reinit.single.f1"
helpviewer_keywords: 
  - "Reinicializar suscripciones, cuadro de diálogo"
ms.assetid: 9b0cf0be-d1f1-4163-a0ca-d6f095aa707e
caps.latest.revision: 11
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 11
---
# Reinicializar suscripciones - Una suscripci&#243;n
  El **reinicializar suscripciones** cuadro de diálogo le permite marcar una suscripción para reinicializarla. La reinicialización implica aplicar una instantánea al suscriptor; esta operación la realizan el Agente de distribución para suscripciones a publicaciones transaccionales y el Agente de mezcla para suscripciones a publicaciones de combinación.  
  
## Opciones  
 **Utilizar la instantánea actual**  
 Seleccione esta opción para aplicar la instantánea actual al suscriptor la próxima vez que se ejecute el Agente de distribución o el Agente de mezcla. Si no hay ninguna instantánea válida disponible, esta opción no puede seleccionarse.  
  
 **Utilizar una instantánea nueva**  
 Seleccione esta opción para reinicializar la suscripción con una instantánea nueva. La instantánea solo puede aplicarse al suscriptor después de que la haya generado el Agente de instantáneas. Si se configura el Agente de instantáneas para que se ejecute siguiendo una programación determinada, la suscripción no se reinicializará hasta que se haya producido la siguiente ejecución programada del Agente de instantáneas.  
  
 Seleccione **Generar la nueva instantánea ahora** para iniciar el Agente de instantáneas de forma inmediata.  
  
 **Cargar los cambios no sincronizados antes de reinicializar**  
 Solo replicación de mezcla. Seleccione esta opción para cargar cambios pendientes de la base de datos de suscripciones antes de que se sobrescriba el suscriptor con una instantánea.  
  
 Si se agrega, quita o modifica un filtro con parámetros, los cambios pendientes en el suscriptor no se pueden cargar en el publicador durante la reinicialización. Si desea cargar los cambios pendientes, sincronice todas las suscripciones antes de cambiar el filtro.  
  
 **Marcar para reinicializar**  
 Haga clic para marcar la suscripción para reinicializar. Una vez que hay una instantánea disponible, se aplicará dicha instantánea al suscriptor la próxima vez que se ejecute el Agente de distribución o el Agente de mezcla para la suscripción.  
  
## Vea también  
 [Reinicializar suscripciones](../../relational-databases/replication/reinitialize-subscriptions.md)  
  
  