---
title: Ver (objeto) (ADOX) | Documentos de Microsoft
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
f1_keywords: View
helpviewer_keywords: View object [ADOX]
ms.assetid: 653421ce-7b94-43d0-9bc6-4900f8f2af45
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 74f53494e11f46432b57b07ad0d9f42d6c3773f6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="view-object-adox"></a>Objeto de vista (ADOX)
Representa un conjunto filtrado de registros o una tabla virtual. Cuando se utiliza junto con la propiedad ADO [comando](../../../ado/reference/ado-api/command-object-ado.md) objeto, el **vista** objeto se puede usar para agregar, eliminar o modificar vistas.  
  
## <a name="remarks"></a>Comentarios  
 Una vista es una tabla virtual, creada a partir de otras tablas de base de datos o vistas. El **vista** objeto le permite crear una vista sin tener que conocer ni utilizar la sintaxis del proveedor "CREATE VIEW".  
  
 Con las propiedades de un **vista** de objeto, puede:  
  
-   Identificar la vista con la [nombre](../../../ado/reference/adox-api/name-property-adox.md) propiedad.  
  
-   Especifique la propiedad ADO **comando** objeto que puede usar para agregar, eliminar o modificar vistas con la [comando](../../../ado/reference/adox-api/command-property-adox.md) propiedad.  
  
-   Devolver información de fecha con el [DateCreated](../../../ado/reference/adox-api/datecreated-property-adox.md) y [DateModified](../../../ado/reference/adox-api/datemodified-property-adox.md) propiedades.  
  
 Esta sección contiene el siguiente tema.  
  
-   [Propiedades, métodos y eventos del objeto View](../../../ado/reference/adox-api/view-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vea también  
 [Vistas y ejemplo de colecciones de campos (VB)](../../../ado/reference/adox-api/views-and-fields-collections-example-vb.md)   
 [Vistas de ejemplo de método Append (VB)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Colección de vistas, ejemplo de la propiedad CommandText (VB)](../../../ado/reference/adox-api/views-collection-commandtext-property-example-vb.md)   
 [Vistas de eliminar el ejemplo del método (VB)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)   
 [Colección de vistas (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)
