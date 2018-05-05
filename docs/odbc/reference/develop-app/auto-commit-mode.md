---
title: Modo de confirmación automática | Documentos de Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- rolling back transactions [ODBC]
- auto-commit mode [ODBC]
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
- transactions [ODBC], rolling back
ms.assetid: c8de5b60-d147-492d-b601-2eeae8511d00
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 679bbb3486c947ef3ebbd7d285f74f3cb510172f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="auto-commit-mode"></a>Modo de confirmación automática
*En el modo de confirmación automática,* cada operación de base de datos es una transacción que se confirma cuando se realiza. Este modo es adecuado para muchas transacciones reales que se componen de una sola instrucción SQL. No es necesario delimitar o especificar la realización de estas transacciones. En las bases de datos sin compatibilidad con transacciones, modo de confirmación automática es el único modo compatible. En esas bases de datos, las instrucciones se confirman cuando se ejecutan y no hay ninguna manera de revertirlas; por lo tanto, están siempre en modo de confirmación automática.  
  
 Si el DBMS subyacente no admite transacciones de modo de confirmación automática, el controlador puede emular al confirmar manualmente cada instrucción SQL que se ejecuta.  
  
 Si un lote de instrucciones SQL se ejecuta en modo de confirmación automática, es específico del origen de datos cuando las instrucciones del lote se confirman. Pueden ser confirmadas cuando se ejecutan o como un todo después de que se ha ejecutado todo el lote. Algunos orígenes de datos pueden admitir estos comportamientos y pueden proporcionar una manera de seleccionar uno o los demás. En concreto, si se produce un error en el medio del lote, es específico del origen de datos si las instrucciones de ejecución ya se haya confirmado o revertidas. Por lo tanto, las aplicaciones interoperables que usan los lotes y requieren que se haya confirmado o revertido como un todo deben ejecutar lotes solo en modo de confirmación manual.
