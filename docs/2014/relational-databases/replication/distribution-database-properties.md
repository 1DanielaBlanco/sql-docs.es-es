---
title: Propiedades de base de datos de distribución | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.distdbproperties.f1
helpviewer_keywords:
- Distribution Database Properties dialog box
ms.assetid: 0f404ab9-1237-4936-8df5-888baab6a245
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 89b8381de605ab3736afc6ac8e3a7da0d53bf9e6
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2018
ms.locfileid: "52796887"
---
# <a name="distribution-database-properties"></a>Propiedades de base de datos de distribución
  El cuadro de diálogo **Propiedades de base de datos de distribución** permite ver un número de propiedades y establecer el período de retención de transacción y retención de historial para la base de datos.  
  
## <a name="options"></a>Opciones  
 **Name**  
 Nombre de la base de datos de distribución que, de manera predeterminada, se establece 'distribución' (de solo lectura).  
  
 **Ubicaciones de archivos**  
 Ubicación del archivo de la base de datos y del archivo de registro (de solo lectura).  
  
 **Período de retención de transacción**  
 También se conoce como período de retención de distribución. Representa el tiempo durante el cual se almacenan las transacciones para la replicación transaccional. Para más información, consulte [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).  
  
 **Período de retención del historial**  
 Representa el tiempo durante el cual se almacenan los metadatos de historial para todos los tipos de replicación.  
  
 **Seguridad del Agente de lectura de cola**  
 El Agente de lectura de cola se utiliza con la replicación transaccional que admite suscripciones de actualización en cola. El Agente de lectura de cola se crea automáticamente si selecciona **Publicación transaccional con suscripciones actualizables** en la página **Tipo de publicación** del Asistente para nueva publicación. Haga clic en **Configuración de seguridad...** para cambiar la cuenta con la que el agente se ejecuta y establece conexiones con el distribuidor.  
  
 También se puede crear un Agente de lectura de cola seleccionando **Crear Agente de lectura de cola** en esta página (esta opción está deshabilitada si ya se ha creado el agente).  
  
 Puede encontrar más información de conexión para el Agente de lectura de cola en dos lugares:  
  
-   El agente se conecta al publicador con las credenciales especificadas en el cuadro de diálogo **Propiedades del publicador** , que se encuentra en la página **Publicadores** del cuadro de diálogo **Propiedades del distribuidor** .  
  
-   El agente se conecta con el suscriptor utilizando las credenciales especificadas para el Agente de distribución del Asistente para nueva suscripción.  
  
 Para más información, consulte  \\[Replication Agent Security Model](security/replication-agent-security-model.md).  
  
## <a name="see-also"></a>Vea también  
 [Configurar distribución](configure-distribution.md)   
 [Create a Pull Subscription](create-a-pull-subscription.md)   
 [Create a Push Subscription](create-a-push-subscription.md)   
 [Ver y modificar las propiedades del distribuidor y del publicador](view-and-modify-distributor-and-publisher-properties.md)  
  
  
