---
title: "Close (método) (ADO MD) | Documentos de Microsoft"
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
- Close
- Cellset::Close
helpviewer_keywords: Close method [ADO MD]
ms.assetid: a3aa594d-f9d4-4654-8625-ec20153ff5d9
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 187d525cf0795457c87c540d68b62c03661e56b8
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="close-method-ado-md"></a>Close (método) (ADO MD)
Cierra un conjunto de celdas abierto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Cellset.Close  
```  
  
## <a name="remarks"></a>Comentarios  
 Mediante el **cerrar** método para cerrar un [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) objeto liberará los datos asociados, incluidos los datos en cualquier relacionados con [celda](../../../ado/reference/ado-md-api/cell-object-ado-md.md), [eje](../../../ado/reference/ado-md-api/axis-object-ado-md.md), [Posición](../../../ado/reference/ado-md-api/position-object-ado-md.md), o [miembro](../../../ado/reference/ado-md-api/member-object-ado-md.md) objetos. Cerrar un **Cellset** no lo quita de la memoria; puede cambiar sus valores de propiedad y abrirlo de nuevo más tarde. Para eliminar completamente un objeto de la memoria, establezca la variable de objeto **nada**.  
  
 Posteriormente, podrá llamar el [abiertos](../../../ado/reference/ado-md-api/open-method-ado-md.md) método para volver a abrir la **Cellset** utilizando la misma u otra cadena de origen. Mientras el **Cellset** objeto está cerrado, recuperar las propiedades o llamar a cualquier método que hacen referencia a los datos subyacentes o metadatos genera un error.  
  
## <a name="applies-to"></a>Se aplica a  
 [Objeto de conjunto de celdas (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Vea también  
 [Objeto Axis (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)   
 [Objeto Cell (ADO MD)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)   
 [Objeto de miembro (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)   
 [Open (método) (ADO MD)](../../../ado/reference/ado-md-api/open-method-ado-md.md)   
 [Objeto Position (ADO MD)](../../../ado/reference/ado-md-api/position-object-ado-md.md)   
 [State (propiedad) (ADO MD)](../../../ado/reference/ado-md-api/state-property-ado-md.md)
