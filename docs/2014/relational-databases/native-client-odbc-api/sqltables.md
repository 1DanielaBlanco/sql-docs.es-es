---
title: SQLTables | Documentos de Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLTables function
ms.assetid: 77b6c15c-9cf7-4019-b3f0-3d27d23ef656
caps.latest.revision: 38
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b57c9e62115f7e30dccee569fa32a12545dddaac
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36203171"
---
# <a name="sqltables"></a>SQLTables
  SQLTables se puede ejecutar en un cursor de servidor estático. Un intento de ejecutar SQLTables en un cursor actualizable (dinámico o conjunto de claves) devolverá SQL_SUCCESS_WITH_INFO, que indica que se ha cambiado el tipo de cursor.  
  
 SQLTables informa de las tablas de todas las bases de datos cuando el *CatalogName* parámetro es SQL_ALL_CATALOGS y todos los demás parámetros contienen los valores predeterminados (punteros NULL).  
  
 Para notificar catálogos disponibles, esquemas y tipos de tabla, SQLTables hace un uso especial de cadenas vacías (punteros de bytes de longitud cero). Las cadenas vacías no son valores predeterminados (punteros NULL).  
  
 El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] controlador ODBC Native Client permite notificar información de tablas en servidores vinculados aceptando un nombre de dos partes para el *CatalogName* parámetro: *nombre_servidor_vinculado.nombre_catálogo*.  
  
 SQLTables devuelve información sobre las tablas cuyo nombres coinciden con *TableName* y son propiedad del usuario actual.  
  
## <a name="sqltables-and-table-valued-parameters"></a>SQLTables y parámetros con valores de tabla  
 Cuando el atributo de instrucción SQL_SOPT_SS_NAME_SCOPE tiene el valor SQL_SS_NAME_SCOPE_TABLE_TYPE, en lugar de su valor predeterminado de SQL_SS_NAME_SCOPE_TABLE, SQLTables devuelve información acerca de los tipos de tabla. El valor TABLE_TYPE devuelto para un tipo de tabla en la columna 4 del conjunto de resultados devuelto por SQLTables es el tipo de tabla. Para obtener más información sobre SQL_SOPT_SS_NAME_SCOPE, vea [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 Las tablas, vistas y sinónimos comparten un espacio de nombres común que es distinto del espacio de nombres que utilizan los tipos de tabla. Aunque no es posible tener una tabla y una vista con el mismo nombre, sí se puede tener una tabla y un tipo de tabla con el mismo nombre en el mismo catálogo y esquema.  
  
 Para obtener más información acerca de los parámetros con valores de tabla, vea [parámetros con valores de tabla &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// Get a list of all tables in the current database.  
SQLTables(hstmt, NULL, 0, NULL, 0, NULL, 0, NULL,0);  
  
// Get a list of all tables in all databases.  
SQLTables(hstmt, (SQLCHAR*) "%", SQL_NTS, NULL, 0, NULL, 0, NULL,0);  
  
// Get a list of databases on the current connection's server.  
SQLTables(hstmt, (SQLCHAR*) "%", SQL_NTS, (SQLCHAR*)"", 0, (SQLCHAR*)"",  
    0, NULL, 0);  
```  
  
## <a name="see-also"></a>Vea también  
 [SQLTables, función](http://go.microsoft.com/fwlink/?LinkId=59374)   
 [Detalles de implementación de la API de ODBC](odbc-api-implementation-details.md)  
  
  