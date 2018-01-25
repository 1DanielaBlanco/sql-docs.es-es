---
title: "Opciones de validación de suscripciones (suscripciones transaccionales) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.validate.options.f1
helpviewer_keywords: Subscription Validation Options dialog box
ms.assetid: fd66ad1f-df01-4240-9e89-8f41bff12c1e
caps.latest.revision: "18"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1f6945e61fb5d5d530a4a147259cbc7347020517
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/18/2018
---
# <a name="subscription-validation-options-transactional-subscriptions"></a>Opciones de validación de suscripciones (suscripciones transaccionales)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)] Utilice el cuadro de diálogo **Opciones de validación de suscripciones** para especificar si la validación debe utilizar solo un recuento de filas o un recuento de filas y una suma de comprobación binaria.  
  
## <a name="options"></a>.  
 **Comprobar que el suscriptor tiene el mismo número de filas de datos replicados que el publicador**  
 Seleccione el tipo de validación de número de fila que debe realizarse. Para publicaciones de Oracle, la única opción disponible es **Calcular un recuento de filas real consultando las tablas directamente**.  
  
 **Comparar las sumas de comprobación para comprobar los datos de las filas**  
 Además de llevar a cabo un recuento de filas en el publicador y en el suscriptor, se calcula una suma de comprobación de todos los datos utilizando el algoritmo binario de suma de comprobación. Si el número de filas da un error, no se lleva a cabo la suma de comprobación.  
  
 **Detener el Agente de distribución después de finalizar la validación**  
 De forma predeterminada, el Agente de distribución se ejecuta sin interrupción. Seleccione esta opción para detener el agente una vez realizada la validación. Esto permite comprobar si la validación ha sido correcta antes de continuar replicando datos en el suscriptor.  
  
## <a name="see-also"></a>Ver también  
 [Validar datos en el suscriptor](../../relational-databases/replication/validate-data-at-the-subscriber.md)   
 [Validar datos replicados](../../relational-databases/replication/validate-replicated-data.md)  
  
  
