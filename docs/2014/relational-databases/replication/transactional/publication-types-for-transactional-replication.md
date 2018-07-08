---
title: Tipos de publicaciones para la replicación transaccional | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- transactional replication, publications
ms.assetid: ad66aa34-3e37-401e-a6a1-fc1514eb6d50
caps.latest.revision: 31
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 88941deda14053fdf2eac1e1600b4ef02253b401
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37181902"
---
# <a name="publication-types-for-transactional-replication"></a>Tipos de publicaciones para la replicación transaccional
  La replicación transaccional ofrece tres tipos de publicaciones:  
  
|Tipo de publicación|Descripción|  
|----------------------|-----------------|  
|Publicación transaccional estándar|Apropiada para topologías en las que todos los datos del suscriptor son de solo lectura (la replicación transaccional no exige que esto se cumpla en el suscriptor).<br /><br /> Las publicaciones transaccionales estándar se crean de manera predeterminada cuando se usa Transact-SQL o Replication Management Objects (RMO). Cuando se utiliza el Asistente para nueva publicación, se crean seleccionando **Publicación transaccional** en la página **Tipo de publicación** .<br /><br /> Para obtener más información sobre la creación de publicaciones, vea [Publish Data and Database Objects (Publicar datos y objetos de base de datos)](../publish/publish-data-and-database-objects.md).|  
|Publicación transaccional en una topología punto a punto|Las características de este tipo de publicación son:<br /><br /> Cada ubicación tiene datos idénticos y funciona como publicador y como suscriptor.<br /><br /> Una misma fila solo se puede cambiar en una ubicación a la vez.<br /><br /> Esta topología es más apropiada para los entornos de servidor que necesitan una gran disponibilidad y escalabilidad de lectura.<br /><br /> <br /><br /> Para obtener más información, consulte [Peer-to-Peer Transactional Replication](peer-to-peer-transactional-replication.md).|  
  
## <a name="see-also"></a>Vea también  
 [Transactional Replication](transactional-replication.md) (Replicación transaccional)  
  
  
