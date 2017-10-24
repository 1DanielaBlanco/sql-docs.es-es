---
title: Number (propiedad, ADO) | Documentos de Microsoft
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
- Error::Number
- Error::GetNumber
- Error::get_Number
helpviewer_keywords:
- number property [ADO]
ms.assetid: f92323c5-dd11-4a63-a505-d9014a0f067f
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8d5567283a62a31842185afce7682d3641d6fcc4
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="number-property-ado"></a>Propiedad Number (ADO)
Indica el número que identifica de forma única un [Error](../../../ado/reference/ado-api/error-object.md) objeto.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un **largo** valor que puede corresponder a uno de los [ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md) constantes.  
  
## <a name="remarks"></a>Comentarios  
 Use la **número** propiedad para determinar qué error se produjo. El valor de la propiedad es un número único que se corresponde con la condición de error.  
  
 El [errores](../../../ado/reference/ado-api/errors-collection-ado.md) colección devuelve un HRESULT en formato hexadecimal (por ejemplo, 0 x 80004005) o el valor de tipo long (por ejemplo, 2147467259). Estos HRESULT pueden ser generados por los componentes subyacentes, como OLE DB o incluso el propio OLE. Para obtener más información acerca de estos números, vea [errores (OLE DB)](http://msdn.microsoft.com/en-us/ed74e62d-4948-4eeb-a7c9-fd7ad46af7fd) en el [referencia del programador de OLE DB](http://msdn.microsoft.com/en-us/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8)*.*  
  
## <a name="applies-to"></a>Se aplica a  
 [Objeto de error](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>Vea también  
 [Descripción, HelpContext, HelpFile, NativeError, número, origen y ejemplo de las propiedades SQLState (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Descripción, HelpContext, HelpFile, NativeError, número, origen y ejemplo de las propiedades SQLState (VC ++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Description (propiedad)](../../../ado/reference/ado-api/description-property.md)   
 [HelpContext, HelpFile propiedades](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Propiedad Source (Error de ADO)](../../../ado/reference/ado-api/source-property-ado-error.md)

