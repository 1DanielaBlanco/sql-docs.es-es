---
title: Cursores estáticos ODBC | Documentos de Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], static
- static cursors [ODBC]
ms.assetid: 28cb324c-e1c3-4b5c-bc3e-54df87037317
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4c2e6835d818d1e1d5aba7b54497f4a95f0bc150
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="odbc-static-cursors"></a>Cursores estáticos ODBC
Un cursor estático es uno en la que el conjunto de resultados aparece como estático. Normalmente no detectar los cambios realizados a la pertenencia, el orden o los valores del conjunto una vez abierto el cursor de resultados. Por ejemplo, suponga que un cursor estático recupera una fila y otra aplicación, a continuación, actualiza esa fila. Si el cursor estático vuelve a obtener la fila, los valores que ve son iguales, a pesar de los cambios realizados por la otra aplicación.  
  
 Los cursores estáticos pueden detectar sus propias actualizaciones, eliminaciones e inserciones, aunque no tengan que hacer esto. Si un cursor estático determinado detecta estos cambios se notifica a través de la opción SQL_STATIC_SENSITIVITY en **SQLGetInfo**. Los cursores estáticos no detectan nunca otras actualizaciones, se elimina y se inserta.  
  
 La matriz de Estados de fila especificada por el atributo de instrucción de SQL_ATTR_ROW_STATUS_PTR puede contener SQL_ROW_SUCCESS, SQL_ROW_SUCCESS_WITH_INFO o SQL_ROW_ERROR para ninguna fila. Devuelve SQL_ROW_UPDATED, SQL_ROW_DELETED o SQL_ROW_ADDED para filas actualiza, elimina o inserta el cursor, suponiendo que el cursor puede detectar dichos cambios.  
  
 Los cursores estáticos normalmente se implementa bloqueando las filas del conjunto de resultados o mediante la realización de una copia o instantánea, de lo establecidos. Aunque el bloqueo de filas es relativamente fácil de hacer, tiene el inconveniente de reducir significativamente la simultaneidad. Realizar una copia permite mayor simultaneidad y permite que el cursor realizar un seguimiento de sus propias actualizaciones, eliminaciones y se inserta mediante la modificación de la copia. Sin embargo, es más costosa de una copia realizar y puede difieran de los datos subyacentes a medida que los datos se cambian por otros usuarios.
