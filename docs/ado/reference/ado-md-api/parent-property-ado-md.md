---
title: Parent (propiedad) (ADO MD) | Documentos de Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Parent
- Member::Parent
helpviewer_keywords: Parent property [ADO MD]
ms.assetid: 32c278c1-d8e1-4bb7-9ecd-2fbfdffee34b
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f07be3b319d11a42567f98dc9223716eeb78de85
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="parent-property-ado-md"></a>Propiedad primaria (ADO MD)
Indica el miembro que es el elemento primario del elemento actual [miembro](../../../ado/reference/ado-md-api/member-object-ado-md.md) en una jerarquía.  
  
## <a name="return-values"></a>Valores devueltos  
 Devuelve un [miembro](../../../ado/reference/ado-md-api/member-object-ado-md.md) del objeto y es de solo lectura.  
  
## <a name="remarks"></a>Comentarios  
 Un miembro que está en el nivel superior de una jerarquía (la raíz) no tiene uno primario. Esta propiedad solo se admite en **miembro** objetos que pertenecen a un [nivel](../../../ado/reference/ado-md-api/level-object-ado-md.md) objeto. Se produce un error cuando se hace referencia a esta propiedad desde **miembro** objetos que pertenecen a un [posición](../../../ado/reference/ado-md-api/position-object-ado-md.md) objeto.  
  
## <a name="applies-to"></a>Se aplica a  
 [Objeto de miembro (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>Vea también  
 [Los elementos secundarios (propiedad, ADO MD)](../../../ado/reference/ado-md-api/children-property-ado-md.md)
