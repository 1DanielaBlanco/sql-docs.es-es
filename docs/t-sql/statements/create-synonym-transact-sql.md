---
title: CREATE SYNONYM (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 04/11/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_SYNONYM_TSQL
- SYNONYM_TSQL
- SYNONYM
- CREATE SYNONYM
dev_langs:
- TSQL
helpviewer_keywords:
- alternate names [SQL Server]
- names [SQL Server], synonyms
- CREATE SYNONYM statement
- synonyms [SQL Server], creating
ms.assetid: 41313809-e970-449c-bc35-85da2ef96e48
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 065b00489ac2ccd0c86e67719679a0b9cc0ece1b
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="create-synonym-transact-sql"></a>CREATE SYNONYM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Crea un nuevo sinónimo.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
-- SQL Server Syntax  
  
CREATE SYNONYM [ schema_name_1. ] synonym_name FOR <object>  
  
<object> :: =  
{  
    [ server_name.[ database_name ] . [ schema_name_2 ]. object_name   
  | database_name . [ schema_name_2 ].| schema_name_2. ] object_name  
}  
```  
  
```  
-- Windows Azure SQL Database Syntax  
  
CREATE SYNONYM [ schema_name_1. ] synonym_name FOR < object >  
  
< object > :: =  
{  
    [database_name. [ schema_name_2 ].| schema_name_2. ] object_name  
}  
```  
  
## <a name="arguments"></a>Argumentos  
 *schema_name_1*  
 Especifica el esquema en el que se crea el sinónimo. Si *esquema* no se especifica, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utiliza el esquema predeterminado del usuario actual.  
  
 *synonym_name*  
 Es el nombre del nuevo sinónimo.  
  
 *nombre_servidor*  
 **Se aplica a**: desde [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] hasta [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Es el nombre del servidor donde se encuentra el objeto base.  
  
 *database_name*  
 Es el nombre de la base de datos donde se encuentra el objeto base. Si *database_name* no se especifica, se usa el nombre de la base de datos actual.  
  
 *schema_name_2*  
 Es el nombre del esquema del objeto base. Si *schema_name* no se especifica se usa el esquema predeterminado del usuario actual.  
  
 *object_name*  
 Es el nombre del objeto base al que hace referencia el sinónimo.  
  
 SQL Database de Microsoft Azure admite el formato de nombre de tres partes nombre_basededatos.[nombre_esquema].nombre_objeto cuando nombre_basededatos es la base de datos actual o tempdb y nombre_objeto comienza con #.  
  
## <a name="remarks"></a>Comentarios  
 No es necesario que el objeto base exista en el momento de crear el sinónimo. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] comprueba la existencia del objeto base en tiempo de ejecución.  
  
 Se pueden crear sinónimos para los siguientes tipos de objetos:  
  
|||  
|-|-|  
|Procedimiento almacenado del ensamblado (CLR)|Función con valores de tabla de ensamblado (CLR)|  
|Función escalar del ensamblado (CLR)|Funciones de agregado del ensamblado (CLR)|  
|Procedimiento de filtro de replicación|Procedimiento almacenado extendido|  
|Función escalar de SQL|Función con valores de tabla SQL|  
|Función SQL con valores de tabla insertados|Procedimiento almacenado de SQL|  
|Ver|Tabla<sup>1</sup> (definido por el usuario)|  
  
 <sup>1 incluye tablas temporales locales y globales</sup>  
  
 No pueden usarse nombres de cuatro partes para objetos base de función.  
  
 Es posible crear, quitar y hacer referencia a sinónimos en SQL dinámico.  
  
## <a name="permissions"></a>Permissions  
 Para crear un sinónimo en un esquema determinado, el usuario debe tener el permiso CREATE SYNONYM y ser propietario del esquema o tener el permiso ALTER SCHEMA.  
  
 El permiso CREATE SYNONYM se puede conceder.  
  
> [!NOTE]  
>  No se necesitan permisos en el objeto base para compilar correctamente la instrucción CREATE SYNONYM, porque la comprobación de los permisos para el objeto base no se realiza hasta el momento de la ejecución.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-creating-a-synonym-for-a-local-object"></a>A. Crear un sinónimo para un objeto local  
 En el ejemplo siguiente, primero se crea un sinónimo para el objeto base `Product` en la base de datos `AdventureWorks2012` y, después, se consulta el sinónimo.  
  
```  
-- Create a synonym for the Product table in AdventureWorks2012.  
CREATE SYNONYM MyProduct  
FOR AdventureWorks2012.Production.Product;  
GO  
  
-- Query the Product table by using the synonym.  
SELECT ProductID, Name   
FROM MyProduct  
WHERE ProductID < 5;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `-----------------------`  
  
 `ProductID   Name`  
  
 `----------- --------------------------`  
  
 `1           Adjustable Race`  
  
 `2           Bearing Ball`  
  
 `3           BB Ball Bearing`  
  
 `4           Headset Ball Bearings`  
  
 `(4 row(s) affected)`  
  
### <a name="b-creating-a-synonym-to-remote-object"></a>B. Crear un sinónimo de un objeto remoto  
 En el ejemplo siguiente, el objeto base (`Contact`) reside en un servidor remoto denominado `Server_Remote`.  
  
**Se aplica a**: desde [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] hasta [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
EXEC sp_addlinkedserver Server_Remote;  
GO  
USE tempdb;  
GO  
CREATE SYNONYM MyEmployee FOR Server_Remote.AdventureWorks2012.HumanResources.Employee;  
GO  
```  
  
### <a name="c-creating-a-synonym-for-a-user-defined-function"></a>C. Crear un sinónimo para una función definida por el usuario  
 En el ejemplo siguiente, se crea una función denominada `dbo.OrderDozen` que aumenta los pedidos a una cantidad uniforme de doce unidades. A continuación, en el ejemplo se crea el sinónimo `dbo.CorrectOrder` para la función `dbo.OrderDozen`.  
  
```  
-- Creating the dbo.OrderDozen function  
CREATE FUNCTION dbo.OrderDozen (@OrderAmt int)  
RETURNS int  
WITH EXECUTE AS CALLER  
AS  
BEGIN  
IF @OrderAmt % 12 <> 0  
BEGIN  
    SET @OrderAmt +=  12 - (@OrderAmt % 12)  
END  
RETURN(@OrderAmt);  
END;  
GO  
  
-- Using the dbo.OrderDozen function  
DECLARE @Amt int;  
SET @Amt = 15;  
SELECT @Amt AS OriginalOrder, dbo.OrderDozen(@Amt) AS ModifiedOrder;  
  
-- Create a synonym dbo.CorrectOrder for the dbo.OrderDozen function.  
CREATE SYNONYM dbo.CorrectOrder  
FOR dbo.OrderDozen;  
GO  
  
-- Using the dbo.CorrectOrder synonym.  
DECLARE @Amt int;  
SET @Amt = 15;  
SELECT @Amt AS OriginalOrder, dbo.CorrectOrder(@Amt) AS ModifiedOrder;  
```  
  
## <a name="see-also"></a>Vea también  
 [DROP SYNONYM &#40; Transact-SQL &#41;](../../t-sql/statements/drop-synonym-transact-sql.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

