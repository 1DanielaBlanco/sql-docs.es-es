---
title: Formato de salida JSON anidada con el modo PATH (SQL Server) | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 07/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 032761b0-6358-42e4-b05c-dbfd663ac881
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: 9045ebe77cf2f60fecad22672f3f055d8c5fdff2
ms.openlocfilehash: 12dfc255364a410de1ad5c75f3abf38155d6d70f
ms.contentlocale: es-es
ms.lasthandoff: 07/31/2017

---
# <a name="format-nested-json-output-with-path-mode-sql-server"></a>Formato de salida JSON anidada con el modo PATH (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Para mantener el control total sobre la salida de la cláusula **FOR JSON**, especifique la opción**PATH**.  
  
El modo**PATH** le permite crear objetos contenedores y anidar propiedades complejas. Se da formato a los resultados como una matriz de objetos JSON.  
  
La alternativa es usar la opción **AUTO** para aplicar formato a la salida automáticamente en función de la estructura de la instrucción **SELECT**.
 -   Para más información sobre la opción **AUTO**, vea [Aplicar formato a la salida JSON automáticamente con el modo AUTO](../../relational-databases/json/format-json-output-automatically-with-auto-mode-sql-server.md).
 -   Para obtener información general de ambas opciones, vea [Format Query Results as JSON with FOR JSON](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md) (Aplicar formato JSON a los resultados de la consulta con FOR JSON).
 
Estos son algunos ejemplos de la cláusula **FOR JSON** con la opción **PATH** . Aplique formato a los resultados anidados utilizando nombres de columna separados por puntos o consultas anidadas, tal como se muestra en los ejemplos siguientes. De forma predeterminada los valores null no se incluyen en la salida de **FOR JSON**.  

## <a name="example---dot-separated-column-names"></a>Ejemplo: nombres de columna separados por puntos  
La siguiente consulta da formato a las cinco primeras filas de la tabla AdventureWorks `Person` como JSON.  

La cláusula **FOR JSON PATH** usa el alias de columna o el nombre de columna para determinar el nombre de clave en la salida de JSON. Si un alias que contiene puntos, la opción PATH crea objetos anidados.  

 **Query**  
  
```sql  
SELECT TOP 5   
       BusinessEntityID As Id,  
       FirstName, LastName,  
       Title As 'Info.Title',  
       MiddleName As 'Info.MiddleName'  
   FROM Person.Person  
   FOR JSON PATH   
```  
  
 **Resultado**  
  
```json  
[{
    "Id": 1,
    "FirstName": "Ken",
    "LastName": "Sanchez",
    "Info": {
        "MiddleName": "J"
    }
}, {
    "Id": 2,
    "FirstName": "Terri",
    "LastName": "Duffy",
    "Info": {
        "MiddleName": "Lee"
    }
}, {
    "Id": 3,
    "FirstName": "Roberto",
    "LastName": "Tamburello"
}, {
    "Id": 4,
    "FirstName": "Rob",
    "LastName": "Walters"
}, {
    "Id": 5,
    "FirstName": "Gail",
    "LastName": "Erickson",
    "Info": {
        "Title": "Ms.",
        "MiddleName": "A"
    }
}]
```  
   
## <a name="example---multiple-tables"></a>Ejemplo: varias tablas  
Si se hace referencia a más de una tabla en una consulta, **FOR JSON PATH** anida cada columna mediante su alias. La siguiente consulta crea un objeto JSON por par (OrderHeader, OrderDetails) combinado en la consulta. 
  
 **Query**  
  
```sql  
SELECT TOP 2 SalesOrderNumber AS 'Order.Number',  
        OrderDate AS 'Order.Date',  
        UnitPrice AS 'Product.Price',  
        OrderQty AS 'Product.Quantity'  
FROM Sales.SalesOrderHeader H  
   INNER JOIN Sales.SalesOrderDetail D  
     ON H.SalesOrderID = D.SalesOrderID  
FOR JSON PATH   
```  
  
 **Resultado**  
  
```json  
[{
    "Order": {
        "Number": "SO43659",
        "Date": "2011-05-31T00:00:00"
    },
    "Product": {
        "Price": 2024.9940,
        "Quantity": 1
    }
}, {
    "Order": {
        "Number": "SO43659"
    },
    "Product": {
        "Price": 2024.9940
    }
}]
```  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>Más información sobre la compatibilidad integrada de JSON en SQL Server  
Para obtener una gran cantidad de soluciones específicas, casos de uso y recomendaciones, consulte las [entradas de blog sobre la compatibilidad integrada de JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) en SQL Server y en Azure SQL Database ofrecidas por el director de programas de Microsoft Jovan Popovic.

## <a name="see-also"></a>Vea también  
 [Cláusula FOR &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)  

