---
title: Admite los tipos de datos (controlador ODBC para Oracle) | Documentos de Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data types [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], data types
ms.assetid: 21d5f8d9-a3aa-4aa4-bc37-ff8bc90c0870
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7ea00ac6b2e95b2bd21453312a42ef2769b20d9c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2017
---
# <a name="supported-data-types-odbc-driver-for-oracle"></a>Tipos de datos admitidos (controlador ODBC para Oracle)
> [!IMPORTANT]  
>  Esta característica se quitará en una versión futura de Windows. Evite utilizar esta característica en nuevos trabajos de desarrollo y tenga previsto modificar las aplicaciones que actualmente la utilizan. En su lugar, utilice el controlador ODBC proporcionado por Oracle.  
  
 El controlador ODBC para Oracle admite todos los tipos de datos de Oracle 7.3; Sin embargo, no admite cualquiera de los nuevos tipos de datos de Oracle8 enumerados aquí.  
  
|Tipo de datos|Oracle 7.3|Oracle8|  
|---------------|----------------|-------------|  
|BFILE|n/d|No compatible|  
|BLOB|n/d|No compatible|  
|CHAR|Admitida|Admitida|  
|CLOB|n/d|No compatible|  
|DATE|Admitida|Admitida|  
|FLOAT|Admitida|Admitida|  
|INTEGER|Admitida|Admitida|  
|LONG|Admitida|Admitida|  
|LONG RAW|Admitida|Admitida|  
|NCHAR|n/d|No compatible|  
|NCLOB|n/d|No compatible|  
|NUMBER|Admitida|Admitida|  
|NVARCHAR2|n/d|No compatible|  
|RAW|Admitida|Admitida|  
|VARCHAR2|Admitida|Admitida|  
|MLSLABEL|No compatible.|No compatible.|  
  
> [!NOTE]  
>  Para obtener más información sobre el tamaño permitido de la columna VARCHAR, consulte [tamaño de la columna VARCHAR](../../odbc/microsoft/varchar-column-size-odbc-driver-for-oracle.md) en esta guía.
