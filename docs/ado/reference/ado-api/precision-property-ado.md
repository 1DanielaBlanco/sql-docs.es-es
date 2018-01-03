---
title: Propiedad Precision (ADO) | Documentos de Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Parameter::Precision
- Field20::Precision
helpviewer_keywords: Precision property [ADO]
ms.assetid: 1fa38e78-6b5b-414d-ba0a-3dd26b29b766
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fd179c5b850f9b7863cbb5881c2ecb56b4acd096
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="precision-property-ado"></a>Propiedad Precision (ADO)
Indica el grado de precisión para los valores numéricos en un [parámetro](../../../ado/reference/ado-api/parameter-object.md) objeto o numérico [campo](../../../ado/reference/ado-api/field-object.md) objetos.  
  
## <a name="settings-and-return-values"></a>Configuración y valores devueltos  
 Establece o devuelve un **bytes** valor que indica el número máximo de dígitos que se usan para representar los valores.  
  
## <a name="remarks"></a>Comentarios  
 Use la **precisión** propiedad para determinar el número máximo de dígitos que se usan para representar valores de un tipo numérico **parámetro** o **campo** objeto.  
  
 El valor es de lectura/escritura en un **parámetro** objeto.  
  
 Para una **campo**objeto, **precisión** suele ser de sólo lectura. Sin embargo, para el nuevo **campo** objetos que se han anexado a la [campos](../../../ado/reference/ado-api/fields-collection-ado.md) colección de un [registro](../../../ado/reference/ado-api/record-object-ado.md), **precisión** es de solo lectura/escritura Después de la [valor](../../../ado/reference/ado-api/value-property-ado.md) propiedad para la **campo** se ha especificado y el proveedor de datos ha agregado correctamente el nuevo **campo** mediante una llamada a la [Actualización](../../../ado/reference/ado-api/update-method.md) método de la **campos** colección.  
  
## <a name="applies-to"></a>Se aplica a  
  
|||  
|-|-|  
|[Objeto Field](../../../ado/reference/ado-api/field-object.md)|[Objeto Parameter](../../../ado/reference/ado-api/parameter-object.md)|  
  
## <a name="see-also"></a>Vea también  
 [NumericScale y ejemplo de las propiedades Precision (VB)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vb.md)   
 [NumericScale y ejemplo de las propiedades Precision (VC ++)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vc.md)   
 [NumericScale (propiedad, ADO)](../../../ado/reference/ado-api/numericscale-property-ado.md)
