---
title: SQLSpecialColumns | Documentos de Microsoft
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords: SQLSpecialColumns function
ms.assetid: dffe02ed-8f79-4c9a-af34-98130bbe5462
caps.latest.revision: "35"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8ff6889d81489b0009d4c48b5194d772abaec014
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="sqlspecialcolumns"></a>SQLSpecialColumns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Cuando se solicitan identificadores de fila (*IdentifierType* SQL_BEST_ROWID), **SQLSpecialColumns** devuelve un conjunto de resultados vacío (ninguna fila de datos) para cualquier ámbito solicitado distinto de SQL_SCOPE_CURROW. El conjunto de resultados generado indica que las columnas solamente son válidas dentro de este ámbito.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no admite pseudocolumnas para identificadores. El conjunto de resultados de **SQLSpecialColumns** identificará todas las columnas como SQL_PC_NOT_PSEUDO.  
  
 **SQLSpecialColumns** se puede ejecutar en un cursor estático. Si se intenta ejecutar **SQLSpecialColumns** en un cursor actualizable (dinámico o controlado por conjunto de claves), devuelve SQL_SUCCESS_WITH_INFO para indicar que el tipo de cursor ha cambiado.  
  
## <a name="sqlspecialcolumns-support-for-enhanced-date-and-time-features"></a>SQLSpecialColumns admite características mejoradas de fecha y hora  
 Para obtener información acerca de los valores devueltos para las columnas DATA_TYPE, TYPE_NAME, COLUMN_SIZE, BUFFER_LENGTH y DECIMAL_DIGTS para tipos de fecha y hora, vea [metadatos de catálogo](../../relational-databases/native-client-odbc-date-time/metadata-catalog.md).  
  
 Para obtener más información, consulte [fecha y hora mejoras &#40; ODBC &#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlspecialcolumns-support-for-large-clr-udts"></a>Compatibilidad con SQLSpecialColumns para el UDT CLR grandes  
 **SQLSpecialColumns** admite tipos definidos por el usuario (UDT) CLR grandes. Para obtener más información, consulte [Large CLR User-Defined tipos &#40; ODBC &#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Vea también  
 [SQLSpecialColumns, función](http://go.microsoft.com/fwlink/?LinkId=59371)   
 [Detalles de implementación de la API de ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
