---
title: DECLARAR @local_variable (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DECLARE
- DECLARE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- table-valued parameters
- variables [SQL Server], declaring
- DECLARE statement
- declaring variables
ms.assetid: d1635ebb-f751-4de1-8bbc-cae161f90821
caps.latest.revision: 76
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 70decceb0fb5bc34f5ac7a32c64ca80cb0977de2
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="declare-localvariable-transact-sql"></a>DECLARAR @local_variable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Las variables se declaran en el cuerpo de un proceso por lotes o un procedimiento con la instrucción DECLARE, y se les asignan valores con una instrucción SET o SELECT. Las variables de cursor pueden declararse con esta instrucción y utilizarse con otras instrucciones relacionadas con los cursores. Después de la declaración, todas las variables se inicializan como NULL, a menos que se proporcione un valor como parte de la declaración.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
DECLARE   
{   
    { @local_variable [AS] data_type  | [ = value ] }  
  | { @cursor_variable_name CURSOR }  
} [,...n]   
| { @table_variable_name [AS] <table_type_definition> }   
  
<table_type_definition> ::=   
     TABLE ( { <column_definition> | <table_constraint> } [ ,... ] )   
  
<column_definition> ::=   
     column_name { scalar_data_type | AS computed_column_expression }  
     [ COLLATE collation_name ]   
     [ [ DEFAULT constant_expression ] | IDENTITY [ (seed ,increment ) ] ]   
     [ ROWGUIDCOL ]   
     [ <column_constraint> ]   
  
<column_constraint> ::=   
     { [ NULL | NOT NULL ]   
     | [ PRIMARY KEY | UNIQUE ]   
     | CHECK ( logical_expression )   
     | WITH ( <index_option > )  
     }   
  
<table_constraint> ::=   
     { { PRIMARY KEY | UNIQUE } ( column_name [ ,... ] )   
     | CHECK ( search_condition )   
     }   
  
<index_option> ::=  
See CREATE TABLE for index option syntax.  
  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DECLARE   
{{ @local_variable [AS] data_type } [ =value [ COLLATE <collation_name> ] ] } [,...n]  
  
```  
  
## <a name="arguments"></a>Argumentos  
@*local_variable*  
 Es el nombre de una variable. Los nombres de variables deben comenzar con un signo de arroba (@). Nombres de variables locales deben cumplir las reglas de [identificadores](../../relational-databases/databases/database-identifiers.md).  
  
*data_type*  
 Es cualquier tipo de tabla definido por el usuario CLR (Common Language Runtime) o tipo de datos de alias, suministrado por el sistema. No puede ser una variable de **texto**, **ntext**, o **imagen** tipo de datos.  
  
 Para obtener más información acerca de los tipos de datos del sistema, consulte [tipos de datos &#40; Transact-SQL &#41; ](../../t-sql/data-types/data-types-transact-sql.md). Para obtener más información acerca de los tipos de datos de alias o tipos definidos por el usuario CLR, vea [CREATE TYPE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-type-transact-sql.md).  
  
 =*valor*  
 Asigna un valor a la variable en línea. El valor puede ser una constante o una expresión, pero debe coincidir con el tipo de declaración de la variable o poder convertirse implícitamente a ese tipo. Para obtener más información, vea [Expresiones &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md).  
  
@*cursor_variable_name*  
 Es el nombre de una variable de cursor. Los nombres de variable de cursor deben comenzar con un signo de arroba (@) y seguir las reglas de los identificadores.  
  
CURSOR  
 Especifica que la variable es una variable de cursor local.  
  
@*table_variable_name*  
 Es el nombre de una variable de tipo **tabla**. Los nombres de variable deben comenzar con un signo de arroba (@) y seguir las reglas de los identificadores.  
  
<table_type_definition>  
Define la **tabla** tipo de datos. La declaración de tabla incluye definiciones de columna, nombres, tipos de datos y restricciones. Solo se permiten los tipos de restricciones PRIMARY KEY, UNIQUE, NULL y CHECK. Un tipo de datos de alias no puede usarse como un tipo de datos de columna escalar si una regla o definición de valor predeterminado está enlazada al tipo.
  
\<table_type_definiton > es un subconjunto de información que se usa para definir una tabla en CREATE TABLE. Aquí se incluyen los elementos y definiciones fundamentales. Para obtener más información, vea [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md).  
  
 *n*  
 Es un marcador de posición que indica que se pueden especificar y asignar valores a varias variables. Cuando se declara **tabla** variables, la **tabla** variable debe ser la única variable que se declara en la instrucción DECLARE.  
  
 *column_name*  
 Es el nombre de la columna de la tabla.  
  
 *scalar_data_type*  
 Especifica que la columna es de un tipo de datos escalar.  
  
 *computed_column_expression*  
 Es una expresión que define el valor de una columna calculada. Se calcula a partir de una expresión mediante otras columnas de la misma tabla. Por ejemplo, una columna calculada puede tener la definición de **costo** AS **precio \* qty**. La expresión puede ser un nombre de columna no calculada, una constante, una función integrada, una variable o cualquier combinación de estos elementos conectados mediante uno o más operadores. La expresión no puede ser una subconsulta o una función definida por el usuario. La expresión no puede hacer referencia a un tipo CLR definido por el usuario.  
  
 [COLLATE *collation_name*]  
 Especifica la intercalación de la columna. *collation_name* puede ser un nombre de intercalación de Windows o un nombre de intercalación de SQL y es aplicable únicamente a las columnas de la **char**, **varchar**, **texto** , **nchar**, **nvarchar**, y **ntext** tipos de datos. Si no se especifica, se asignará a la columna la intercalación del tipo de datos definido por el usuario, si la columna es de un tipo de datos definido por el usuario, o la intercalación de la base de datos actual.  
  
 Para obtener más información acerca de los nombres de intercalación de Windows y SQL, consulte [COLLATE &#40; Transact-SQL &#41; ](~/t-sql/statements/collations.md).  
  
 DEFAULT  
 Especifica el valor suministrado para la columna cuando no se ha especificado explícitamente un valor durante una inserción. Las definiciones DEFAULT se pueden aplicar a cualquier columna excepto los definidos como **timestamp** o aquellos con la propiedad IDENTITY. Las definiciones DEFAULT desaparecen cuando se quita la tabla. Solo se puede utilizar un valor constante como valor predeterminado, por ejemplo, una cadena de caracteres, una función del sistema como SYSTEM_USER() o el valor NULL. Para mantener la compatibilidad con las versiones anteriores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], se puede asignar un nombre de restricción a DEFAULT.  
  
 *expresiónConstante*  
 Es una constante, el valor NULL o una función del sistema que se utiliza como el valor predeterminado de una columna.  
  
 IDENTITY  
 Indica que la nueva columna es una columna de identidad. Cuando se agrega una nueva fila a la tabla [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proporciona un valor incremental único para la columna. Las columnas de identidad se utilizan normalmente junto con restricciones PRIMARY KEY para que actúen como identificador exclusivo de fila para la tabla. La propiedad IDENTITY se puede asignar a **tinyint**, **smallint**, **int**, **decimal(p,0)**, o **numeric(p,0)** columnas. Solo se puede crear una columna de identidad para cada tabla. Las restricciones DEFAULT y los valores predeterminados enlazados no se pueden utilizar en las columnas de identidad. Se debe especificar los dos argumentos, seed e increment, o ninguno. Si no se especifica ninguno, el valor predeterminado es (1,1).  
  
 *valor de inicialización*  
 Es el valor que se utiliza para la primera fila cargada en la tabla.  
  
 *incremento*  
 Es el valor incremental que se agrega al valor de identidad de la fila anterior que se cargó.  
  
 ROWGUIDCOL  
 Indica que la nueva columna es una columna de identificador único global de fila. Solo un **uniqueidentifier** se puede designar la columna por tabla como columna ROWGUIDCOL. La propiedad ROWGUIDCOL se puede asignar solo a un **uniqueidentifier** columna.  
  
 NULL | NOT NULL  
 Indica si NULL se permite en la variable. El valor predeterminado es NULL.  
  
 PRIMARY KEY  
 Es una restricción que exige la integridad de entidad para una o varias columnas dadas a través de un índice único. Solo se puede crear una restricción PRIMARY KEY para cada tabla.  
  
 UNIQUE  
 Es una restricción que proporciona la integridad de entidad para una o varias columnas dadas a través de un índice único. Las tablas pueden tener varias restricciones UNIQUE.  
  
 CHECK  
 Es una restricción que exige la integridad del dominio al limitar los valores posibles que se pueden escribir en una o varias columnas.  
  
 *Filter*  
 Es una expresión lógica que devuelve TRUE o FALSE.  
  
## <a name="remarks"></a>Comentarios  
 Las variables se suelen utilizar en un proceso por lotes o procedimiento como contadores para WHILE, LOOP o un bloque IF…ELSE.  
  
 Las variables pueden usarse solo en las expresiones, no en lugar de nombres de objeto o palabras clave. Para formar instrucciones SQL dinámicas, utilice EXECUTE.  
  
 El alcance de una variable local es el lote en el que está declarada.  
 
 Una variable de tabla no es necesariamente residentes en memoria. Presión de memoria, las páginas que pertenecen a una variable de tabla pueden enviarse a tempdb.
  
 Se puede hacer referencia como origen a una variable de cursor que actualmente tiene asignado un cursor en una instrucción:  
  
-   CLOSE.  
  
-   DEALLOCATE.  
  
-   FETCH.  
  
-   OPEN.  
  
-   DELETE o UPDATE por posición.  
  
-   SET CURSOR variable (en el lado derecho).  
  
 En todas estas instrucciones, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] genera un error si la variable de cursor a la que se hace referencia existe pero actualmente no tiene asignado un cursor. Si una variable de cursor a la que se hace referencia no existe, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] genera el mismo error que genera para una variable no declarada de otro tipo.  
  
 Una variable de cursor:  
  
-   Puede ser el destino de un tipo de cursor u otra variable de cursor. Para obtener más información, consulte [establecer @local_variable &#40; Transact-SQL &#41; ](../../t-sql/language-elements/set-local-variable-transact-sql.md).  
  
-   Se puede hacer referencia a la variable de cursor como el destino de un parámetro de cursor de salida en una instrucción EXECUTE si la variable de cursor no tiene actualmente un cursor asignado.  
  
-   Se debe considerar como un puntero al cursor.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-using-declare"></a>A. Usar DECLARE  
 En el ejemplo siguiente se utiliza una variable local denominada `@find` para recuperar información de contacto para todos los apellidos que comienzan por `Man`.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @find varchar(30);   
/* Also allowed:   
DECLARE @find varchar(30) = 'Man%';   
*/  
SET @find = 'Man%';   
SELECT p.LastName, p.FirstName, ph.PhoneNumber  
FROM Person.Person AS p   
JOIN Person.PersonPhone AS ph ON p.BusinessEntityID = ph.BusinessEntityID  
WHERE LastName LIKE @find;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `LastName            FirstName               Phone`  
  
 `------------------- ----------------------- -------------------------`  
  
 `Manchepalli         Ajay                    1 (11) 500 555-0174`  
  
 `Manek               Parul                   1 (11) 500 555-0146`  
  
 `Manzanares          Tomas                   1 (11) 500 555-0178`  
  
 `(3 row(s) affected)`  
  
### <a name="b-using-declare-with-two-variables"></a>B. Usar DECLARE con dos variables  
 El ejemplo siguiente recupera los nombres de representantes de ventas de [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] que se encuentran en la zona de ventas de Norteamérica y tienen, como mínimo, $2.000.000 en ventas anuales.  
  
```  
USE AdventureWorks2012;  
GO  
SET NOCOUNT ON;  
GO  
DECLARE @Group nvarchar(50), @Sales money;  
SET @Group = N'North America';  
SET @Sales = 2000000;  
SET NOCOUNT OFF;  
SELECT FirstName, LastName, SalesYTD  
FROM Sales.vSalesPerson  
WHERE TerritoryGroup = @Group and SalesYTD >= @Sales;  
```  
  
### <a name="c-declaring-a-variable-of-type-table"></a>C. Declarar una variable de tipo table  
 El ejemplo siguiente crea una variable `table` que almacena los valores especificados en la cláusula OUTPUT de la instrucción UPDATE. Las dos instrucciones `SELECT` que le siguen devuelven los valores en `@MyTableVar` y los resultados de la operación de actualización en la tabla `Employee`. Tenga en cuenta que los resultados en la `INSERTED.ModifiedDate` columna difieren de los valores en el `ModifiedDate` columna en el `Employee` tabla. Esto se debe a que el desencadenador `AFTER UPDATE`, que actualiza el valor de `ModifiedDate` a la fecha actual, se define en la tabla `Employee`. Sin embargo, las columnas que devuelve `OUTPUT` reflejan los datos anteriores a la activación de los desencadenadores. Para obtener más información, vea [cláusula OUTPUT &#40; Transact-SQL &#41; ](../../t-sql/queries/output-clause-transact-sql.md).  
  
```  
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
  
### <a name="d-declaring-a-variable-of-user-defined-table-type"></a>D. Declarar una variable de tipo de tabla definido por el usuario  
 El ejemplo siguiente crea un parámetro con valores de tabla o una variable de tabla denominada `@LocationTVP`. Esto requiere un tipo de tabla definido por el usuario correspondiente denominado `LocationTableType`. Para obtener más información sobre cómo crear un tipo de tabla definido por el usuario, consulte [CREATE TYPE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-type-transact-sql.md). Para obtener más información acerca de los parámetros con valores de tabla, vea [usar parámetros &#40; motor de base de datos &#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md).  
  
```  
DECLARE @LocationTVP   
AS LocationTableType;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Ejemplos: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] y[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-using-declare"></a>E. Usar DECLARE  
 En el ejemplo siguiente se utiliza una variable local denominada `@find` para recuperar información de contacto para todos los apellidos que comienzan por `Walt`.  
  
```  
-- Uses AdventureWorks  
  
DECLARE @find varchar(30);  
/* Also allowed:   
DECLARE @find varchar(30) = 'Man%';  
*/  
SET @find = 'Walt%';  
  
SELECT LastName, FirstName, Phone  
FROM DimEmployee   
WHERE LastName LIKE @find;  
```  
  
### <a name="f-using-declare-with-two-variables"></a>F. Usar DECLARE con dos variables  
 En el ejemplo siguiente se recuperan usa variables para especificar los nombres y apellidos de los empleados de la `DimEmployee` tabla.  
  
```  
-- Uses AdventureWorks  
  
DECLARE @lastName varchar(30), @firstName varchar(30);  
  
SET @lastName = 'Walt%';  
SET @firstName = 'Bryan';  
  
SELECT LastName, FirstName, Phone  
FROM DimEmployee   
WHERE LastName LIKE @lastName AND FirstName LIKE @firstName;  
```  
  
## <a name="see-also"></a>Vea también  
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [Funciones integradas &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [tabla &#40; Transact-SQL &#41;](../../t-sql/data-types/table-transact-sql.md)   
 [Comparar XML con tipo y XML sin tipo](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)  
  
  





