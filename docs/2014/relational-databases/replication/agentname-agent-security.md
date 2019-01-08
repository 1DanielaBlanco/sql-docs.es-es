---
title: Seguridad del agente &lt;NombreAgente&gt; | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.agentnameagentsecurity.f1
ms.assetid: d34c7ef8-cf77-4ffd-887f-3c4214dfd71e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 25dc706689ec136a5423de8051fecd3c6071d5bc
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2018
ms.locfileid: "52762387"
---
# <a name="ltagentnamegt-agent-security"></a>Seguridad del agente &lt;NombreAgente&gt;
  La página **Seguridad del Agente \<NombreAgente>** permite especificar las cuentas con las que el Agente de distribución (para replicación transaccional y de instantáneas) o el Agente de mezcla (para replicación de mezcla) ejecuta y realiza conexiones con los equipos de una topología de replicación. Para obtener información sobre los permisos requeridos por los agentes y las prácticas recomendadas que se aplican a la seguridad de replicación, consulte [Modelo de seguridad del Agente de replicación](security/replication-agent-security-model.md) y [Prácticas recomendadas de seguridad de replicación](security/replication-security-best-practices.md).  
  
## <a name="options"></a>Opciones  
 Haga clic en el botón de propiedades (**...**) de la fila de cada suscriptor para obtener acceso al cuadro de diálogo **Seguridad del Agente de distribución** o **Seguridad del Agente de mezcla** . Haga clic en **Ayuda** en el cuadro de diálogo que se muestra para obtener más información sobre los permisos requeridos para las cuentas utilizadas por los agentes.  
  
 Una vez especificadas las opciones en uno de los cuadros de diálogo, la información de conexión del suscriptor aparece en la cuadrícula.  
  
 **Agente para el suscriptor**  
 El nombre de cada suscriptor.  
  
 **Conexión al distribuidor**  
 Se muestra para la replicación transaccional y de instantáneas. Contexto en el que se realiza la conexión al distribuidor. Las conexiones locales se realizan siempre utilizando el contexto de la cuenta de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows con la que se ejecuta el agente:  
  
-   Para las suscripciones de inserción, la conexión local es la conexión al distribuidor, por lo que este campo siempre mostrará: **Suplantar '\<dominio >\\< inicio de sesión\>'** o **suplantar '\<equipo >\\< inicio de sesión\>'** de inserción suscripciones.  
  
-   Para las suscripciones de extracción, la conexión se puede realizar también bajo el contexto de un inicio de sesión de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . El campo muestra uno de los siguientes: **Usar inicio de sesión '\<inicio de sesión >'**, **suplantar '\<dominio >\\< inicio de sesión\>'** o **suplantar '\<equipo >\\< inicio de sesión\>'**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] recomienda que todas las conexiones se realicen utilizando el contexto de la cuenta de Windows.  
  
 **Conexión con el publicador y distribuidor**  
 Se muestra para la replicación de mezcla. Contexto en el que se realizan las conexiones al publicador y al distribuidor. Las conexiones locales se realizan siempre utilizando el contexto de la cuenta de Windows con la que se ejecuta el agente:  
  
-   Para las suscripciones de inserción, la conexión local es la conexión al publicador y distribuidor, por lo que este campo siempre mostrará: **Suplantar '\<dominio >\\< inicio de sesión\>'** o **suplantar '\<equipo >\\< inicio de sesión\>'** de inserción suscripciones.  
  
-   Para las suscripciones de extracción, la conexión se puede realizar también bajo el contexto de un inicio de sesión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . El campo muestra uno de los siguientes: **Usar inicio de sesión '\<inicio de sesión >'**, **suplantar '\<dominio >\\< inicio de sesión\>'** o **suplantar '\<equipo >\\< inicio de sesión\>'**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] recomienda que todas las conexiones se realicen utilizando el contexto de la cuenta de Windows.  
  
 **Conexión al suscriptor**  
 Contexto en el que se realiza la conexión al suscriptor. Las conexiones locales se realizan siempre utilizando el contexto de la cuenta de Windows con la que se ejecuta el agente:  
  
-   Para las suscripciones de extracción, la conexión local es la conexión al suscriptor, por lo que este campo siempre mostrará: **Suplantar '\<dominio >\\< inicio de sesión\>'** o **suplantar '\<equipo >\\< inicio de sesión\>'** de inserción suscripciones.  
  
-   Para las suscripciones de inserción, la conexión se puede realizar también bajo el contexto de un inicio de sesión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . El campo muestra uno de los siguientes: **Usar inicio de sesión '\<inicio de sesión >'**, **suplantar '\<dominio >\\< inicio de sesión\>'** o **suplantar '\<equipo >\\< inicio de sesión\>'**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] recomienda que todas las conexiones se realicen utilizando el contexto de la cuenta de Windows.  
  
## <a name="see-also"></a>Vea también  
 [View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md)  (Ver y modificar las propiedades de una suscripción de extracción)  
 [Ver y modificar las propiedades de una suscripción de inserción](view-and-modify-push-subscription-properties.md)   
 [Administrar inicios de sesión y contraseñas en la replicación](security/manage-logins-and-passwords-in-replication.md)   
 [Modelo de seguridad del Agente de replicación](security/replication-agent-security-model.md)   
 [Seguridad y protección &#40;Replicación&#41;](security/security-and-protection-replication.md)  
  
  
