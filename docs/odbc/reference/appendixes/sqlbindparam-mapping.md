---
title: Asignación de SQLBindParam | Documentos de Microsoft
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
ms.topic: article
helpviewer_keywords:
- SQLBindparam function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLBindParam
ms.assetid: 375f8f24-36de-4946-916e-c75abc6f070d
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1a2c78cd97b6577be8d11d07325165d6d82cd895
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="sqlbindparam-mapping"></a>Asignación de SQLBindParam
**SQLBindParam** no se puede llamar realmente en desuso porque no estaba presente en ODBC; sin embargo, todavía representa funcionalidad duplicada, debe exportarlo ya ISO y abra compatible con grupo de aplicaciones se va a usar el Administrador de controladores. Dado que **SQLBindParameter** contiene toda la funcionalidad de **SQLBindParam**, **SQLBindParam** va a asignar sobre **SQLBindParameter** (cuando el controlador subyacente es una aplicación ODBC 3*.x* controlador). Una aplicación ODBC 3*.x* controlador no es necesario implementar **SQLBindParam**.  
  
## <a name="remarks"></a>Comentarios  
 Cuando la siguiente llamada a **SQLBindParam** se realiza:  
  
```  
SQLBindParam(   StatementHandle,    ParameterNumber,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    StrLen_or_IndPtr)  
```  
  
 las llamadas del Administrador de controladores **SQLBindParameter** en el controlador de la manera siguiente:  
  
```  
SQLBindParameter(   StatementHandle,    ParameterNumber,    SQL_PARAM_INPUT,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    BufferLength,    StrLen_or_IndPtr)  
```  
  
 Vea [información ODBC de 64 bits](../../../odbc/reference/odbc-64-bit-information.md), si la aplicación se ejecutará en un sistema operativo de 64 bits.  
  
## <a name="see-also"></a>Vea también  
 [Asignación de funciones en desuso](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)
