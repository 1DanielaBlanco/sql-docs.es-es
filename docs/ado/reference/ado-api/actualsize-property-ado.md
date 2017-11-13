---
title: Propiedad ActualSize (ADO) | Documentos de Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Field20::ActualSize
helpviewer_keywords:
- ActualSize property [ADO]
ms.assetid: 722803d0-cef5-4d4c-b79d-3f2f58052229
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9d66019d7a71dd480f1a88a28fe94d72a176497c
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="actualsize-property-ado"></a>Propiedad ActualSize (ADO)
Indica la longitud real de un campo??? valor s en bytes.  
  
## <a name="settings-and-return-values"></a>Configuración y valores devueltos  
 Devuelve un **largo** valor.  
  
## <a name="remarks"></a>Comentarios  
 Use la **ActualSize** propiedad para devolver la longitud real de un [campo](../../../ado/reference/ado-api/field-object.md) valor del objeto. Para todos los campos, el **ActualSize** propiedad es de solo lectura. Si ADO no puede determinar la longitud de la **campo** valor de objeto, el **ActualSize** propiedad devuelve **adUnknown**.  
  
 El **ActualSize** y [DefinedSize](../../../ado/reference/ado-api/definedsize-property.md) propiedades son diferentes, como se muestra en el ejemplo siguiente. A **campo** objeto con un tipo declarado de **parámetros** y una longitud máxima de 50 caracteres devuelve un **DefinedSize** valor de la propiedad de 50, pero la  **ActualSize** devuelve el valor de propiedad es la longitud de los datos almacenados en el campo para el registro actual. **Campos** con un **DefinedSize** mayores que 255 bytes se tratan como columnas de longitud variable.  
  
## <a name="applies-to"></a>Se aplica a  
 [Objeto Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo ActualSize y DefinedSize propiedades (VB)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vb.md)   
 [Ejemplo ActualSize y DefinedSize propiedades (VC ++)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vc.md)   
 [Propiedad DefinedSize](../../../ado/reference/ado-api/definedsize-property.md)

