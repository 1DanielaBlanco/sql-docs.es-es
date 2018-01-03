---
title: Compatibilidad con versiones anteriores de los tipos de datos de C | Documentos de Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backward compatibility [ODBC], C data types
- compatibility [ODBC], C data types
- data types [ODBC], backward compatibility
- C data types [ODBC], backward compatibility
ms.assetid: b1453a65-ae03-4061-b0cf-a8434d8bc40b
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2c7c999230837dcb78a294ab2f1b462c6932ab3a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="backward-compatibility-of-c-data-types"></a>Compatibilidad con versiones anteriores de los tipos de datos de C
SQL_C_SHORT, SQL_C_LONG y SQL_C_TINYINT se reemplazaron en ODBC por tipos signed y unsigned: SQL_C_SSHORT y SQL_C_USHORT, SQL_C_SLONG y SQL_C_ULONG y SQL_C_STINYINT y SQL_C_UTINYINT. Una aplicación ODBC 3*.x* controlador que debe trabajar con ODBC 2. *x* las aplicaciones deben admitir SQL_C_SHORT, SQL_C_LONG y SQL_C_TINYINT, porque cuando se les llama, el Administrador de controladores pasa a través del controlador.
