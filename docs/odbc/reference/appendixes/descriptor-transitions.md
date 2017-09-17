---
title: Transiciones de descriptor | Documentos de Microsoft
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
- state transitions [ODBC], descriptor
- transitioning states [ODBC], descriptor
- descriptor transitions [ODBC]
ms.assetid: 0cf24fe6-5e3c-45fa-81b8-4f52ddf8501d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 280d35d8ce03d3d7685441c12d99c05c9ff5f451
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="descriptor-transitions"></a>Transiciones de descriptor
Descriptores ODBC tienen los tres estados siguientes.  
  
|State|Description|  
|-----------|-----------------|  
|D0|Descriptor sin asignar|  
|D1i|Descriptor asignado implícitamente|  
|D1e|Descriptor asignado explícitamente|  
  
 Las tablas siguientes muestran cómo cada función ODBC afecta al estado de descriptor.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|D0<br /><br /> Sin asignar|D1i<br /><br /> Implícito|D1e<br /><br /> Explícito|  
|------------------------|----------------------|----------------------|  
|D1i [1]|--|--|  
|D1e [2]|--|--|  
  
 [1] esta fila muestra las transiciones cuando *HandleType* era SQL_HANDLE_STMT.  
  
 [2] esta fila muestra las transiciones cuando *HandleType* era SQL_HANDLE_DESC.  
  
## <a name="sqlcopydesc"></a>SQLCopyDesc  
  
|D0<br /><br /> Sin asignar|D1i<br /><br /> Implícito|D1e<br /><br /> Explícito|  
|------------------------|----------------------|----------------------|  
|(IH)|--|--|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|D0<br /><br /> Sin asignar|D1i<br /><br /> Implícito|D1e<br /><br /> Explícito|  
|------------------------|----------------------|----------------------|  
|--[1]|D0|--|  
|(IH) [2]|(HY017)|D0|  
  
 [1] esta fila muestra las transiciones cuando *HandleType* era SQL_HANDLE_STMT.  
  
 [2] esta fila muestra las transiciones cuando *HandleType* era SQL_HANDLE_DESC.  
  
## <a name="sqlgetdescfield-and-sqlgetdescrec"></a>SQLGetDescField y SQLGetDescRec  
  
|D0<br /><br /> Sin asignar|D1i<br /><br /> Implícito|D1e<br /><br /> Explícito|  
|------------------------|----------------------|----------------------|  
|(IH)|--|--|  
  
## <a name="sqlsetdescfield-and-sqlsetdescrec"></a>SQLSetDescField y SQLSetDescRec  
  
|D0<br /><br /> Sin asignar|D1i<br /><br /> Implícito|D1e<br /><br /> Explícito|  
|------------------------|----------------------|----------------------|  
|(IH) [1]|--|--|  
  
 [1] esta fila muestra las transiciones cuando *DescriptorHandle* era el identificador de un descartar, APD o IPD, o (para **SQLSetDescField**) cuando *DescriptorHandle* era el identificador de un IRD y *FieldIdentifier* era SQL_DESC_ARRAY_STATUS_PTR o SQL_DESC_ROWS_PROCESSED_PTR.  
  
## <a name="all-other-odbc-functions"></a>Todas las demás funciones ODBC  
  
|D0<br /><br /> Sin asignar|D1i<br /><br /> Implícito|D1e<br /><br /> Explícito|  
|------------------------|----------------------|----------------------|  
|--|--|--|
