---
title: Colecciones (ADO para la sintaxis Visual C++) | Documentos de Microsoft
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
dev_langs:
- C++
helpviewer_keywords:
- ADO for Visual C++ syntax [ADO]
- syntax indexes [ADO], ADO for Visual C++ syntax
- collections [ADO], ADO for Visual C++ syntax
ms.assetid: 6a0109a0-f2d9-4f7c-8e1e-42763f9acaea
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: da75220f32fcd90d0785d802b5281cb5016da063
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="collections-ado-for-visual-c-syntax"></a>Colecciones (ADO para la sintaxis Visual C++)
## <a name="parameters"></a>Parámetros  
  
### <a name="methods"></a>Métodos  
  
```  
Append(IDispatch *Object);  
Delete(VARIANT Index);  
Refresh(void);  
```  
  
 Para obtener más información, vea  
  
-   [Append (método) (ADO)](../../../ado/reference/ado-api/append-method-ado.md)  
  
-   [Método Delete (colección de parámetros de ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)  
  
-   [Actualizar (método, ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)  
  
### <a name="properties"></a>Propiedades  
  
```  
get_Count(long *c);  
get_Item(VARIANT Index, _ADOParameter **ppvObject);  
```  
  
 Para obtener más información, vea  
  
-   [Count (propiedad, ADO)](../../../ado/reference/ado-api/count-property-ado.md)  
  
-   [Propiedad Item (ADO)](../../../ado/reference/ado-api/item-property-ado.md)  
  
## <a name="fields"></a>Campos  
  
### <a name="methods"></a>Métodos  
  
```  
Append(BSTR bstrName, DataTypeEnum Type, long DefinedSize, FieldAttributeEnum Attrib);  
Delete(VARIANT Index);  
Refresh(void);  
```  
  
 Para obtener más información, vea  
  
-   [Append (método) (ADO)](../../../ado/reference/ado-api/append-method-ado.md)  
  
-   [Método Delete (colección de parámetros de ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)  
  
-   [Actualizar (método, ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)  
  
### <a name="properties"></a>Propiedades  
  
```  
get_Count(long *c);  
get_Item(VARIANT Index, ADOField **ppvObject);  
```  
  
 Para obtener más información, vea  
  
-   [Count (propiedad, ADO)](../../../ado/reference/ado-api/count-property-ado.md)  
  
-   [Propiedad Item (ADO)](../../../ado/reference/ado-api/item-property-ado.md)  
  
## <a name="errors"></a>Errores  
  
### <a name="methods"></a>Métodos  
  
```  
Clear(void);  
Refresh(void);  
```  
  
 Para obtener más información, vea  
  
-   [Clear (método) (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)  
  
-   [Actualizar (método, ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)  
  
### <a name="properties"></a>Propiedades  
  
```  
get_Count(long *c);  
get_Item(VARIANT Index, ADOError **ppvObject);  
```  
  
 Para obtener más información, vea  
  
-   [Count (propiedad, ADO)](../../../ado/reference/ado-api/count-property-ado.md)  
  
-   [Propiedad Item (ADO)](../../../ado/reference/ado-api/item-property-ado.md)  
  
## <a name="properties"></a>Propiedades  
  
### <a name="methods"></a>Métodos  
  
```  
Refresh(void);  
```  
  
 Para obtener más información, vea  
  
-   [Actualizar (método, ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)  
  
### <a name="properties"></a>Propiedades  
  
```  
get_Count(long *c);  
get_Item(VARIANT Index, ADOProperty **ppvObject);  
```  
  
 Para obtener más información, vea  
  
-   [Count (propiedad, ADO)](../../../ado/reference/ado-api/count-property-ado.md)  
  
-   [Propiedad Item (ADO)](../../../ado/reference/ado-api/item-property-ado.md)  
  
## <a name="see-also"></a>Vea también  
 [Colección de errores (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)   
 [Fields (colección) (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Colección de parámetros (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Colección de propiedades (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
