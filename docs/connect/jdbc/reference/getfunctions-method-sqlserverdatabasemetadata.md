---
title: Método getFunctions (SQLServerDatabaseMetaData) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 44335cbd-c84d-4ef3-a6a1-fca7eb7ec768
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7cafae4dcdbe9102da3ef4e27ee20b41b231667e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="getfunctions-method-sqlserverdatabasemetadata"></a>Método getFunctions (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera una descripción de las funciones de usuario y del sistema.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public ResultSet getFunctions(java.lang.String catalog,  
                       java.lang.String schemaPattern,  
                       java.lang.String functionNamePattern)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *catalog*  
  
 El nombre de un catálogo en la base de datos. Si es una cadena vacía "", el resultado incluye las funciones sin un catálogo. Si es **null**, el nombre del catálogo no se utiliza para la búsqueda.  
  
 *schemaPattern*  
  
 El nombre de un esquema. Si es una cadena vacía "", el resultado incluye las funciones sin un esquema. Si es **null**, el nombre del esquema no se utiliza para la búsqueda.  
  
 *functionNamePattern*  
  
 Nombre de una función.  
  
## <a name="return-value"></a>Valor devuelto  
 A [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objeto.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 Este método getFunctions especificado por el método getFunctions en la interfaz java.sql.DatabaseMetaData.  
  
 Este método devuelve solamente las funciones de usuario y del sistema que coinciden con el nombre de esquema y de función especificados.  
  
> [!IMPORTANT]  
>  El conjunto de resultados devuelto puede contener funciones para las que el usuario que llamó al método no tenga permiso para ejecutarlas.  
  
 Cada descripción de función incluye las siguientes columnas:  
  
|Nombre|Tipo|Description|  
|----------|----------|-----------------|  
|FUNCTION_CAT|**String**|Nombre de la base de datos en que reside la función.|  
|FUNCTION_SCHEM|**String**|Nombre del esquema de datos en que reside la función.|  
|FUNCTION_NAME|**String**|Nombre de la función.|  
|NUM_INPUT_PARAMS|**int**|Se reserva para su uso futuro, actualmente devuelve un valor -1.|  
|NUM_OUTPUT_PARAMS|**int**|Se reserva para su uso futuro, actualmente devuelve un valor -1.|  
|NUM_RESULT_SETS|**int**|Se reserva para su uso futuro, actualmente devuelve un valor -1.|  
|REMARKS|**String**|Comentarios acerca de la función.|  
|FUNCTION_TYPE|**Corto**|Tipo de la función. Puede ser uno de los siguientes valores:<br /><br /> SQL_PT_UNKNOWN (0)<br /><br /> SQL_PT_PROCEDURE (1)<br /><br /> SQL_PT_FUNCTION (2)|  
  
 Todas las descripciones en el conjunto de resultados devuelto se ordenan según FUNCTION_CAT, FUNCTION_SCHEM, FUNCTION_NAME y SPECIFIC_NAME.  
  
## <a name="see-also"></a>Vea también  
 [Miembros de SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Clase SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
