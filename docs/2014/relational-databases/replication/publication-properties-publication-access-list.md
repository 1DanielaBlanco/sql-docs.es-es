---
title: Propiedades de la publicación, lista de acceso a la publicación | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.pubproperties.publicationaccesslist.f1
ms.assetid: 9587bb9e-c66c-4e70-8171-09b943ec2d50
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f9945c45c1747524fe264553fdbabf816e799f17
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2018
ms.locfileid: "52776847"
---
# <a name="publication-properties-publication-access-list"></a>Propiedades de la publicación, lista de acceso a la publicación
  La página **Lista de acceso a la publicación** del cuadro de diálogo **Propiedades de la publicación** permite agregar y quitar inicios de sesión, cuentas y grupos de la lista de acceso a la publicación (PAL). La PAL es el mecanismo principal para configurar la seguridad del publicador. Al crear una publicación, la replicación crea una PAL para dicha publicación. La PAL, que ofrece funciones similares a las de una lista de control de acceso de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, contiene una lista de inicios de sesión, cuentas y grupos con permiso de acceso a la publicación.  
  
 Cuando un suscriptor se conecta al publicador o al distribuidor y solicita acceso a la publicación, el inicio de sesión del suscriptor se compara con la información de autenticación de la PAL. Esto proporciona seguridad adicional para el publicador, ya que evita que en el inicio de sesión en el publicador o el distribuidor pueda usarse una herramienta cliente para realizar directamente modificaciones en el publicador. Para obtener más información, vea [Proteger el publicador](security/secure-the-publisher.md).  
  
## <a name="options"></a>Opciones  
 **Agregar**  
 Permite agregar una nueva entrada a la lista. Puede agregar solo aquellos nombres de inicio de sesión, cuenta o grupo que ya estén definidos tanto en el publicador como en el distribuidor. Estarán definidos en ambos servidores si se usan cuentas de dominio o si se crean cuentas locales en ambos servidores.  
  
 **Quitar**  
 Permite quitar la entrada seleccionada de la lista.  
  
 **Quitar todo**  
 Quita todas las entradas de la lista.  
  
## <a name="see-also"></a>Vea también  
 [Create a Publication](publish/create-a-publication.md)   
 [Ver y modificar propiedades de publicación](publish/view-and-modify-publication-properties.md)   
 [Publicar datos y objetos de base de datos](publish/publish-data-and-database-objects.md)  
  
  
