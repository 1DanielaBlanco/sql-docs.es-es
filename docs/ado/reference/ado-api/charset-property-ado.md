---
title: Propiedad de conjunto de caracteres (ADO) | Documentos de Microsoft
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
- _Stream::Charset
helpviewer_keywords:
- Charset property [ADO]
ms.assetid: e42507cb-9b46-4ce4-8191-2948eaf14ca2
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8c3f9568a04572718bb6b1a968a3bacae4520898
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="charset-property-ado"></a>Propiedad de conjunto de caracteres (ADO)
Indica el juego de caracteres al que el contenido de un texto [flujo](../../../ado/reference/ado-api/stream-object-ado.md) deben traducir para el almacenamiento en el búfer interno de la **flujo** objeto.  
  
## <a name="settings-and-return-values"></a>Configuración y valores devueltos  
 Establece o devuelve un **cadena** establece el valor que especifica el carácter en el que el contenido de la **flujo** se va a traducir. El valor predeterminado es **Unicode**. Los valores permitidos son cadenas típicas que se pasan a través de la interfaz como nombres de conjunto de caracteres de Internet (por ejemplo, "iso-8859-1", "Windows-1252" y así sucesivamente). Para obtener una lista de los nombres de conjunto de caracteres que se conocen por un sistema, vea las subclaves de HKEY_CLASSES_ROOT\MIME\Database\Charset en el registro de Windows.  
  
## <a name="remarks"></a>Comentarios  
 En el texto **flujo** de objetos, datos de texto se almacenan en el juego de caracteres especificado por el **Charset** propiedad. El valor predeterminado es Unicode. El **Charset** propiedad se utiliza para convertir datos en el **flujo** o próximos fuera de la **flujo**. Por ejemplo, si la **flujo** contiene datos ISO-8859-1 y que los datos se copian en una cadena BSTR, el **flujo** objeto convertirá los datos a Unicode. Lo contrario también es cierto.  
  
 Un circuito abierto **flujo**, actual [posición](../../../ado/reference/ado-api/position-property-ado.md) debe estar al principio de la **flujo** (0) para poder establecer **Charset**.  
  
 **Juego de caracteres** sólo se utiliza con texto **flujo** objetos ([tipo](../../../ado/reference/ado-api/type-property-ado-stream.md) es **adTypeText**). Esta propiedad se omite si **tipo** es **adTypeBinary**.  
  
 Para obtener un ejemplo de código, vea [paso 4: rellenar el cuadro de texto detalles](../../../ado/guide/data/step-4-populate-the-details-text-box.md).  
  
## <a name="applies-to"></a>Se aplica a  
 [Objeto de secuencia (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)

