---
title: "Open (método) (ADO MD) | Documentos de Microsoft"
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
- Open
- Cellset::Open
helpviewer_keywords:
- Open method [ADO MD]
ms.assetid: a87d8080-a238-45e5-bc80-9a8625b3810f
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 35faf0a1217f5b558c9781644cb9ea115e602584
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="open-method-ado-md"></a>Open (método) (ADO MD)
Recupera los resultados de una consulta multidimensional y devuelve los resultados a un [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Cellset.Open Source, ActiveConnection  
```  
  
#### <a name="parameters"></a>Parámetros  
 *Source*  
 Opcional. A **Variant** que da como resultado una consulta multidimensional válida, por ejemplo, una consulta de expresiones multidimensionales (MDX). El *origen* argumento corresponde a la [origen](../../../ado/reference/ado-md-api/source-property-ado-md.md) propiedad. Para obtener más información acerca de MDX, vea la [OLE DB para OLAP Online Analytical Processing ()](http://msdn.microsoft.com/en-us/8a7673c6-3ca1-4411-9f1e-adf1e47df4f3) documentación en el SDK de Microsoft Data Access Components.  
  
 *ActiveConnection*  
 Opcional. A **Variant** que se evalúa como una cadena que especifica un ADO válido [conexión](../../../ado/reference/ado-api/connection-object-ado.md) objeto nombre de variable o una definición para una conexión. El *ActiveConnection* argumento especifica la conexión en la que se va a abrir el [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) objeto. Si se pasa una definición de conexión para este argumento, ADO abre una nueva conexión mediante los parámetros especificados. El *ActiveConnection* argumento corresponde a la [ActiveConnection](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md) propiedad.  
  
## <a name="remarks"></a>Comentarios  
 El **abrir** método genera un error si se omite cualquiera de sus parámetros y no se estableció el valor de propiedad correspondiente antes de volver a abrir la **Cellset**.  
  
## <a name="applies-to"></a>Se aplica a  
 [Objeto de conjunto de celdas (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de conjunto de celdas (VB)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [ActiveConnection (propiedad, ADO MD)](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md)   
 [Close (método) (ADO MD)](../../../ado/reference/ado-md-api/close-method-ado-md.md)   
 [Objeto de conexión (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Propiedad de origen (ADO MD)](../../../ado/reference/ado-md-api/source-property-ado-md.md)   
 [State (propiedad) (ADO MD)](../../../ado/reference/ado-md-api/state-property-ado-md.md)

