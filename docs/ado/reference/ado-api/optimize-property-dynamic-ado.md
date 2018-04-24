---
title: Optimizar la propiedad dinámica (ADO) | Documentos de Microsoft
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
helpviewer_keywords:
- Optimize property [ADO]
ms.assetid: a491c4ce-2b04-4c84-be83-3846bde8d16b
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a21eec363c7c611ae9b21e590f27eb2351df74df
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="optimize-property-dynamic-ado"></a>Optimizar la propiedad dinámica (ADO)
Especifica si se debe crear un índice en una [campo](../../../ado/reference/ado-api/field-object.md).  
  
## <a name="settings-and-return-values"></a>Configuración y valores devueltos  
 Establece o devuelve un **booleano** valor que indica si se debe crear un índice.  
  
## <a name="remarks"></a>Comentarios  
 Un índice puede mejorar el rendimiento de las operaciones que buscan u ordenar los valores de un [conjunto de registros](../../../ado/reference/ado-api/recordset-object-ado.md). El índice es interno a ADO; explícitamente no se puede obtener acceso a o utilizarlo en su aplicación.  
  
 Para crear un índice en un campo, establezca la **optimizar** propiedad **True**. Para eliminar el índice, establezca esta propiedad en **False**.  
  
 **Optimizar** es una propiedad dinámica que se anexa a la [campo](../../../ado/reference/ado-api/field-object.md) objeto [propiedades](../../../ado/reference/ado-api/properties-collection-ado.md) colección cuando la [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) propiedad está establecida en **adUseClient**.  
  
## <a name="usage"></a>Uso  
  
```  
Dim rs As New Recordset  
Dim fld As Field  
rs.CursorLocation = adUseClient      'Enable index creation  
rs.Fields.Append "Field1", adChar, 35, adFldIsNullable  
rs.Open  
Set fld = rs.Fields(0)  
fld.Properties("Optimize") = True    'Create an index  
fld.Properties("Optimize") = False   'Delete an index  
```  
  
## <a name="applies-to"></a>Se aplica a  
 [Objeto Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Vea también  
 [Optimizar el ejemplo de la propiedad (VB)](../../../ado/reference/ado-api/optimize-property-example-vb.md)   
 [Optimizar el ejemplo de la propiedad (VC ++)](../../../ado/reference/ado-api/optimize-property-example-vc.md)   
 [Propiedad de filtro](../../../ado/reference/ado-api/filter-property.md)   
 [Find (método) (ADO)](../../../ado/reference/ado-api/find-method-ado.md)   
 [Propiedad de ordenación](../../../ado/reference/ado-api/sort-property.md)
