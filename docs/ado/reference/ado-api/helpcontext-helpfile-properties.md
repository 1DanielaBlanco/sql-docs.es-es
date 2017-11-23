---
title: HelpContext, HelpFile propiedades | Documentos de Microsoft
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
- Error::GetHelpContext
- Error::GetHelpFile
- Error::get_HelpFile
- Error::get_HelpContext
- Error::HelpContext
- Error::HelpFile
helpviewer_keywords:
- HelpContext property [ADO]
- HelpFile property [ADO]
ms.assetid: 2b9ef441-993c-44d4-8f87-fac0979dac1d
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dce4f5513199be2b4c74903741178844c0ecedf6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="helpcontext-helpfile-properties"></a>HelpContext, HelpFile propiedades
Indica el archivo de ayuda y el tema asociados con un [Error](../../../ado/reference/ado-api/error-object.md) objeto.  
  
## <a name="return-values"></a>Valores devueltos  
  
-   **HelpContextID** devuelve un identificador de contexto, como un **largo** valor para un tema en un archivo de ayuda.  
  
-   **HelpFile** devuelve un **cadena** valor que se evalúa como una ruta de acceso totalmente resuelta a un archivo de ayuda.  
  
## <a name="remarks"></a>Comentarios  
 Si se especifica un archivo de ayuda en la **HelpFile** propiedad, el **HelpContext** propiedad se utiliza para mostrar automáticamente el tema de ayuda que identifica. Si no hay ningún tema de ayuda relevante disponible, la **HelpContext** propiedad devuelve cero y la **HelpFile** propiedad devuelve una cadena de longitud cero ("").  
  
## <a name="applies-to"></a>Se aplica a  
 [Objeto de error](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>Vea también  
 [Descripción, HelpContext, HelpFile, NativeError, número, origen y ejemplo de las propiedades SQLState (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Descripción, HelpContext, HelpFile, NativeError, número, origen y ejemplo de las propiedades SQLState (VC ++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Description (propiedad)](../../../ado/reference/ado-api/description-property.md)   
 [Propiedad Number (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [Propiedad Source (Error de ADO)](../../../ado/reference/ado-api/source-property-ado-error.md)
