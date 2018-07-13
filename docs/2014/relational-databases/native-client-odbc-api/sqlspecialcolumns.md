---
title: SQLSpecialColumns | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLSpecialColumns function
ms.assetid: dffe02ed-8f79-4c9a-af34-98130bbe5462
caps.latest.revision: 34
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f1bc1cb10816f407bed89e65ccc5e8927c82442b
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2018
ms.locfileid: "37408034"
---
# <a name="sqlspecialcolumns"></a>SQLSpecialColumns
  Cuando se solicitan identificadores de fila (*IdentifierType* SQL_BEST_ROWID), **SQLSpecialColumns** devuelve un conjunto de resultados vacío (ninguna fila de datos) para cualquier ámbito solicitado distinto de SQL_SCOPE_CURROW. El conjunto de resultados generado indica que las columnas solamente son válidas dentro de este ámbito.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no admite pseudocolumnas para identificadores. El conjunto de resultados de **SQLSpecialColumns** identificará todas las columnas como SQL_PC_NOT_PSEUDO.  
  
 **SQLSpecialColumns** se puede ejecutar en un cursor estático. Si se intenta ejecutar **SQLSpecialColumns** en un cursor actualizable (dinámico o controlado por conjunto de claves), devuelve SQL_SUCCESS_WITH_INFO para indicar que el tipo de cursor ha cambiado.  
  
## <a name="sqlspecialcolumns-support-for-enhanced-date-and-time-features"></a>SQLSpecialColumns admite características mejoradas de fecha y hora  
 Para obtener información acerca de los valores devueltos para las columnas DATA_TYPE, TYPE_NAME, COLUMN_SIZE, BUFFER_LENGTH y DECIMAL_DIGTS para tipos de fecha y hora, vea [metadatos de catálogo](../native-client-odbc-date-time/metadata-catalog.md).  
  
 Para obtener más información, consulte [mejoras de fecha y hora &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlspecialcolumns-support-for-large-clr-udts"></a>Compatibilidad con SQLSpecialColumns para el UDT CLR grandes  
 **SQLSpecialColumns** admite tipos definidos por el usuario (UDT) CLR grandes. Para obtener más información, consulte [Large CLR User-Defined tipos &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Vea también  
 [Función SQLSpecialColumns](http://go.microsoft.com/fwlink/?LinkId=59371)   
 [Detalles de implementación de la API de ODBC](odbc-api-implementation-details.md)  
  
  
