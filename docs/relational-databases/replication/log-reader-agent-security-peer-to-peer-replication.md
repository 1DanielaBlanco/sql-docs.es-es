---
title: "Seguridad del Agente de registro del LOG (replicaci&#243;n punto a punto) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.p2pwizard.LRA.f1"
ms.assetid: 6575e2a8-16bb-449c-bdca-4a4202d0972f
caps.latest.revision: 17
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 17
---
# Seguridad del Agente de registro del LOG (replicaci&#243;n punto a punto)
  La página **Seguridad del Agente de registro del LOG** permite especificar las cuentas bajo las cuales el Agente de registro del LOG de cada nodo del mismo nivel se ejecuta y establece conexiones. Para obtener información sobre los permisos requeridos por los agentes y las prácticas recomendadas de seguridad de replicación, consulte [modelo de seguridad del agente de replicación](../../relational-databases/replication/security/replication-agent-security-model.md) y [recomendaciones de seguridad de replicación](../../relational-databases/replication/security/replication-security-best-practices.md).  
  
> [!NOTE]  
>  Existe un Agente de registro del LOG para cada base de datos que se publica utilizando la replicación transaccional. Si el Agente de registro del LOG para una base de datos ya ha sido configurado (ya sea para una publicación en una ejecución anterior de este asistente o para otra publicación transaccional en la misma base de datos), no se pueden cambiar las credenciales que el agente utiliza en este asistente. Si especifica credenciales nuevas, se omitirán. Para cambiar las credenciales, utilice el cuadro de diálogo **Propiedades de la publicación** . Para más información, consulte [View and Modify Replication Security Settings](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
## Opciones  
 Haga clic en el botón de propiedades (**...**) en la fila para cada elemento del mismo nivel tener acceso a la **seguridad del agente de lector de registro** cuadro de diálogo. Haga clic en **Ayuda** en el cuadro de diálogo **Seguridad del Agente de registro del LOG** que se inicia para obtener más información acerca de los permisos requeridos para las cuentas que utilizan los agentes.  
  
 Una vez que se ha especificado la configuración en el cuadro de diálogo, se muestra la información de conexión para el suscriptor en la cuadrícula.  
  
 **Agentes para el publicador**  
 Nombre de cada instancia de servidor del mismo nivel.  
  
 **Base de datos del mismo nivel**  
 Base de datos que actúa como base de datos de publicaciones y base de datos de suscripciones en cada nodo del mismo nivel.  
  
 **Conexión al distribuidor**  
 Contexto en el que se realiza la conexión al distribuidor. La conexión al distribuidor local siempre se realiza utilizando el contexto de la [!INCLUDE[msCoName](../../includes/msconame-md.md)] cuenta de Windows bajo la que se ejecuta el agente, por lo que este campo siempre mostrará **suplantar ' \< dominio>\\< inicio de sesión\>'** o **suplantar ' \< equipo>\\< inicio de sesión\>'**.  
  
 **Conexión al publicador**  
 Contexto bajo el cual se establece la conexión al publicador. La conexión al publicador se puede establecer utilizando un inicio de sesión de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o utilizando el contexto de la cuenta de Windows bajo la que se ejecuta el agente. El campo muestra uno de los siguientes: **Usar inicio de sesión ' \< inicio de sesión>'**, **suplantar ' \< dominio>\\< inicio de sesión\>'** o **suplantar ' \< equipo>\\< inicio de sesión\>'**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] recomienda que todas las conexiones se realicen utilizando el contexto de la cuenta de Windows.  
  
## Vea también  
 [Administrar una topología punto a punto & #40; Programación de replicación Transact-SQL & #41;](../../relational-databases/replication/administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [Replicación transaccional punto a punto](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  