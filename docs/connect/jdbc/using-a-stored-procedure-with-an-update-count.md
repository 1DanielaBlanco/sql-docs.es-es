---
title: Usar un procedimiento almacenado con un recuento de actualización| Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 64cf4877-5995-4bfc-8865-b7618a5c8d01
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b840cc9b6b8492af0cffa71986d747ac59b7dd57
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 07/27/2018
ms.locfileid: "39278926"
---
# <a name="using-a-stored-procedure-with-an-update-count"></a>Usar un procedimiento almacenado con un recuento de actualizaciones
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Para modificar datos de una base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] mediante un procedimiento almacenado, [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] proporciona la clase [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md). Con la clase SQLServerCallableStatement, puede llamar a los procedimientos almacenados que modifican los datos en la base de datos y devuelven un recuento del número de filas afectadas, lo que se denomina recuento de actualización.  
  
 Una vez configurada la llamada al procedimiento almacenado mediante la clase SQLServerCallableStatement, puede llamar al procedimiento almacenado con el método [execute](../../connect/jdbc/reference/execute-method-sqlserverstatement.md) o [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md). El método executeUpdate devuelve un valor **int** que contiene el número de filas afectadas por el procedimiento almacenado, mientras que el método execute no lo hace. Si usa el método execute y quiere obtener el recuento del número de filas afectadas, puede llamar al método [getUpdateCount](../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md) después de ejecutar el procedimiento almacenado.  
  
> [!NOTE]  
>  Si desea que el controlador JDBC devuelva todos los recuentos de actualizaciones, incluidos los recuentos de actualizaciones devueltos por todos los desencadenadores activados, establezca la propiedad de cadena de conexión lastUpdateCount en "false". Para obtener más información acerca de la propiedad lastUpdateCount, consulte [estableciendo las propiedades de conexión](../../connect/jdbc/setting-the-connection-properties.md).  
  
 A modo de ejemplo, cree la tabla y el procedimiento almacenado siguientes e inserte también datos de ejemplo en la base de datos de ejemplo de [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]:  
  
```sql
CREATE TABLE TestTable   
   (Col1 int IDENTITY,   
    Col2 varchar(50),   
    Col3 int);  
  
CREATE PROCEDURE UpdateTestTable  
   @Col2 varchar(50),  
   @Col3 int  
AS  
BEGIN  
   UPDATE TestTable  
   SET Col2 = @Col2, Col3 = @Col3  
END;  
INSERT INTO dbo.TestTable (Col2, Col3) VALUES ('b', 10);  
```  
  
 En el siguiente ejemplo, se pasa una conexión abierta a la base de datos de ejemplo de [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] a la función, se usa el método execute para llamar al procedimiento almacenado UpdateTestTable y luego se usa el método getUpdateCount para devolver un recuento de las filas afectadas por el procedimiento almacenado.  
  
 [!code[JDBC#UsingSprocWithUpdateCount1](../../connect/jdbc/codesnippet/Java/using-a-stored-procedure_0_1.java)]  
  
## <a name="see-also"></a>Ver también  
 [Usar instrucciones con procedimientos almacenados](../../connect/jdbc/using-statements-with-stored-procedures.md)  
  
  
