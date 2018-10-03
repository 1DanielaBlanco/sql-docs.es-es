---
title: Información general sobre seguridad (replicación) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- authorization [SQL Server replication]
- cryptography [SQL Server replication]
- encryption [SQL Server replication]
- security [SQL Server replication], about security
- authentication [SQL Server replication]
ms.assetid: 27828fe4-3b54-4c33-886e-08e8279e34b5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9beafd39b57e89692dca117cb215cf06704323b2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47643123"
---
# <a name="security-overview-replication"></a>Información general sobre seguridad (replicación)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Básicamente, la protección del entorno de replicación consiste en conocer las opciones de autenticación y autorización, en usar de manera apropiada las características de filtrado de la replicación y en saber cuáles son los métodos específicos para proteger cada parte del entorno de replicación. El entorno de la replicación incluye el distribuidor, el publicador, los suscriptores y la carpeta de instantáneas. Este capítulo trata el tema de la seguridad de la replicación, pero la seguridad de la replicación depende de la seguridad de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] y la seguridad de Windows. Por consiguiente, debería partir del conocimiento de esta base, así como de los aspectos de seguridad específicos de la replicación. Para más información, vea [Consideraciones de seguridad para una instalación de SQL Server](../../../sql-server/install/security-considerations-for-a-sql-server-installation.md). Para obtener más información acerca de las consideraciones para la publicación de Oracle, vea la sección sobre el modelo de seguridad de replicación en el tema [Design Considerations and Limitations for Oracle Publishers](../../../relational-databases/replication/non-sql/design-considerations-and-limitations-for-oracle-publishers.md).  
  
## <a name="in-this-section"></a>En esta sección  
 [Mitigar amenazas y vulnerabilidades &#40;replicación&#41;](../../../relational-databases/replication/security/threat-and-vulnerability-mitigation-replication.md)  
 Aborda las amenazas potenciales a una topología de replicación y describe maneras de reducir esas amenazas.  
  
 [Identidad y control de acceso &#40;replicación&#41;](../../../relational-databases/replication/security/identity-and-access-control-replication.md)  
 Describe cómo utilizar autenticación, autorización y filtrado para ayudar a proteger una topología de replicación.  
  
 [Desarrollo seguro &#40;replicación&#41;](../../../relational-databases/replication/security/secure-development-replication.md)  
 Describe el comportamiento de seguridad de la replicación, las prácticas recomendadas que se aplican a la seguridad de la replicación y la replicación con menos permisos.  
  
 [Implementación segura &#40;replicación&#41;](../../../relational-databases/replication/security/secure-deployment-replication.md)  
 Describe cómo proteger mejor todos los componentes de una topología de replicación.  
  
## <a name="see-also"></a>Ver también  
 [Seguridad y protección &#40;replicación&#41;](../../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  
