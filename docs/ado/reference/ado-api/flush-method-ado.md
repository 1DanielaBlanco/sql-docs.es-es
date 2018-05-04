---
title: Flush (método) (ADO) | Documentos de Microsoft
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
- _Stream::Flush
- _Stream::raw_Flush
helpviewer_keywords:
- Flush method [ADO]
ms.assetid: 938522b4-f836-4c80-8d27-a598a000f0ee
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d6fbf389b2cf0d8726dbce5585bce8bff1ca0b4e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="flush-method-ado"></a>Flush (método) (ADO)
Fuerza que el contenido de la [flujo](../../../ado/reference/ado-api/stream-object-ado.md) permanecen en el búfer de ADO en el objeto subyacente con el que el **flujo** está asociado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Stream.Flush  
```  
  
## <a name="remarks"></a>Comentarios  
 Este método puede utilizarse para enviar el contenido del búfer de secuencia al objeto subyacente: por ejemplo, el nodo o archivo representado por la dirección URL que es el origen de la **flujo** objeto. Debe llamar a este método cuando desee asegurarse de que todos los cambios que se realizaron en el contenido de un **flujo** se han escrito. Sin embargo, con ADO normalmente no es necesario llamar a **vaciar**, puesto que ADO vacía continuamente su búfer tanto como sea posible en segundo plano. Cambios en el contenido de un **flujo** se realizan automáticamente y no almacena en caché hasta que **vaciar** se llama.  
  
 Cerrar un **flujo** con el [cerrar](../../../ado/reference/ado-api/close-method-ado.md) método vuelca el contenido de un **flujo** automáticamente; no existe no es necesario llamar explícitamente a **vaciar**inmediatamente antes de **cerrar**.  
  
## <a name="applies-to"></a>Se aplica a  
 [Objeto de secuencia (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
