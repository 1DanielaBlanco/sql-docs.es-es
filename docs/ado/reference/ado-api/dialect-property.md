---
title: Propiedad Dialect | Documentos de Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Command::Dialect
helpviewer_keywords:
- Dialect property
ms.assetid: 329c3a71-ba88-4009-b04f-2f52195a5957
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 74299cc953c3ac94653860d18d0ee7774ecf49ad
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="dialect-property"></a>Propiedad Dialect
Indica el dialecto de la [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) o [CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md) propiedades. El dialecto define la sintaxis y reglas generales que el proveedor utiliza para analizar la cadena o secuencia.  
  
## <a name="settings-and-return-values"></a>Configuración y valores devueltos  
 El **dialecto** propiedad contiene un GUID válido que representa el dialecto del texto de comando o secuencia. El valor predeterminado de esta propiedad es {C8B521FB-5CF3-11CE-ADE5-00AA0044773D}, lo que indica que el proveedor debe decidir cómo interpretar el texto del comando o la secuencia.  
  
## <a name="remarks"></a>Comentarios  
 ADO no consultar el proveedor cuando el usuario lee el valor de esta propiedad; Devuelve una representación de cadena del valor almacenado actualmente en el [comando](../../../ado/reference/ado-api/command-object-ado.md) objeto.  
  
 Cuando el usuario establece el **dialecto** valida el GUID de propiedad, ADO y genera un error si el valor proporcionado no es un GUID válido. Consulte la documentación de su proveedor para determinar los valores GUID admitidos por el **dialecto** propiedad.  
  
## <a name="applies-to"></a>Se aplica a  
 [Objeto Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Vea también  
 [Método Execute (Command ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md)
