---
title: DBCC CHECKIDENT (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CHECKIDENT
- DBCC CHECKIDENT
- CHECKIDENT_TSQL
- DBCC_CHECKIDENT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- checking identity values
- reseeding identity values
- resetting identity values
- identity values [SQL Server]
- identity values [SQL Server], checking
- modifying identity values
- current identity values
- DBCC CHECKIDENT statement
- identity values [SQL Server], reseeding
- reporting current identity values
ms.assetid: 2c00ee51-2062-4e47-8b19-d90f524c6427
caps.latest.revision: 63
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d81aa2c26cf693d8ed5613c2aceb970a54db5aca
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-checkident-transact-sql"></a>DBCC CHECKIDENT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Comprueba el valor de identidad actual de la tabla especificada en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y, si fuera necesario, lo cambia. También puede utilizar DBCC CHECKIDENT para establecer manualmente un nuevo valor de identidad actual para la columna de identidad.  
   
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
DBCC CHECKIDENT   
 (   
    table_name  
        [, { NORESEED | { RESEED [, new_reseed_value ] } } ]  
)  
[ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Argumentos  
 *table_name*  
 Es el nombre de la tabla para la que se va a comprobar el valor de identidad actual. La tabla especificada debe contener una columna de identidad. Nombres de tabla deben cumplir las reglas de [identificadores](../../relational-databases/databases/database-identifiers.md). Nombres de partes de dos o tres deben delimitarse, como 'Person.AddressType' o [Person.AddressType].   
  
 NORESEED  
 Especifica que el valor de identidad actual no se debe cambiar.  
  
 RESEED  
 Especifica que el valor de identidad actual se debería cambiar.  
  
 *new_reseed_value*  
 Es el nuevo valor que se va a usar como valor de identidad actual de la columna de identidad.  
  
 WITH NO_INFOMSGS  
 Suprime todos los mensajes de información.  
  
## <a name="remarks"></a>Comentarios  
 Las correcciones concretas realizadas en el valor de identidad actual dependen de las especificaciones de los parámetros.  
  
|Comando DBCC CHECKIDENT|Corrección o correcciones de identidad realizadas|  
|-----------------------------|---------------------------------------------|  
|DBCC CHECKIDENT ( *table_name*, NORESEED)|No se restablece el valor de identidad actual. DBCC CHECKIDENT devuelve el valor de identidad actual y el valor máximo actual de la columna de identidad. Si los dos valores no coinciden, debe restablecer el valor de identidad para evitar posibles errores o espacios en la secuencia de valores.|  
|DBCC CHECKIDENT ( *table_name* )<br /><br /> o bien<br /><br /> DBCC CHECKIDENT ( *table_name*, RESEED)|Si el valor de identidad actual de una tabla es menor que el valor de identidad máximo almacenado en la columna de identidad, se restablece con el valor máximo de la columna de identidad. Vea la sección "Excepciones" que aparece más adelante.|  
|DBCC CHECKIDENT ( *table_name*, RESEED, *new_reseed_value* )|Valor de identidad actual se establece en el *new_reseed_value*. Si no hay filas se han insertado en la tabla desde que se creó la tabla, o si se han quitado todas las filas mediante la instrucción TRUNCATE TABLE, la primera fila insertada después de ejecutar DBCC CHECKIDENT utiliza *new_reseed_value* como la identidad.<br /><br /> Si hay filas en la tabla, se inserta la siguiente fila con el *new_reseed_value* valor. En la versión [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] y versiones anteriores, se usa la siguiente fila insertada *new_reseed_value* + la [incremento actual](../../t-sql/functions/ident-incr-transact-sql.md) valor.<br /><br /> Si la tabla no está vacía y se establece el valor de identidad en un número menor que el valor máximo de la columna de identidad, puede darse una de las siguientes condiciones:<br /><br /> -Si existe una restricción PRIMARY KEY o UNIQUE en la columna de identidad, se generará el mensaje de error 2627 en posteriores operaciones de inserción en la tabla porque el valor de identidad generado estará en conflicto con los valores existentes.<br /><br /> -Si no existe una restricción PRIMARY KEY o UNIQUE, se producirán posteriores operaciones de inserción de valores de identidad duplicados.|  
  
## <a name="exceptions"></a>Excepciones  
 En la tabla siguiente se muestran condiciones en las que DBCC CHECKIDENT no restablece automáticamente el valor de identidad actual y se proporcionan métodos para restablecer el valor.  
  
|Condición|Métodos para restablecer|  
|---------------|-------------------|  
|El valor de identidad actual es mayor que el valor máximo de la tabla.|Ejecute DBCC CHECKIDENT (*table_name*, NORESEED) para determinar el valor máximo actual de la columna y, a continuación, especifique ese valor como el *new_reseed_value* en un DBCC CHECKIDENT (*table_ nombre*, RESEED,*new_reseed_value*) comando.<br /><br /> -OR-<br /><br /> Ejecute DBCC CHECKIDENT (*table_name*, RESEED,*new_reseed_value*) con *new_reseed_value* establecido en un valor muy bajo y, a continuación, ejecute DBCC CHECKIDENT ( *table_name*, RESEED) para corregir el valor.|  
|Se eliminan todas las filas de la tabla.|Ejecute DBCC CHECKIDENT (*table_name*, RESEED,*new_reseed_value*) con *new_reseed_value* establecida en el valor de inicio deseado.|  
  
## <a name="changing-the-seed-value"></a>Cambiar el valor de inicialización  
 El valor de inicialización es el valor insertado en una columna de identidad para la primera fila cargada en la tabla. Todas las filas subsiguientes contienen el valor de identidad actual más el valor de incremento, donde el valor de identidad actual es el último valor de identidad generado para la tabla o vista.  
  
 No puede usar DBCC CHECKIDENT para realizar las tareas siguientes:  
  
-   Cambiar el valor de inicialización original que se especificó para una columna de identidad cuando se creó la tabla o vista.  
  
-   Reinicializar las filas existentes de una tabla o vista.  
  
 Para cambiar el valor de inicialización original y reinicializar cualquier fila existente, debe quitar la columna de identidad y volverla a crear especificando el nuevo valor de inicialización. Cuando la tabla contiene datos, los números de identidad se agregan a las filas existentes con los valores de inicialización e incremento especificados. No se garantiza el orden en que las filas se actualizan.  
  
## <a name="result-sets"></a>Conjuntos de resultados  
 Tanto si se especifican opciones para una tabla que contiene una columna de identidad como si no, DBCC CHECKIDENT devuelve el mensaje siguiente para todas las operaciones excepto cuando se especifica un nuevo valor de inicialización.  
  
`Checking identity information: current identity value '\<current identity value>', current column value '\<current column value>'. DBCC execution completed. If DBCC printed error messages, contact your system administrator.`
  
 Cuando DBCC CHECKIDENT se utiliza para especificar un nuevo valor de inicialización mediante RESEED *new_reseed_value*, se devuelve el mensaje siguiente.  
  
`Checking identity information: current identity value '\<current identity value>'. DBCC execution completed. If DBCC printed error messages, contact your system administrator.`
  
## <a name="permissions"></a>Permissions  
 Autor de la llamada debe poseer el esquema que contiene la tabla o ser miembro del **sysadmin** rol fijo de servidor, el **db_owner** función fija de base de datos, o la **db_ddladmin** fijo rol de base de datos.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-resetting-the-current-identity-value-if-it-is-needed"></a>A. Restablecer el valor de identidad actual si es necesario  
 En el ejemplo siguiente, si es necesario, se restablece el valor de identidad actual de la tabla especificada en la base de datos [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
USE AdventureWorks2012;  
GO  
DBCC CHECKIDENT ('Person.AddressType');  
GO  
```  
  
### <a name="b-reporting-the-current-identity-value"></a>B. Informar del valor de identidad actual  
 En el ejemplo siguiente se notifica el valor de identidad actual de la tabla especificada en la base de datos [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], y no se corrige el valor de identidad si es incorrecto.  
  
```  
USE AdventureWorks2012;   
GO  
DBCC CHECKIDENT ('Person.AddressType', NORESEED);   
GO  
  
```  
  
### <a name="c-forcing-the-current-identity-value-to-a-new-value"></a>C. Hacer que el valor de identidad actual sea un nuevo valor  
 En el ejemplo siguiente, el valor de identidad actual de la columna `AddressTypeID` de la tabla `AddressType` se establece en el valor 10. Dado que la tabla ya contiene filas, la fila siguiente que se inserte utilizará el valor 11, es decir, el nuevo valor de identidad actual definido para el valor de columna más 1.  
  
```  
USE AdventureWorks2012;  
GO  
DBCC CHECKIDENT ('Person.AddressType', RESEED, 10);  
GO  
  
```  
  
## <a name="see-also"></a>Vea también  
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[IDENTITY &#40;propiedad de Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql-identity-property.md)  
[Replicar columnas de identidad](../../relational-databases/replication/publish/replicate-identity-columns.md)  
[USE &#40;Transact-SQL&#41;](../../t-sql/language-elements/use-transact-sql.md)  
[IDENT_SEED &#40; Transact-SQL &#41;](../../t-sql/functions/ident-seed-transact-sql.md)  
[IDENT_INCR &#40; Transact-SQL &#41;](../../t-sql/functions/ident-incr-transact-sql.md)  
  
  

