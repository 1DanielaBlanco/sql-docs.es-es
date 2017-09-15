---
title: "Modo de confirmación manual | Documentos de Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rolling back transactions [ODBC]
- manual-commit mode [ODBC]
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
- transactions [ODBC], rolling back
ms.assetid: 9c4b3931-e48b-4960-89a2-5697537e9f51
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1a5f9d510d1a92ce8faf4fe29f3274afdba6f83b
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="manual-commit-mode"></a>Modo de confirmación manual
*En el modo de confirmación manual,* aplicaciones explícitamente deben completar las transacciones mediante una llamada a **SQLEndTran** confirmarlas o revertirlas. Éste es el modo de transacción normal para la mayoría de bases de datos relacionales.  
  
 Las transacciones en ODBC no es necesario que se inicie de forma explícita. En su lugar, una transacción se inicia implícitamente siempre que inicia la aplicación en funcionamiento en la base de datos. Si el origen de datos requiere inicio de transacciones explícitas, el controlador debe proporcionar cada vez que la aplicación ejecuta una instrucción que requiere una transacción y no hay ninguna transacción actual.
