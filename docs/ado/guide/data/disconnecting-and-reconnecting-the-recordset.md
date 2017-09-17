---
title: Desconectar y volver a conectar el conjunto de registros | Documentos de Microsoft
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
- Recordset object [ADO], disconnecting and reconnecting
ms.assetid: c5134af7-81d6-4de4-9fd1-cfe29973545e
caps.latest.revision: 4
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a6ddbc392ae0bd0c378a4d08cd2c76f3119d8332
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="disconnecting-and-reconnecting-the-recordset"></a>Desconectar y volver a conectar el conjunto de registros
Una de las características más eficaces de ADO es la capacidad de abrir un conjunto de registros de cliente desde un origen de datos y, a continuación, desconecte el conjunto de registros desde el origen de datos. Una vez que se ha desconectado el conjunto de registros, se puede cerrar la conexión al origen de datos, con lo que se liberan los recursos en el servidor utilizado para mantenerlo. Puede continuar ver y editar los datos en el conjunto de registros mientras está desconectada y vuelve a conectarse al origen de datos y enviar las actualizaciones en modo por lotes.  
  
 Para desconectar un conjunto de registros, ábralo con una ubicación de cursor de adUseClient y, a continuación, establezca la propiedad ActiveConnection en Nothing. (Los usuarios de C++ deben establecer que el objeto ActiveConnection igual en NULL para desconectar).  
  
 Se utilizará un conjunto de registros desconectado más adelante en esta sección cuando se hable de la persistencia de conjunto de registros para afrontar un escenario en el que es necesario disponer de los datos en un conjunto de registros disponible para una aplicación mientras el equipo cliente no está conectado a una red.  
  
## <a name="see-also"></a>Vea también  
 [Modo por lotes](../../../ado/guide/data/batch-mode.md)
