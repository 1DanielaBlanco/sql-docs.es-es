---
title: Superposición correcta de la máscara de afinidad y la máscara de entrada y salida de afinidad | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 1a0da6df-57ff-4f3f-aae9-2fbc4897508c
caps.latest.revision: 11
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5e1ea7389ef027b9ef4adee955ee51699f8f1785
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="correct-affinity-mask-and-affinity-input-and-output-mask-overlap"></a>Superposición correcta de la máscara de afinidad y la máscara de entrada y salida de afinidad
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Esta regla comprueba si la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tiene uno o varios procesadores que están asignados para usarse con las opciones de máscara de afinidad y de máscara de afinidad de E/S. En un equipo con más de un procesador, las opciones de máscara de afinidad y de máscara de afinidad de E/S se utilizan para designar qué CPU usa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Al habilitar una CPU con la máscara de afinidad y con la máscara de afinidad de E/S, se puede ralentizar el rendimiento al exigir que el procesador se use demasiado.  
  
## <a name="best-practices-recommendations"></a>Prácticas recomendadas  
 Al especificar las opciones de máscara de afinidad o de máscara de afinidad de E/S, debería especificar ambas, pero habilitar cada CPU únicamente una vez.  
  
 No habilite la misma CPU en ambas opciones de máscara de afinidad y de máscara de afinidad de E/S. Los bits que corresponden a cada CPU deberían estar en alguno de los estados siguientes:  
  
-   0 tanto en la opción de máscara de afinidad de E/S como en la opción máscara de afinidad.  
  
-   0 en la opción de máscara de afinidad y 1 en la opción de máscara de afinidad de E/S.  
  
-   1 en la opción de máscara de afinidad y 0 en la opción de máscara de afinidad de E/S.  
  
## <a name="for-more-information"></a>Para obtener más información  
 [affinity mask (opción de configuración del servidor)](../../database-engine/configure-windows/affinity-mask-server-configuration-option.md)  
  
 [affinity Input-Output mask (opción de configuración del servidor)](../../database-engine/configure-windows/affinity-input-output-mask-server-configuration-option.md)  
  
 [affinity64 mask (opción de configuración del servidor)](../../database-engine/configure-windows/affinity64-mask-server-configuration-option.md)  
  
 [affinity64 I/O mask (opción de configuración del servidor)](../../database-engine/configure-windows/affinity64-input-output-mask-server-configuration-option.md)  
  
## <a name="see-also"></a>Ver también  
 [Supervisar y aplicar las prácticas recomendadas usando la administración basada en directivas](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
