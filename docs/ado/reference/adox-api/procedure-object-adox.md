---
title: Objeto de procedimiento (ADOX) | Documentos de Microsoft
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
- Procedure
helpviewer_keywords:
- Procedure object [ADOX]
ms.assetid: 927bcf3e-32f5-4a80-98d3-600779f0732e
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 50fa6ab8e1481bd80413ba32a77a9c865ae0d8fb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="procedure-object-adox"></a>Objeto de procedimiento (ADOX)
Representa un procedimiento almacenado. Cuando se utiliza junto con la propiedad ADO [comando](../../../ado/reference/ado-api/command-object-ado.md) objeto, el **procedimiento** objeto se puede usar para agregar, eliminar o modificar procedimientos almacenados.  
  
## <a name="remarks"></a>Comentarios  
 El **procedimiento** objeto le permite crear un procedimiento almacenado sin necesidad de conocer ni utilizar la sintaxis del proveedor "CREATE PROCEDURE".  
  
 Con las propiedades de un **procedimiento** de objeto, puede:  
  
-   Identificar el procedimiento con el [nombre](../../../ado/reference/adox-api/name-property-adox.md) propiedad.  
  
-   Especifique la propiedad ADO **comando** objeto que puede utilizarse para crear o ejecutar el procedimiento con el [comando](../../../ado/reference/adox-api/command-property-adox.md) propiedad.  
  
-   Devolver información de fecha con el [DateCreated](../../../ado/reference/adox-api/datecreated-property-adox.md) y [DateModified](../../../ado/reference/adox-api/datemodified-property-adox.md) propiedades.  
  
 Esta sección contiene el siguiente tema.  
  
-   [Propiedades, métodos y eventos del objeto Procedure](../../../ado/reference/adox-api/procedure-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vea también  
 [Comando y ejemplo de las propiedades CommandText (VB)](../../../ado/reference/adox-api/command-and-commandtext-properties-example-vb.md)   
 [Colección de parámetros, ejemplo de la propiedad de comando (VB)](../../../ado/reference/adox-api/parameters-collection-command-property-example-vb.md)   
 [Procedimientos de ejemplo de método Append (VB)](../../../ado/reference/adox-api/procedures-append-method-example-vb.md)   
 [Eliminar de procedimientos de ejemplo del método (VB)](../../../ado/reference/adox-api/procedures-delete-method-example-vb.md)   
 [Colección de procedimientos (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)
