---
title: DrilledDown (propiedad, ADO MD) | Documentos de Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- DrilledDown
- Member::DrilledDown
helpviewer_keywords:
- DrilledDown property [ADO MD]
ms.assetid: bf39dd36-fc7a-4f6e-86c0-fa71430c0d86
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f8be1a63b9d4f1c979d7670c2ed3a79766070ca4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="drilleddown-property-ado-md"></a>DrilledDown (propiedad, ADO MD)
Indica si los elementos secundarios siguen inmediatamente a la [miembro](../../../ado/reference/ado-md-api/member-object-ado-md.md) en el eje.  
  
## <a name="return-values"></a>Valores devueltos  
 Devuelve un **booleano** valor y es de solo lectura. **DrilledDown** devuelve **True** si no hay ningún miembro secundario del miembro actual en el eje. **DrilledDown** devuelve **False** si el miembro actual tiene uno o más miembros secundarios en el eje.  
  
## <a name="remarks"></a>Comentarios  
 Use la **DrilledDown** propiedad para determinar si hay al menos un elemento secundario de este miembro en el eje inmediatamente detrás de este miembro. Esta información es útil al mostrar al miembro.  
  
 Esta propiedad solo se admite en [miembro](../../../ado/reference/ado-md-api/member-object-ado-md.md) objetos que pertenecen a un [posición](../../../ado/reference/ado-md-api/position-object-ado-md.md) objeto. Se produce un error cuando se hace referencia a esta propiedad desde **miembro** objetos que pertenecen a un [nivel](../../../ado/reference/ado-md-api/level-object-ado-md.md) objeto.  
  
## <a name="applies-to"></a>Se aplica a  
 [Objeto de miembro (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>Vea también  
 [ParentSameAsPrev (propiedad, ADO MD)](../../../ado/reference/ado-md-api/parentsameasprev-property-ado-md.md)
