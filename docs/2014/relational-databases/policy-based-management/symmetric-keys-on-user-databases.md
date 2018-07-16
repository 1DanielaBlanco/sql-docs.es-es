---
title: Claves simétricas en bases de datos de usuario | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3333ab5b-2518-4753-a0a8-57df5e5af74f
caps.latest.revision: 5
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 8f8a87976d4db4e00207822bbd171e2fb0844dcb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37284951"
---
# <a name="symmetric-keys-on-user-databases"></a>Claves simétricas en bases de datos de usuario
  Esta regla comprueba si las claves que tienen una longitud de menos de 128 bytes no utilizan el algoritmo de cifrado RC2 o RC4.  
  
## <a name="best-practices-recommendations"></a>Prácticas recomendadas  
 Utilice AES de 128 bits o más para crear las claves simétricas para el cifrado de los datos. Si el sistema operativo no admite AES, utilice 3DES.  
  
## <a name="for-more-information"></a>Para obtener más información  
 [Elegir un algoritmo de cifrado](../security/encryption/choose-an-encryption-algorithm.md)  
  
## <a name="see-also"></a>Vea también  
 [Supervisar y aplicar las prácticas recomendadas usando la administración basada en directivas](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
