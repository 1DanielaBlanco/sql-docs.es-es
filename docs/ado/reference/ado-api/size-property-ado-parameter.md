---
title: "Cambiar el tamaño de propiedad (parámetro de ADO) | Documentos de Microsoft"
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
f1_keywords: _Parameter::Size
helpviewer_keywords: Size property [ADO Parameter]
ms.assetid: e6bad449-ebdb-4dd3-886a-9e6f1e7ee5d2
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d2208300a31c141c2092caae62bc11cfe83606cd
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="size-property-ado-parameter"></a>Propiedad Size (parámetro de ADO)
Indica el tamaño máximo, en bytes o caracteres, de un [parámetro](../../../ado/reference/ado-api/parameter-object.md) objeto.  
  
## <a name="settings-and-return-values"></a>Configuración y valores devueltos  
 Establece o devuelve un **largo** valor que indica el tamaño máximo en bytes o caracteres de un valor en un **parámetro** objeto.  
  
## <a name="remarks"></a>Comentarios  
 Use la **tamaño** propiedad para determinar el tamaño máximo de los valores escritos en o leer desde el [valor](../../../ado/reference/ado-api/value-property-ado.md) propiedad de un **parámetro** objeto.  
  
 Si se especifica un tipo de datos de longitud variable para un **parámetro** objeto (por ejemplo, cualquier **cadena** escriba, por ejemplo, **parámetros**), debe establecer el objeto  **Tamaño** propiedad antes de agregarlo a la [parámetros](../../../ado/reference/ado-api/parameters-collection-ado.md) colección; en caso contrario, se produce un error.  
  
 Si ya se ha anexado el **parámetro** el objeto a la **parámetros** colección de un [comando](../../../ado/reference/ado-api/command-object-ado.md) objeto y cambiar el tipo a un tipo de datos de longitud variable, debe establecer el **parámetro** del objeto **tamaño** propiedad antes de ejecutar el **comando** objeto; en caso contrario, se produce un error.  
  
 Si usas el [actualizar](../../../ado/reference/ado-api/refresh-method-ado.md) método para obtener información sobre los parámetros desde el proveedor y devuelve uno o más tipos de datos de longitud variable **parámetro** objetos, ADO puede asignar memoria para los parámetros de acuerdo en su tamaño máximo potencial, lo que puede provocar un error durante la ejecución. Para evitar un error, debe establecer explícitamente la **tamaño** propiedad para estos parámetros antes de ejecutar el comando.  
  
 El **tamaño** propiedad es de lectura/escritura.  
  
## <a name="applies-to"></a>Se aplica a  
 [Objeto Parameter](../../../ado/reference/ado-api/parameter-object.md)  
  
## <a name="see-also"></a>Vea también  
 [ActiveConnection, CommandText, CommandTimeout, CommandType, tamaño y ejemplo de propiedades de dirección (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, tamaño y ejemplo de propiedades de dirección (VC ++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, tamaño y ejemplo de propiedades de dirección (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)   
 [Propiedad Size (Stream de ADO)](../../../ado/reference/ado-api/size-property-ado-stream.md)
