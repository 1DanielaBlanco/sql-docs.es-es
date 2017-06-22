---
title: Usar salidas FOR JSON en SQL Server y en aplicaciones cliente (SQL Server) | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 06/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FOR JSON, using in client apps
- FOR JSON, using in SQL Server
ms.assetid: 302e5397-b499-4ea3-9a7f-c24ccad698eb
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 439b568fb268cdc6e6a817f36ce38aeaeac11fab
ms.openlocfilehash: 9383b62ac3413b0e4dc8780413bdde09bfc04af3
ms.contentlocale: es-es
ms.lasthandoff: 06/22/2017

---
# <a name="use-for-json-output-in-sql-server-and-in-client-apps-sql-server"></a>Uso de salidas FOR JSON en SQL Server y en aplicaciones cliente (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Los siguientes ejemplos muestran algunas de las formas de usar el **FOR JSON** su JSON y la cláusula output en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o en aplicaciones cliente.  
  
## <a name="use-for-json-output-in-sql-server-variables"></a>Uso de salidas FOR JSON en variables de SQL Server  
La salida de la cláusula FOR JSON es de tipo nvarchar (max), por lo que puede asignar a cualquier variable, como se muestra en el ejemplo siguiente.  
  
```sql  
DECLARE @x NVARCHAR(MAX) = (SELECT TOP 10 * FROM Sales.SalesOrderHeader FOR JSON AUTO)  
```  
  
## <a name="use-for-json-output-in-sql-server-user-defined-functions"></a>Uso de salidas FOR JSON en funciones definidas por el usuario de SQL Server  
 Puede crear funciones definidas por el usuario que formatean conjuntos de resultados como JSON y devuelven esta salida JSON. En el ejemplo siguiente se crea una función definida por el usuario que recupera algunas filas de detalle de pedido de ventas y las formatea como una matriz JSON.  
  
```sql  
CREATE FUNCTION GetSalesOrderDetails(@salesOrderId int)  
 RETURNS NVARCHAR(MAX)  
AS  
BEGIN  
   RETURN (SELECT UnitPrice, OrderQty  
           FROM Sales.SalesOrderDetail  
           WHERE SalesOrderID = @salesOrderId  
           FOR JSON AUTO)  
END
```  
  
 Puede utilizar esta función en un lote o una consulta, como se muestra en el ejemplo siguiente.  
  
```sql  
DECLARE @x NVARCHAR(MAX) = dbo.GetSalesOrderDetails(43659)

PRINT dbo.GetSalesOrderDetails(43659)

SELECT TOP 10
  H.*, dbo.GetSalesOrderDetails(H.SalesOrderId) AS Details
FROM Sales.SalesOrderHeader H
```  
  
## <a name="merge-parent-and-child-data-into-a-single-table"></a>Combinación de datos primarios y secundarios en una sola tabla  
En el ejemplo siguiente, cada conjunto de filas secundarias se formatea como una matriz JSON. La matriz JSON se convierte en el valor de la columna de detalles de la tabla primaria.  
  
```sql  
SELECT TOP 10 SalesOrderId, OrderDate,  
      (SELECT TOP 3 UnitPrice, OrderQty  
         FROM Sales.SalesOrderDetail D  
         WHERE H.SalesOrderId = D.SalesOrderID  
         FOR JSON AUTO) AS Details  
INTO SalesOrder  
FROM Sales.SalesOrderHeader H  
```  
  
## <a name="update-the-data-in-json-columns"></a>Actualización de los datos en columnas JSON  
 En el ejemplo siguiente se muestra que se puede actualizar el valor de una columna que contiene texto JSON.  
  
```sql  
UPDATE SalesOrder  
SET Details =  
     (SELECT TOP 1 UnitPrice, OrderQty  
       FROM Sales.SalesOrderDetail D  
       WHERE D.SalesOrderId = SalesOrder.SalesOrderId  
      FOR JSON AUTO 
```  
  
## <a name="use-for-json-output-in-a-c-client-app"></a>Uso de salidas FOR JSON en una aplicación cliente de C#  
 En el ejemplo siguiente se muestra cómo recuperar la salida JSON de una consulta en un objeto StringBuilder en una aplicación cliente de C#. Se asume que la variable `queryWithForJson` contiene el texto de una instrucción SELECT con una cláusula FOR JSON.  
  
```csharp  
var queryWithForJson = "SELECT ... FOR JSON";
var conn = new SqlConnection("<connection string>");
var cmd = new SqlCommand(queryWithForJson, conn);
conn.Open();
var jsonResult = new StringBuilder();
var reader = cmd.ExecuteReader();
if (!reader.HasRows)
{
    jsonResult.Append("[]");
}
else
{
    while (reader.Read())
    {
        jsonResult.Append(reader.GetValue(0).ToString());
    }
}
```  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>Obtener más información sobre la compatibilidad integrada de JSON en SQL Server  
Para una gran cantidad de soluciones específicas, casos de uso y recomendaciones, consulte el [entradas de blog sobre la compatibilidad integrada de JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) en SQL Server y en la base de datos de SQL de Azure mediante el Administrador de programas de Microsoft Jovan Popovic.
 
## <a name="see-also"></a>Vea también  
 [Format Query Results as JSON with FOR JSON &#40;SQL Server&#41; (Dar formato JSON a los resultados de consulta con FOR JSON &#40;SQL Server&#41;)](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
  
  

