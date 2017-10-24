---
title: Objeto Column (ADOX) | Documentos de Microsoft
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
- Column
helpviewer_keywords:
- Column object [ADOX]
ms.assetid: 6e772783-1bc8-4ea7-94b2-7d7a52ea5c47
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a5a8a5047f4cd4655ebe1dd041e44949ca361c54
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="column-object-adox"></a>Objeto Column (ADOX)
Representa una columna de una tabla, índice o clave.  
  
## <a name="remarks"></a>Comentarios  
 El siguiente código crea un nuevo **columna**:  
  
 `Dim obj As New Column`  
  
 Con las propiedades y colecciones de una **columna** objeto, puede:  
  
-   Identificar la columna con el [nombre de propiedad (ADOX)](../../../ado/reference/adox-api/name-property-adox.md) propiedad.  
  
-   Especificar el tipo de datos de la columna con el [(clave) (ADOX) del tipo de propiedad](../../../ado/reference/adox-api/type-property-key-adox.md) propiedad.  
  
-   Determinar si la columna tiene una longitud fija o si puede contener valores null con el [propiedad atributos (ADOX)](../../../ado/reference/adox-api/attributes-property-adox.md) propiedad.  
  
-   Especifique el tamaño máximo de la columna con el [propiedad DefinedSize (ADOX)](../../../ado/reference/adox-api/definedsize-property-adox.md) propiedad.  
  
-   Para los valores de datos numéricos, especificar la escala con el [propiedad NumericScale (ADOX)](../../../ado/reference/adox-api/numericscale-property-adox.md) propiedad.  
  
-   Para los valores de datos numéricos, especificar la precisión máxima con la [propiedad precisión (ADOX)](../../../ado/reference/adox-api/precision-property-adox.md) propiedad.  
  
-   Especifique el [objeto de catálogo (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md) que posee la columna con el [propiedad ParentCatalog (ADOX)](../../../ado/reference/adox-api/parentcatalog-property-adox.md) propiedad.  
  
-   Para columnas de clave, especifique el nombre de la columna relacionada en la tabla relacionada con la [propiedad RelatedColumn (ADOX)](../../../ado/reference/adox-api/relatedcolumn-property-adox.md) propiedad.  
  
-   Para las columnas de índice, especificar si el criterio de ordenación es ascendente o descendente con la [propiedad SortOrder (ADOX)](../../../ado/reference/adox-api/sortorder-property-adox.md) propiedad.  
  
-   Obtener acceso a propiedades específicas del proveedor con el [colección de propiedades (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) colección.  
  
> [!NOTE]
>  No todas las propiedades de **columna** objetos pueden admitir el proveedor de datos. Si ha configurado un valor para una propiedad que no es compatible con el proveedor, se producirá un error. Para obtener nuevos **columna** objetos, se producirá el error cuando el objeto se anexa a la colección. Para los objetos existentes, se producirá el error al establecer la propiedad.  
>   
>  Al crear **columna** objetos, la existencia de un valor predeterminado adecuado para una propiedad opcional no garantiza que el proveedor admita la propiedad. Para obtener más información acerca de las propiedades que admite el proveedor, consulte la documentación del proveedor.  
  
 Esta sección contiene el siguiente tema.  
  
-   [Eventos, métodos y propiedades del objeto de columna](../../../ado/reference/adox-api/column-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vea también  
 [Las tablas y columnas anexar métodos, ejemplo de la propiedad de nombre (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Método de cierre de conexión, ejemplo de propiedad de tipo de tabla (VB)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Anexar de teclas de método, tipo de clave, RelatedColumn, RelatedTable y ejemplo de las propiedades UpdateRule (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Ejemplo de código ADOX: NumericScale y ejemplo de las propiedades Precision (VB)](../../../ado/reference/adox-api/adox-code-example-numericscale-and-precision-properties-example-vb.md)   
 [Ejemplo de propiedad ParentCatalog (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Ejemplo de propiedad SortOrder (VB)](../../../ado/reference/adox-api/sortorder-property-example-vb.md)   
 [Colección de columnas (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Colección de propiedades (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)

