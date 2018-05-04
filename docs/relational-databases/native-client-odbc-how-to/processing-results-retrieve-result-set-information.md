---
title: Recuperar información del conjunto de resultados (ODBC) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-how-to
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC]
- result sets [ODBC], fetching
ms.assetid: 34f235e4-f80b-4123-8764-9deb18506f14
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: ef54e7c82473159a79c9e2dc25b63940b4dc2a6f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="processing-results---retrieve-result-set-information"></a>Procesar resultados - recuperar información del conjunto de resultados
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

    
### <a name="to-get-information-about-a-result-set"></a>Para obtener información sobre un conjunto de resultados  
  
1.  Llame a [SQLNumResultCols](../../relational-databases/native-client-odbc-api/sqlnumresultcols.md) para obtener el número de columnas del conjunto de resultados.  
  
2.  Para cada columna del conjunto de resultados:  
  
    -   Llame a [SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md) para obtener información acerca de la columna de resultados.  
  
     O bien  
  
    -   Llame a [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md) para obtener información específica del descriptor acerca de la columna de resultados.  
  
## <a name="see-also"></a>Vea también  
[Procesar resultados & #40; ODBC & #41;](../../relational-databases/native-client-odbc-how-to/processing-results-process-results.md)

[Determinar las características de un conjunto de resultados & #40; ODBC & #41;](../../relational-databases/native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
  
