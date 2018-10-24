---
title: table (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/11/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- table data type [SQL Server]
- table variables [SQL Server]
ms.assetid: 1ef0b60e-a64c-4e97-847b-67930e3973ef
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ba13a096eac5b83a9bc094a2017ddde3cf6d8f81
ms.sourcegitcommit: 485e4e05d88813d2a8bb8e7296dbd721d125f940
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2018
ms.locfileid: "49100466"
---
# <a name="table-transact-sql"></a>table (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Es un tipo de datos especial que se puede utilizar para almacenar un conjunto de resultados para procesar en otro momento. **table** se usa sobre todo para el almacenamiento temporal de un conjunto de filas devueltas como el conjunto de resultados de una función con valores de tabla. Las funciones y las variables se pueden declarar como de tipo **table**. Las variables **table** se pueden usar en funciones, procedimientos almacenados y lotes. Para declarar variables de tipo **table**, use [DECLARE @local_variable](../../t-sql/language-elements/declare-local-variable-transact-sql.md).
  

**Se aplica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (hasta la [versión actual](http://go.microsoft.com/fwlink/p/?LinkId=299658)) [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].
  
![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintaxis  
  
```sql
table_type_definition ::=   
    TABLE ( { <column_definition> | <table_constraint> } [ ,...n ] )   
  
<column_definition> ::=   
    column_name scalar_data_type   
    [ COLLATE <collation_definition> ]   
    [ [ DEFAULT constant_expression ] | IDENTITY [ ( seed , increment ) ] ]   
    [ ROWGUIDCOL ]   
    [ column_constraint ] [ ...n ]   
  
 <column_constraint> ::=   
    { [ NULL | NOT NULL ]   
    | [ PRIMARY KEY | UNIQUE ]   
    | CHECK ( logical_expression )   
    }   
  
<table_constraint> ::=   
     { { PRIMARY KEY | UNIQUE } ( column_name [ ,...n ] )  
     | CHECK ( logical_expression )   
     }   
```  
  
## <a name="arguments"></a>Argumentos  
*table_type_definition*  
Es el mismo subconjunto de información que se utiliza para definir una tabla en CREATE TABLE. La declaración de tabla incluye definiciones de columna, nombres, tipos de datos y restricciones. Solo se permiten los tipos de restricciones PRIMARY KEY, UNIQUE KEY y NULL.  
Para saber más sobre la sintaxis, vea [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md), [CREATE FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-function-transact-sql.md) y [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md).
  
*collation_definition*  
Es la intercalación de la columna que consiste en una configuración regional de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows y un estilo de comparación, una configuración regional de Windows y la notación binaria o una intercalación de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si no se especifica *collation_definition*, la columna hereda la intercalación de la base de datos actual. Si la columna se ha definido como un tipo definido por el usuario CLR (Common Language Runtime), la columna hereda la intercalación del tipo definido por el usuario.
  
## <a name="remarks"></a>Notas  
Se puede hacer referencia a las variables **table** por nombre en la cláusula FROM de un lote, según se muestra en este ejemplo:
  
```sql
SELECT Employee_ID, Department_ID FROM @MyTableVar;  
```  
  
Fuera de una cláusula FROM, se debe hacer referencia a las variables **table** mediante un alias, como se muestra en este ejemplo:
  
```sql
SELECT EmployeeID, DepartmentID   
FROM @MyTableVar m  
JOIN Employee on (m.EmployeeID =Employee.EmployeeID AND  
   m.DepartmentID = Employee.DepartmentID);  
```  
  
Las variables **table** proporcionan las siguientes ventajas para las consultas a pequeña escala que tienen planes de consulta invariables y cuando la recompilación es un tema importante:
-   Una variable **table** se comporta como una variable local. Tiene un ámbito bien definido. Dicho ámbito es la función, el procedimiento almacenado o el lote en que se declara.   
     Dentro de su ámbito, la variable **table** se puede usar como una tabla normal. Puede aplicarse en cualquier lugar de las instrucciones SELECT, INSERT, UPDATE y DELETE donde se utilice una tabla o expresión de tabla. Aunque **table** no puede usarse en esta instrucción:  
  
```sql
SELECT select_list INTO table_variable;
```
  
Las variables de **table** se limpian automáticamente al final de la función, el procedimiento almacenado o el lote en que están definidas.
  
-   Las variables de **table** usadas en procedimientos almacenados causan menos recompilaciones de procedimientos almacenados que cuando se usan tablas temporales, cuando no hay elecciones basadas en cuestiones económicas que afecten al rendimiento.  
-   Las transacciones con variables **table** existen solo mientras dura una actualización en la variable **table**. Por tanto, las variables **table** requieren menos recursos de registro y bloqueo.  
  
## <a name="limitations-and-restrictions"></a>Limitaciones y restricciones
Como las variables **table** no disponen de estadísticas de distribución, no desencadenarán recompilaciones. Por tanto, en muchos casos, el optimizador generará un programa de consultas basándose en que la variable table no tiene filas. Por este motivo, las variables table deben usarse con precaución si se espera una gran cantidad de filas (más de 100). En estos casos, las tablas Temp pueden representar una mejor solución. Por otra parte, para las consultas que se unen a la variable table con otras tablas, puede usar la sugerencia RECOMPILE, que hará que el optimizador use la cardinalidad correcta para la variable table.
  
Las variables **table** no se admiten en el modelo de razonamiento basado en costos del optimizador de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Por lo tanto, no se deben usar cuando se requieren opciones basadas en costos para lograr un plan de consultas eficaz. Se prefieren las tablas temporales cuando se requieren opciones basadas en costos. Esto incluye normalmente consultas con uniones, decisiones de paralelismo y opciones de selección de índice.
  
Las consultas que modifican variables **table** no generan planes de ejecución de consultas en paralelo. El rendimiento puede verse afectado cuando se modifican variables **table** muy grandes o variables **table** en consultas complejas. En estas situaciones, puede optar por utilizar tablas temporales. Para obtener más información, vea [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md). Las consultas que leen variables **table** sin modificarlas pueden generarse en paralelo.
  
En las variables **table** no se pueden crear índices de forma explícita; en estas variables **table** tampoco se conserva ninguna estadística. A partir de [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], se introdujo una sintaxis nueva que le permite crear determinado tipos de índice alineados con la definición de tabla.  Con esta nueva sintaxis, puede crear índices en las variables de **tabla** como parte de la definición de tabla. En determinados casos, el rendimiento puede mejorar si en su lugar se utilizan tablas temporales, las que proporcionan estadísticas y compatibilidad total del índice. Para más información sobre la creación de índices alineados y las tablas temporales, consulte[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md).

Las restricciones CHECK, los valores DEFAULT y las columnas calculadas de la declaración de tipos **table** no pueden llamar a funciones definidas por el usuario.
  
No se permite la operación de asignación entre variables **table**.
  
Las variables **table** no se ven afectadas por las operaciones de reversión de transacciones debido a que tienen un ámbito limitado y no forman parte de la base de datos persistente.
  
Las variables de tabla no se pueden modificar una vez creadas.

## <a name="table-variable-deferred-compilation"></a>Compilación diferida de variables de tabla
La **compilación diferida de variables de tabla** mejora la calidad del plan y el rendimiento general de las consultas que hacen referencia a las variables de tabla. Durante la optimización y la compilación del plan inicial, esta característica propagará las estimaciones de cardinalidad que se basan en los recuentos de filas de variables de tabla reales. Esta información precisa del recuento de filas se usará para optimizar las operaciones del plan de bajada.

> [!NOTE]
> La compilación diferida de variables de tabla es una característica en vista previa (GB) pública de Azure SQL Database.  

Con la compilación aplazada variable de tabla, la compilación de una instrucción que hace referencia a una variable de tabla se aplaza hasta que la primera ejecución real de la instrucción. El comportamiento de esta compilación diferida es idéntico al comportamiento de las tablas temporales y este cambio genera el uso de la cardinalidad real en lugar de la estimación de una fila original. 

Para habilitar la versión preliminar pública de la compilación diferida de variables de tabla, habilite el nivel 150 de compatibilidad de la base de datos para la base de datos a la que se conecta cuando ejecuta la consulta.

La compilación diferida de variables de tabla **no** cambia ninguna otra característica de las variables de tabla. Por ejemplo, esta característica no agrega estadísticas de columna a las variables de tabla.

La compilación diferida de variables de tabla **no aumenta la frecuencia de recompilación**.  En su lugar, se desplaza a donde se produce la compilación inicial. El plan en caché resultante se genera en función del recuento de filas de variables de tabla de la compilación diferida. Consultas consecutivas vuelven a usar el plan en caché hasta que este se expulsa o vuelve a compilar. 

Si el recuento de filas de variables de tabla usado para la compilación del plan inicial representa un valor típico que es significativamente distinto de una estimación del número de filas corregidas, las operaciones de bajada se beneficiarán.  Si el recuento de filas de variables de tabla varía significativamente entre las ejecuciones, es posible que esta característica no mejore el rendimiento.

### <a name="disabling-table-variable-deferred-compilation-without-changing-the-compatibility-level"></a>Deshabilitación de la compilación diferida de variables de tabla sin cambiar el nivel de compatibilidad
La compilación diferida de variables de tabla se puede deshabilitar en el ámbito de base de datos o de instrucción mientras se mantiene el nivel de compatibilidad de base de datos 150 o posterior. Para deshabilitar la compilación diferida de variables de tabla para todas las ejecuciones de consultas que se originan en la base de datos, ejecute lo siguiente en el contexto de la base de datos aplicable:

```sql
ALTER DATABASE SCOPED CONFIGURATION SET DEFERRED_COMPILATION_TV = OFF;
```

Para volver a habilitar la compilación diferida de variables de tabla para todas las ejecuciones de consultas que se originan en la base de datos, ejecute lo siguiente en el contexto de la base de datos aplicable:

```sql
ALTER DATABASE SCOPED CONFIGURATION SET DEFERRED_COMPILATION_TV = ON;
```

También puede deshabilitar la compilación diferida de variables de tabla para una consulta específica mediante la designación de DISABLE_DEFERRED_COMPILATION_TV como una sugerencia de consulta USE HINT.  Por ejemplo:

```sql
DECLARE @LINEITEMS TABLE 
    (L_OrderKey INT NOT NULL,
     L_Quantity INT NOT NULL
    );

INSERT @LINEITEMS
SELECT L_OrderKey, L_Quantity
FROM dbo.lineitem
WHERE L_Quantity = 5;

SELECT  O_OrderKey,
    O_CustKey,
    O_OrderStatus,
    L_QUANTITY
FROM    
    ORDERS,
    @LINEITEMS
WHERE   O_ORDERKEY  =   L_ORDERKEY
    AND O_OrderStatus = 'O'
OPTION (USE HINT('DISABLE_DEFERRED_COMPILATION_TV'));
```

  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-declaring-a-variable-of-type-table"></a>A. Declarar una variable de tipo table  
El ejemplo siguiente crea una variable `table` que almacena los valores especificados en la cláusula OUTPUT de la instrucción UPDATE. Las dos instrucciones `SELECT` que le siguen devuelven los valores en `@MyTableVar` y los resultados de la operación de actualización en la tabla `Employee`. Tenga en cuenta que los resultados de la columna `INSERTED.ModifiedDate` son diferentes de los valores de la columna `ModifiedDate` de la tabla `Employee`. Esto se debe a que el desencadenador `AFTER UPDATE`, que actualiza el valor de `ModifiedDate` a la fecha actual, se define en la tabla `Employee`. Sin embargo, las columnas que devuelve `OUTPUT` reflejan los datos anteriores a la activación de los desencadenadores. Para más información, vea [Cláusula OUTPUT &#40;Transact-SQL&#41;](../../t-sql/queries/output-clause-transact-sql.md).
  
```sql
USE AdventureWorks2012;  
GO  
DECLARE @MyTableVar table(  
    EmpID int NOT NULL,  
    OldVacationHours int,  
    NewVacationHours int,  
    ModifiedDate datetime);  
UPDATE TOP (10) HumanResources.Employee  
SET VacationHours = VacationHours * 1.25   
OUTPUT INSERTED.BusinessEntityID,  
       DELETED.VacationHours,  
       INSERTED.VacationHours,  
       INSERTED.ModifiedDate  
INTO @MyTableVar;  
--Display the result set of the table variable.  
SELECT EmpID, OldVacationHours, NewVacationHours, ModifiedDate  
FROM @MyTableVar;  
GO  
--Display the result set of the table.  
--Note that ModifiedDate reflects the value generated by an  
--AFTER UPDATE trigger.  
SELECT TOP (10) BusinessEntityID, VacationHours, ModifiedDate  
FROM HumanResources.Employee;  
GO  
```  
  
### <a name="b-creating-an-inline-table-valued-function"></a>B. Crear una función alineada con valores de tabla  
En el siguiente ejemplo se devuelve una función alineada con valores de tabla. Devuelve tres columnas `ProductID`, `Name` y el agregado de ventas totales anuales hasta la fecha por tienda como `YTD Total` para cada producto vendido a la tienda.
  
```sql
USE AdventureWorks2012;  
GO  
IF OBJECT_ID (N'Sales.ufn_SalesByStore', N'IF') IS NOT NULL  
    DROP FUNCTION Sales.ufn_SalesByStore;  
GO  
CREATE FUNCTION Sales.ufn_SalesByStore (@storeid int)  
RETURNS TABLE  
AS  
RETURN   
(  
    SELECT P.ProductID, P.Name, SUM(SD.LineTotal) AS 'Total'  
    FROM Production.Product AS P   
    JOIN Sales.SalesOrderDetail AS SD ON SD.ProductID = P.ProductID  
    JOIN Sales.SalesOrderHeader AS SH ON SH.SalesOrderID = SD.SalesOrderID  
    JOIN Sales.Customer AS C ON SH.CustomerID = C.CustomerID  
    WHERE C.StoreID = @storeid  
    GROUP BY P.ProductID, P.Name  
);  
GO  
```  
  
Para invocar la función, ejecute esta consulta.
  
```sql
SELECT * FROM Sales.ufn_SalesByStore (602);  
```  
  
## <a name="see-also"></a>Vea también
[COLLATE &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9)  
[CREATE FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-function-transact-sql.md)  
[Funciones definidas por el usuario](../../relational-databases/user-defined-functions/user-defined-functions.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[Usar parámetros con valores de tabla &#40;motor de base de datos&#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md)  
[Sugerencias de consulta &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-query.md)
