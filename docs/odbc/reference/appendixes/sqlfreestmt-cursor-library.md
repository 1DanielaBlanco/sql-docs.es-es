---
title: SQLFreeStmt (biblioteca de cursores) | Documentos de Microsoft
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
- SQLFreeStmt function [ODBC], Cursor Library
ms.assetid: 47bfbd4d-9453-4609-958d-1e05794cb223
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2cd1e2eef830ef36887f488dcd6f6c0f4aac0483
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="sqlfreestmt-cursor-library"></a>SQLFreeStmt (biblioteca de cursores)
> [!IMPORTANT]  
>  Esta característica se quitará en una versión futura de Windows. Evite utilizar esta característica en nuevos trabajos de desarrollo y piense en modificar las aplicaciones que actualmente utilizan esta característica. Microsoft recomienda usar la funcionalidad del controlador cursor.  
  
 Este tema describe el uso de la **SQLFreeStmt** función en la biblioteca de cursores. Para obtener información general sobre **SQLFreeStmt**, consulte [SQLFreeStmt, función](../../../odbc/reference/syntax/sqlfreestmt-function.md).  
  
 Si una aplicación llama **SQLFreeStmt** con la opción SQL_UNBIND después de llamar a **SQLExtendedFetch**, **SQLFetch**, o **SQLFetchScroll**, la biblioteca de cursores devuelve un error. Antes de que pueden deshacer el enlace de columnas del conjunto de resultados, una aplicación debe llamar a **SQLCloseCursor** o **SQLFreeStmt** con la opción de SQL_CLOSE.
