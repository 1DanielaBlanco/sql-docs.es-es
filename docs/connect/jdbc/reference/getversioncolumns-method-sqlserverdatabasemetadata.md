---
title: Método getVersionColumns (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getVersionColumns
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6dd275d3-d9b2-4db7-938a-d4406c940a7a
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 449af2fc385e569c8a08051f155f704108153f84
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "42784121"
---
# <a name="getversioncolumns-method-sqlserverdatabasemetadata"></a>Método getVersionColumns (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera una descripción de las columnas de una tabla que se actualiza automáticamente cuando cualquier valor de una fila se actualiza.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public java.sql.ResultSet getVersionColumns(java.lang.String catalog,  
                                            java.lang.String schema,  
                                            java.lang.String table)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *catalog*  
  
 Objeto **String** que contiene el nombre del catálogo.  
  
 *schema*  
  
 Objeto **String** que contiene el modelo de nombre del esquema.  
  
 *table*  
  
 Objeto **String** que contiene el nombre de la tabla.  
  
## <a name="return-value"></a>Valor devuelto  
 Objeto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notas  
 Este método getVersionColumns especificado por el método getVersionColumns en la interfaz java.sql.DatabaseMetaData.  
  
 El conjunto de resultados devuelto por el método getVersionColumns contendrá la siguiente información:  
  
|Nombre|Tipo|Descripción|  
|----------|----------|-----------------|  
|SCOPE|**short**|El controlador JDBC no lo admite.|  
|COLUMN_NAME|**String**|Nombre de columna.|  
|DATA_TYPE|**short**|Tipo de datos SQL de java.sql.Types.|  
|TYPE_NAME|**String**|El nombre del tipo de datos.|  
|COLUMN_SIZE|**int**|Precisión de la columna.|  
|BUFFER_LENGTH|**int**|Longitud de la columna, en bytes.|  
|DECIMAL_DIGITS|**short**|Escala de la columna.|  
|PSEUDO_COLUMN|**short**|Indica si la columna es una pseudocolumna. Puede ser uno de los siguientes valores:<br /><br /> versionColumnUnknown (0)<br /><br /> versionColumnNotPseudo (1)<br /><br /> versionColumnPseudo (2)|  
  
> [!NOTE]  
>  Para más información sobre los datos que devuelve el método getVersionColumns, vea "sp_datatype_info (Transact-SQL)" en los Libros en pantalla de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra cómo utilizar el método getVersionColumns para devolver información sobre las columnas que se actualizan automáticamente en la tabla Person.Contact en la base de datos de ejemplo [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)].  
  
```  
public static void executeGetVersionColumns(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getVersionColumns("AdventureWorks", "Person", "Contact");  
      ResultSetMetaData rsmd = rs.getMetaData();  
  
      // Display the result set data.  
      int cols = rsmd.getColumnCount();  
      while(rs.next()) {  
         for (int i = 1; i <= cols; i++) {  
            System.out.println(rs.getString(i));  
         }  
      }  
      rs.close();  
   }   
  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## <a name="see-also"></a>Ver también  
 [Métodos SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Miembros SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Clase SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
