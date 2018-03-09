---
title: Compatibilidad con columnas dispersas (ODBC) | Documentos de Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|ODBC
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 11ae959f-2fb6-4b85-ac5d-1476a82136d4
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9eb733946c7773f05f4fa203a140ce13cc0a827c
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="sparse-columns-support-odbc"></a>Compatibilidad con columnas dispersas (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  En este tema se describe la compatibilidad ODBC de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client con columnas dispersas. Para obtener un ejemplo que muestra la compatibilidad de ODBC con columnas dispersas, vea [llamar a SQLColumns sobre una tabla con columnas dispersas](../../../relational-databases/native-client-odbc-how-to/call-sqlcolumns-on-a-table-with-sparse-columns.md). Para obtener más información sobre las columnas dispersas, vea [Sparse Columns Support in SQL Server Native Client](../../../relational-databases/native-client/features/sparse-columns-support-in-sql-server-native-client.md).  
  
## <a name="statement-metadata"></a>Metadatos de instrucción  
 El campo del descriptor de parámetros de la aplicación (APD) y el atributo de instrucción SQL_SOPT_SS_NAME_SCOPE aceptan los valores adicionales SQL_SS_NAME_SCOPE_EXTENDED y SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET. Estos valores especifican qué columnas se incluyen en el conjunto de resultados devuelto por [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md). Para obtener más información sobre SQL_SOPT_SS_NAME_SCOPE, vea [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 Es posible utilizar un nuevo descriptor de filas de implementación (IRD), un campo SQLSMALLINT de solo lectura denominado SQL_CA_SS_IS_COLUMN_SET, para determinar si una columna es un valor **column_set** XML. SQL_CA_SS_IS_COLUMN_SET toma los valores SQL_TRUE y SQL_FALSE.  
  
## <a name="catalog-metadata"></a>Metadatos de catálogo  
 Dos [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] columnas específicas (SS_IS_SPARSE y SS_IS_COLUMN_SET) se han agregado al conjunto de resultados para [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md).  
  
## <a name="odbc-function-support-for-sparse-columns"></a>Compatibilidad de funciones ODBC con columnas dispersas  
 Las funciones ODBC que se muestran a continuación se han actualizado para admitir columnas dispersas en [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client:  
  
-   [SQLColAttribute](../../../relational-databases/native-client-odbc-api/sqlcolattribute.md)  
  
-   [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md)  
  
-   [SQLGetDescField](../../../relational-databases/native-client-odbc-api/sqlgetdescfield.md)  
  
-   [SQLSetDescField](../../../relational-databases/native-client-odbc-api/sqlsetdescfield.md)  
  
-   [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)  
  
## <a name="see-also"></a>Vea también  
 [Cliente nativo de SQL Server &#40; ODBC &#41;](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
