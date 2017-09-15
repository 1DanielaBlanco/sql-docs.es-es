---
title: "Los cursores estáticos | Documentos de Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cursors [ADO], static
- static cursors [ADO]
ms.assetid: cce93ace-c4ed-4c6c-940c-28a50ff2fd12
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fd0ace9aabf10c2b7e5b34d28bd54dbde84cfd0a
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="static-cursors"></a>Cursores estáticos
El cursor estático siempre muestra el conjunto tal como estaba cuando se abre por primera vez el cursor de resultados. Según la implementación, los cursores estáticos pueden ser de solo lectura o de lectura/escritura y proporcionar desplazamiento hacia delante y hacia atrás. El cursor estático normalmente no detecta los cambios realizados a la pertenencia, el orden o los valores del conjunto una vez abierto el cursor de resultados. Los cursores estáticos pueden detectar sus propias actualizaciones, eliminaciones e inserciones, aunque no tengan que lo haga.  
  
 Los cursores estáticos no detectan nunca otras actualizaciones, se elimina y se inserta. Por ejemplo, suponga que un cursor estático recupera una fila y otra aplicación, a continuación, actualiza esa fila. Si la aplicación vuelve a obtener la fila desde el cursor estático, los valores que ve son iguales, a pesar de los cambios realizados por la otra aplicación. Se admiten todos los tipos de desplazamiento, pero los proveedores pueden o no admitir marcadores.  
  
 Si la aplicación no necesita detectar requiere desplazamientos y cambian de datos, el cursor estático es la mejor opción. Utilice la **adOpenStatic CursorTypeEnum** para indicar que desea utilizar un cursor estático en ADO.  
  
## <a name="see-also"></a>Vea también  
 [Cursores de solo avance](../../../ado/guide/data/forward-only-cursors.md)   
 [Cursores KEYSET](../../../ado/guide/data/keyset-cursors.md)   
 [Cursores dinámicos](../../../ado/guide/data/dynamic-cursors.md)
