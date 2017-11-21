---
title: ALTER TABLE (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 08/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- WAIT_AT_LOW_PRIORITY
- ABORT_AFTER_WAIT
- ABORT_AFTER_WAIT_TSQL
- ALTER_TABLE_TSQL
- ALTER TABLE
- WAIT_AT_LOW_PRIORITY_TSQL
- ALTER_COLUMN_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- columns [SQL Server], resizing
- changing column size
- MAXDOP index option, ALTER TABLE statement
- table modifications [SQL Server], ALTER TABLE
- ALTER TABLE statement
- modifying tables
- partitioned tables [SQL Server], lock escalation
- resizing columns
- removing columns
- switching partitions
- reassigning partitions
- removing constraints
- triggers [SQL Server], disabling
- columns [SQL Server], adding
- LOCK_ESCALATION option of ALTER TABLE
- constraints [SQL Server], deleting
- constraints [SQL Server], disabling
- triggers [SQL Server], enabling
- re-enabling constraints
- index modifications [SQL Server]
- disabling constraints
- columns [SQL Server], removing
- max degree of parallelism option
- locking [SQL Server], tables
- ONLINE option
- disabling triggers
- constraints [SQL Server], adding
- deleting constraints
- adding constraints
- adding columns
- SWITCH partitions
- partitioned tables [SQL Server], switching
- lock escalation [SQL Server], option of ALTER TABLE
- constraints [SQL Server], enabling
- dropping constraints
- dropping columns
- table changes [SQL Server]
ms.assetid: f1745145-182d-4301-a334-18f799d361d1
caps.latest.revision: 281
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7cee79406283aa3b75d41b968370f490cb454ea5
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="alter-table-transact-sql"></a>ALTER TABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Modifica una definición de tabla al alterar, agregar o quitar columnas y restricciones, reasignar y regenerar particiones, o deshabilitar o habilitar restricciones y desencadenadores.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
ALTER TABLE [ database_name . [ schema_name ] . | schema_name . ] table_name   
{   
    ALTER COLUMN column_name   
    {   
        [ type_schema_name. ] type_name   
            [ (   
                {   
                   precision [ , scale ]   
                 | max   
                 | xml_schema_collection   
                }   
            ) ]   
        [ COLLATE collation_name ]   
        [ NULL | NOT NULL ] [ SPARSE ]  
      | { ADD | DROP }   
          { ROWGUIDCOL | PERSISTED | NOT FOR REPLICATION | SPARSE | HIDDEN }  
      | { ADD | DROP } MASKED [ WITH ( FUNCTION = ' mask_function ') ]  
    }   
    [ WITH ( ONLINE = ON | OFF ) ]  
    | [ WITH { CHECK | NOCHECK } ]  
  
    | ADD   
    {   
        <column_definition>  
      | <computed_column_definition>  
      | <table_constraint>   
      | <column_set_definition>   
    } [ ,...n ]  
      | [ system_start_time_column_name datetime2 GENERATED ALWAYS AS ROW START   
                   [ HIDDEN ] [ NOT NULL ] [ CONSTRAINT constraint_name ] 
           DEFAULT constant_expression [WITH VALUES] ,  
            system_end_time_column_name datetime2 GENERATED ALWAYS AS ROW END   
                   [ HIDDEN ] [ NOT NULL ]  [ CONSTRAINT constraint_name ] 
           DEFAULT constant_expression [WITH VALUES] ,  
         ]  
       PERIOD FOR SYSTEM_TIME ( system_start_time_column_name, system_end_time_column_name )  
    | DROP   
     [ {  
         [ CONSTRAINT ]  [ IF EXISTS ]  
         {   
              constraint_name   
              [ WITH   
               ( <drop_clustered_constraint_option> [ ,...n ] )   
              ]   
          } [ ,...n ]  
          | COLUMN  [ IF EXISTS ]  
          {  
              column_name   
          } [ ,...n ]  
          | PERIOD FOR SYSTEM_TIME  
     } [ ,...n ]  
    | [ WITH { CHECK | NOCHECK } ] { CHECK | NOCHECK } CONSTRAINT   
        { ALL | constraint_name [ ,...n ] }   
  
    | { ENABLE | DISABLE } TRIGGER   
        { ALL | trigger_name [ ,...n ] }  
  
    | { ENABLE | DISABLE } CHANGE_TRACKING   
        [ WITH ( TRACK_COLUMNS_UPDATED = { ON | OFF } ) ]  
  
    | SWITCH [ PARTITION source_partition_number_expression ]  
        TO target_table   
        [ PARTITION target_partition_number_expression ]  
        [ WITH ( <low_lock_priority_wait> ) ]  
    | SET   
        (  
            [ FILESTREAM_ON =   
                { partition_scheme_name | filegroup | "default" | "NULL" } ]  
            | SYSTEM_VERSIONING =   
                  {   
                      OFF   
                  | ON   
                      [ ( HISTORY_TABLE = schema_name . history_table_name   
                          [, DATA_CONSISTENCY_CHECK = { ON | OFF } ] 
                          [, HISTORY_RETENTION_PERIOD = 
                          { 
                               INFINITE | number {DAY | DAYS | WEEK | WEEKS 
                 | MONTH | MONTHS | YEAR | YEARS } 
                          } 
                          ]  
                        )  
                      ]  
                  }  
          )  
    | REBUILD   
      [ [PARTITION = ALL]  
        [ WITH ( <rebuild_option> [ ,...n ] ) ]   
      | [ PARTITION = partition_number   
           [ WITH ( <single_partition_rebuild_option> [ ,...n ] ) ]  
        ]  
      ]  
  
    | <table_option>  
  
    | <filetable_option>  
  
    | <stretch_configuration>  
  
}  
[ ; ]  
  
-- ALTER TABLE options  
  
<column_set_definition> ::=   
    column_set_name XML COLUMN_SET FOR ALL_SPARSE_COLUMNS  
  
<drop_clustered_constraint_option> ::=    
    {   
        MAXDOP = max_degree_of_parallelism  
      | ONLINE = { ON | OFF }  
      | MOVE TO   
         { partition_scheme_name ( column_name ) | filegroup | "default" }  
    }  
<table_option> ::=  
    {  
        SET ( LOCK_ESCALATION = { AUTO | TABLE | DISABLE } )  
    }  
  
<filetable_option> ::=  
    {  
       [ { ENABLE | DISABLE } FILETABLE_NAMESPACE ]  
       [ SET ( FILETABLE_DIRECTORY = directory_name ) ]  
    }  
  
<stretch_configuration> ::=  
    {  
      SET (  
        REMOTE_DATA_ARCHIVE   
        {  
            = ON (  <table_stretch_options>  )  
          | = OFF_WITHOUT_DATA_RECOVERY ( MIGRATION_STATE = PAUSED )  
          | ( <table_stretch_options> [, ...n] )  
        }  
            )  
    }  
  
<table_stretch_options> ::=  
    {  
     [ FILTER_PREDICATE = { null | table_predicate_function } , ]  
       MIGRATION_STATE = { OUTBOUND | INBOUND | PAUSED }  
    }  
  
<single_partition_rebuild__option> ::=  
{  
      SORT_IN_TEMPDB = { ON | OFF }  
    | MAXDOP = max_degree_of_parallelism  
    | DATA_COMPRESSION = { NONE | ROW | PAGE | COLUMNSTORE | COLUMNSTORE_ARCHIVE} }  
    | ONLINE = { ON [( <low_priority_lock_wait> ) ] | OFF }  
}  
  
<low_priority_lock_wait>::=  
{  
    WAIT_AT_LOW_PRIORITY ( MAX_DURATION = <time> [ MINUTES ], 
        ABORT_AFTER_WAIT = { NONE | SELF | BLOCKERS } )   
}  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
ALTER TABLE [ database_name . [schema_name ] . | schema_name. ] source_table_name   
{  
    ALTER COLUMN column_name  
        {   
            type_name [ ( precision [ , scale ] ) ]   
            [ COLLATE Windows_collation_name ]   
            [ NULL | NOT NULL ]   
        }  
    | ADD { <column_definition> | <column_constraint> FOR column_name} [ ,...n ]  
    | DROP { COLUMN column_name | [CONSTRAINT] constraint_name } [ ,...n ]  
    | REBUILD {  
            [ PARTITION = ALL [ WITH ( <rebuild_option> ) ] ] 
          | [ PARTITION = partition_number [ WITH ( <single_partition_rebuild_option> ] ]
      } 
    | { SPLIT | MERGE } RANGE (boundary_value)  
    | SWITCH [ PARTITION source_partition_number  
        TO target_table_name [ PARTITION target_partition_number ]  
}  
[;]  
  
<column_definition>::=  
{  
    column_name  
    type_name [ ( precision [ , scale ] ) ]   
    [ <column_constraint> ]  
    [ COLLATE Windows_collation_name ]  
    [ NULL | NOT NULL ]  
}  
  
<column_constraint>::=  
    [ CONSTRAINT constraint_name ] DEFAULT constant_expression  

<rebuild_option > ::=   
{  
    DATA_COMPRESSION = { COLUMNSTORE | COLUMNSTORE_ARCHIVE }
        [ ON PARTITIONS ( {<partition_number> [ TO <partition_number>] } [ , ...n ] ) ]   
}

<single_partition_rebuild_option > ::=   
{  
    DATA_COMPRESSION = { COLUMNSTORE | COLUMNSTORE_ARCHIVE }  
}  
```    

   
## <a name="arguments"></a>Argumentos  
 *database_name*  
 Es el nombre de la base de datos en la que se creó la tabla.  
  
 *schema_name*  
 Es el nombre del esquema al que pertenece la tabla.  
  
 *table_name*  
 Es el nombre de la tabla que se va a modificar. Si la tabla no se encuentra en la base de datos actual o no está contenida en el esquema propiedad del usuario actual, la base de datos y el esquema deben especificarse explícitamente.  
  
 ALTER COLUMN  
 Especifica que la columna con nombre va a cambiarse o modificarse.  
  
 La columna modificada no puede ser ninguna de las siguientes:  
  
-   Una columna con un **timestamp** tipo de datos.  
  
-   La columna ROWGUIDCOL de la tabla.  
  
-   Una columna calculada o usada en una columna calculada.  
  
-   Use en las estadísticas generadas por la instrucción CREATE STATISTICS a menos que la columna es una **varchar**, **nvarchar**, o **varbinary** no se cambia el tipo de datos, el tipo de datos, y el nuevo tamaño sea igual o mayor que el tamaño anterior, o si se cambia la columna de not null a null. Quite primero las estadísticas con la instrucción DROP STATISTICS. Las estadísticas generadas automáticamente por el optimizador de consultas se quitan automáticamente con ALTER COLUMN.  
  
-   Una columna utilizada en una restricción PRIMARY KEY o [FOREIGN KEY] REFERENCES.  
  
-   Una columna utilizada en una restricción CHECK o UNIQUE. Sin embargo, se permite el cambio de longitud de una columna de longitud variable en una restricción CHECK o UNIQUE.  
  
-   Una columna asociada a la definición predeterminada. No obstante, la longitud, precisión o escala de una columna puede cambiarse si el tipo de datos no se cambia.  
  
Tipo de datos de **texto**, **ntext** y **imagen** columnas pueden cambiarse de las maneras siguientes:  
  
    -   **texto** a **varchar (max)**, **nvarchar (max)**, o **xml**  
  
    -   **ntext** a **varchar (max)**, **nvarchar (max)**, o **xml**  
  
    -   **imagen** a **varbinary (max)**  
  
Algunos cambios del tipo de datos podrían suponer un cambio en los datos. Por ejemplo, cambiar un **nchar** o **nvarchar** columna **char** o **varchar** puede suponer la conversión de caracteres extendidos. Para obtener más información, vea [CAST y CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md). Reducir la precisión o escala de una columna puede dar como resultado que se trunquen los datos.  
  
     The data type of a column of a partitioned table cannot be changed.  
  
 No se puede cambiar el tipo de datos de las columnas incluidas en un índice, a menos que la columna es una **varchar**, **nvarchar**, o **varbinary** tipo de datos, y el nuevo tamaño sea igual o mayor que el tamaño anterior.  
  
 No se puede cambiar las columnas incluidas en una restricción primary key, **NOT NULL** a **NULL**.  
  
 Si la columna que se está modificando se cifra con cifrado, puede cambiar el tipo de datos a un tipo de datos compatible (como INT a BIGINT) pero no se puede cambiar cualquier configuración de cifrado.  
  
 *column_name*  
 Es el nombre de la columna que se va a modificar, agregar o quitar. *column_name* puede tener un máximo de 128 caracteres. Para las nuevas columnas, *column_name* se puede omitir en las columnas creadas con un **timestamp** tipo de datos. El nombre **timestamp** se utiliza si no *column_name* se especifica para un **marca de tiempo** columna tipo de datos.  
  
 [ *type_schema_name***.** ] *type_name*  
 Es el nuevo tipo de datos de la columna modificada o el tipo de datos de la columna agregada. *TYPE_NAME* no se puede especificar para las columnas existentes de tablas con particiones. *TYPE_NAME* puede ser cualquiera de las siguientes acciones:  
  
-   Un tipo de datos del sistema de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Un tipo de datos del alias basado en el tipo de datos del sistema de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Los tipos de datos de alias se crean con la instrucción CREATE TYPE antes de que puedan utilizarse en una definición de tabla.  
  
-   Un tipo definido por el usuario de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] y el esquema al que pertenece. Los tipos definidos por el usuario de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] se crean con la instrucción CREATE TYPE antes de poder usarlos en una definición de tabla.  
  
Los siguientes son los criterios para *type_name* de una columna alterada:  
  
-   El tipo de datos anterior debe poderse convertir implícitamente al nuevo tipo de datos.  
  
-   *TYPE_NAME* no puede ser **marca de tiempo**.  
  
-   Los valores predeterminados de ANSI_NULL están siempre activados para ALTER COLUMN; si no se especifican, la columna admite valores NULL.  
  
-   El relleno ANSI_PADDING está siempre activado para ALTER COLUMN.  
  
-   Si la columna alterada es una columna de identidad *new_data_type* debe ser un tipo de datos que admite la propiedad identity.  
  
-   La configuración actual de SET ARITHABORT se ignora. ALTER TABLE opera como si la opción ARITHABORT estuviera activada.  
  
> [!NOTE]  
>  Si no se especifica la cláusula COLLATE, la modificación de un tipo de datos de columna tendrá como resultado un cambio de intercalación a la intercalación predeterminada de la base de datos.  
  
 *precisión*  
 Es la precisión del tipo de datos especificado. Para obtener más información acerca de los valores de precisión válidos, consulte [precisión, escala y longitud &#40; Transact-SQL &#41; ](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
 *escala*  
 Es la escala del tipo de datos especificado. Para obtener más información acerca de los valores de escala válidos, consulte [precisión, escala y longitud &#40; Transact-SQL &#41; ](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
 **max**  
 Solo se aplica a la **varchar**, **nvarchar**, y **varbinary** tipos de datos para almacenar 2 ^ 31-1 bytes de caracteres, datos binarios y de los datos Unicode.  
  
 *xml_schema_collection*  
 **Se aplica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Solo se aplica a la **xml** tipo de datos para asociar un esquema XML con el tipo. Antes de escribir un **xml** columna a una colección de esquemas, la colección de esquemas debe crearse en la base de datos mediante el uso de [CREATE XML SCHEMA COLLECTION](../../t-sql/statements/create-xml-schema-collection-transact-sql.md).  
  
COLLATE \< *collation_name* > especifica la nueva intercalación para la columna alterada. Si no se especifica, se asigna a la columna la intercalación predeterminada de la base de datos. El nombre de intercalación puede ser un nombre de intercalación de Windows o un nombre de intercalación de SQL. Para obtener una lista y obtener más información, vea [nombre de intercalación de Windows &#40; Transact-SQL &#41; ](../../t-sql/statements/windows-collation-name-transact-sql.md) y [SQL nombre de intercalación de servidor &#40; Transact-SQL &#41; ](../../t-sql/statements/sql-server-collation-name-transact-sql.md).  
  
 La cláusula COLLATE se puede utilizar para cambiar las intercalaciones solo de las columnas de la **char**, **varchar**, **nchar**, y **nvarchar** tipos de datos. Para modificar la intercalación de una columna de tipo de datos de alias definido por el usuario, debe ejecutar distintas instrucciones ALTER TABLE para cambiar la columna por un tipo de datos del sistema de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y modificar su intercalación, y a continuación volver a modificar la columna para que sea un tipo de datos de alias.  
  
 ALTER COLUMN no puede tener un cambio de intercalación si existe alguna de las siguientes condiciones:  
  
-   Si una restricción CHECK, una restricción FOREIGN KEY o las columnas calculadas hacen referencia a la columna cambiada.  
  
-   Si se ha creado algún índice, estadística o índice de texto completo en la columna. Las estadísticas creadas automáticamente en la columna cambiada se quitarán si se altera la intercalación de columna.  
  
-   Si una función o vista enlazada a esquema hace referencia a la columna.  
  
 Para obtener más información, vea [COLLATE &#40;Transact-SQL&#41;](~/t-sql/statements/collations.md).  
  
NULL | NOT NULL  
 Especifica si la columna puede aceptar valores NULL. Las columnas que no permiten valores NULL solo se pueden agregar con ALTER TABLE si tienen especificado un valor predeterminado o si la tabla está vacía. NOT NULL solo puede especificarse para las columnas si también se especifica PERSISTED. Si la nueva columna permite valores NULL y no se especifica un valor predeterminado, la nueva columna contendrá un valor NULL en cada fila de la tabla. Si la nueva columna permite valores NULL y se agrega una definición predeterminada con la nueva columna, se puede utilizar la opción WITH VALUES para almacenar el valor predeterminado en la nueva columna para cada fila existente en la tabla.  
  
 Si la nueva columna no permite valores NULL y la tabla no está vacía, debe agregarse una definición DEFAULT con la nueva columna y ésta se carga automáticamente con el valor predeterminado en las nuevas columnas de cada fila existente.  
  
 NULL puede especificarse en ALTER COLUMN para forzar que una columna NOT NULL permita valores NULL, excepto en el caso de las columnas de las restricciones PRIMARY KEY. NOT NULL solo se puede especificar en ALTER COLUMN si la columna no contiene valores NULL. Los valores NULL deben actualizarse a algún valor para poder permitir ALTER COLUMN NOT NULL, como:  
  
```  
UPDATE MyTable SET NullCol = N'some_value' WHERE NullCol IS NULL;  
ALTER TABLE MyTable ALTER COLUMN NullCOl NVARCHAR(20) NOT NULL;  
```  
  
 Cuando cree o altere una tabla con las instrucciones CREATE TABLE o ALTER TABLE, los valores de sesión y de la base de datos influirán en la nulabilidad, y posiblemente la invalidarán, para el tipo de datos utilizado en la definición de una columna. Recomendamos definir siempre explícitamente una columna como NULL o como NOT NULL en el caso de las columnas no calculadas.  
  
 Si agrega una columna con un tipo de datos definidos por el usuario, recomendamos definir la columna con la misma nulabilidad del tipo de datos definidos por el usuario y especificar un valor predeterminado para la columna. Para obtener más información, vea [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md).  
  
> [!NOTE]  
>  Si NULL o NOT NULL se especifica con ALTER COLUMN, *new_data_type* [(*precisión* [, *escala* ])] debe especificarse también. Si el tipo de datos, la precisión y la escala no se cambian, especifique los valores actuales de la columna.  
  
 [ {ADD | DROP} ROWGUIDCOL ]  
 **Se aplica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Especifica que la propiedad ROWGUIDCOL se agrega a la columna indicada o se quita de ella. ROWGUIDCOL indica que la columna es una columna GUID de fila. Solo un **uniqueidentifier** se puede designar la columna por tabla como columna ROWGUIDCOL, y la propiedad ROWGUIDCOL se puede asignar solo a un **uniqueidentifier** columna. ROWGUIDCOL no puede asignarse a una columna de un tipo de datos definido por el usuario.  
  
 ROWGUIDCOL no exige la exclusividad de los valores almacenados en la columna y no genera automáticamente valores para las nuevas filas que se insertan en la tabla. Para generar valores únicos para cada columna, utilice la función NEWID en instrucciones INSERT o especifique la función NEWID como la predeterminada para la columna.  
  
 [ {ADD | DROP} PERSISTED ]  
 Especifica que la propiedad PERSISTED se agrega a la columna indicada o se quita de ella. La columna debe ser una columna calculada definida mediante una expresión determinista. Para las columnas especificadas como PERSISTED, [!INCLUDE[ssDE](../../includes/ssde-md.md)] almacena físicamente los valores calculados en la tabla y actualiza los valores cuando se actualiza cualquiera de las otras columnas de las que depende la columna calculada. Al marcar una columna calculada como PERSISTED, puede crear índices sobre columnas calculadas definidas sobre expresiones que son deterministas, pero no precisas. Para obtener más información, vea [Indexes on Computed Columns](../../relational-databases/indexes/indexes-on-computed-columns.md).  
  
 Las columnas calculadas que se utilizan como columna de partición de una tabla con particiones deben marcarse explícitamente como PERSISTED.  
  
 DROP NOT FOR REPLICATION  
 **Se aplica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Especifica que los valores de columnas de identidad se incrementan cuando los agentes de replicación realizan operaciones de inserción. Esta cláusula se puede especificar únicamente si *column_name* es una columna de identidad.  
  
 SPARSE  
 Indica que la columna es una columna dispersa. El almacenamiento de columnas dispersas está optimizado para los valores NULL. Las columnas dispersas no se pueden designar como NOT NULL. Al convertir una columna de dispersa a no dispersa o viceversa, se bloquea la tabla durante la ejecución del comando. Es posible que tenga que usar la cláusula REBUILD para recuperar espacio. Para obtener más información sobre las columnas dispersas y restricciones adicionales, consulte [usar columnas dispersas](../../relational-databases/tables/use-sparse-columns.md).  
  
 Agregar enmascarada con (función = ' *mask_function* ')  
 **Se aplica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Especifica una máscara dinámica de datos. *mask_function* es el nombre de la función de enmascaramiento con los parámetros adecuados. Existen tres funciones:  
  
-   es default()  
-   Email()  
-   Partial()  
-   Random()  
  
 Para quitar una máscara, utilice `DROP MASKED`. Para los parámetros de función, vea [Dynamic Data Masking](../../relational-databases/security/dynamic-data-masking.md).  
  
CON (ONLINE = ON | OFF) \<tal como se aplica al modificar una columna >  
 **Se aplica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Permite realizar numerosas acciones de alteración de columna mientras la tabla sigue estando disponible. El valor predeterminado es OFF. La alteración de columna se puede realizar en línea para los cambios de columna relacionados con el tipo de datos, la precisión o la longitud de la columna, la nulabilidad, la escasez y la intercalación.  
  
 La alteración de columna en línea permite a las estadísticas automáticas y a las creadas por el usuario hacer referencia a la columna alterada durante la operación ALTER COLUMN. Esto permite realizar las consultas como habitualmente. Al final de la operación, se quitan las estadísticas automáticas que hacen referencia a la columna y se invalidan las estadísticas creadas por el usuario. El usuario debe actualizar manualmente las estadísticas generadas por el usuario una vez completada la operación. Si la columna forma parte de una expresión de filtro para estadísticas o índices, no se puede realizar una operación de alteración de columna.  
  
-   Mientras se ejecuta la operación de alteración en línea de columna, todas las operaciones que podrían tomar una dependencia en la columna (índices, vistas, etc.) se bloquearán o devolverán el error correspondiente. Esto garantiza que no se produzcan problemas en la alteración de columna en línea debido a las dependencias introducidas durante la ejecución de la operación.  
  
-   No se admite la alteración de columnas NOT NULL a NULL como una operación en línea cuando los índices no agrupados en clúster hacen referencia a la columna alterada.  
  
-   No se admite la alteración en línea cuando una restricción CHECK hace referencia a la columna y la operación de alteración limita la precisión de esta (numéricos o fecha y hora).  
  
-   El **low_priority_lock_wait** opción no puede utilizarse con alteración en línea de columna.  
  
-   ALTER COLUMN … ADD/DROP PERSISTED no se admite para alter column en línea.  
  
-   ALTER COLUMN … ADD/DROP ROWGUIDCOL/NOT FOR REPLICATION no se ve afectada por alter column en línea.  
  
-   La alteración de columna en línea no admite la modificación de una tabla con el seguimiento de cambios habilitado que sea un publicador de replicación de mezcla.  
  
-   La alteración de columna en línea no admite la alteración desde tipos de datos CLR o a estos.  
  
-   La alteración de columna en línea no admite la alteración a un tipo de datos XML con una colección de esquemas diferente a la colección de esquemas actual.  
  
-   La alteración de columna en línea no reduce las restricciones sobre cuándo se puede modificar una columna. Las referencias de las estadísticas/índice, etc. podrían provocar el error de la alteración.  
  
-   La alteración de columna en línea no admite la modificación de más de una columna simultáneamente.  
  
-   La alteración en línea columna no tiene ningún efecto en las tablas temporales con versión del sistema. La columna ALTER no se realiza como en línea, independientemente del valor que se especificó para la opción ONLINE.  
  
La alteración de columna en línea tiene requisitos, restricciones y funciones similares a los de la regeneración de índice en línea. Esto incluye:  
  
-   No se admite la regeneración de índices en línea cuando la tabla contiene columnas LOB o filestream heredadas, o cuando tiene un índice de almacén de columnas. Las mismas limitaciones se aplican para las alteraciones de columna en línea.  
  
-   Una columna existente que se va a modificar requiere dos veces la misma asignación de espacio; para la columna original y para la columna oculta recién creada.  
  
-   La estrategia de bloqueo durante una operación de alteración de columna en línea sigue el mismo patrón de bloqueo usado para la generación de índice en línea.  
  
WITH CHECK | WITH NOCHECK  
 Especifica si los datos de la tabla se han validado o no frente a una restricción FOREIGN KEY o CHECK recién agregada o habilitada de nuevo. Si no se especifica, se supone WITH CHECK para las restricciones nuevas y WITH NOCHECK para las restricciones que se han habilitado otra vez.  
  
 Si no desea volver a comprobar las restricciones CHECK o FOREIGN KEY nuevas con los datos existentes, utilice WITH NOCHECK. No se recomienda que haga esto, excepto en casos muy contados. La nueva restricción se evaluará en todas las actualizaciones futuras. Las infracciones de restricción que se supriman mediante WITH NOCHECK cuando se agrega la restricción pueden hacer que las actualizaciones futuras no se puedan llevar a cabo si actualizan filas con datos que no cumplan la restricción.  
  
 El optimizador de consultas no considera las restricciones definidas como WITH NOCHECK. Estas restricciones se pasan por alto hasta que se vuelven a habilitar mediante `ALTER TABLE table WITH CHECK CHECK CONSTRAINT ALL`.  
  
 ADD  
 Especifica que se agregan uno o más definiciones de columna, definiciones de columnas calculadas o restricciones de tabla, o las columnas que se va a utilizar el sistema de control de versiones de sistema.  
  
 PERIOD FOR SYSTEM_TIME (system_start_time_column_name, system_end_time_column_name)  
 **Se aplica a**: [!INCLUDE[ssCurrentLong](../../includes/sscurrentlong-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Especifica los nombres de las columnas que el sistema usará para registrar el período durante el que un registro es válido. Puede especificar las columnas existentes o crear nuevas columnas como parte del argumento de complemento PERIOD FOR SYSTEM_TIME. Las columnas deben tener la propiedad datatype de datetime2 y se debe definir como NOT NULL. Si una columna de período se define como NULL, se producirá un error. Puede definir un [column_constraint &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-table-column-constraint-transact-sql.md) o [especificar valores predeterminados para las columnas](../../relational-databases/tables/specify-default-values-for-columns.md) para las columnas system_start_time y system_end_time. Vea el ejemplo A en el [control de versiones de sistema](#system_versioning) ejemplos siguientes se muestra el uso de un valor predeterminado para la columna system_end_time.  
  
 Utilice este argumento junto con el argumento de establecer SYSTEM_VERSIONING para habilitar el control de versiones de sistema en una tabla existente. Para obtener más información, consulte [tablas temporales](../../relational-databases/tables/temporal-tables.md) y [Introducción a las tablas temporales de base de datos de SQL Azure](https://azure.microsoft.com/documentation/articles/sql-database-temporal-tables/).  
  
 Como de [!INCLUDE[ssCurrentLong](../../includes/sscurrentlong-md.md)], los usuarios podrán marcar una o ambas columnas de periodo con **HIDDEN** marca implícitamente ocultar estas columnas que **seleccione \* FROM**  *\<tabla >* no devuelve un valor para esas columnas. De forma predeterminada, no se ocultan las columnas de periodo. Para poder usarlo, las columnas ocultas deben incluirse explícitamente en todas las consultas que hacen referencia directa a la tabla temporal.  
  
 DROP  
 Especifica que se quitan uno o más definiciones de columna, definiciones de columnas calculadas o restricciones de tabla, o para quitar la especificación de las columnas que se va a utilizar el sistema de control de versiones de sistema.  
  
 RESTRICCIÓN *constraint_name*  
 Especifica que *constraint_name* se quita de la tabla. Pueden especificarse varias restricciones.  
  
 El nombre definido por el usuario o proporcionado por el sistema de la restricción se puede determinar consultando la **sys.check_constraint**, **sys.default_constraints**, **sys.key_constraints**, y **sys.foreign_keys** vistas de catálogo.  
  
 Una restricción PRIMARY KEY no puede quitarse si existe un índice XML en la tabla.  
  
 COLUMNA *column_name*  
 Especifica que *constraint_name* o *column_name* se quita de la tabla. Pueden especificarse varias columnas.  
  
 Una columna no puede quitarse cuando:  
  
-   Se utiliza en un índice.  
  
-   Se utiliza en una restricción CHECK, FOREIGN KEY, UNIQUE o PRIMARY KEY.  
  
-   Está asociada con un valor predeterminado definido con la palabra clave DEFAULT o enlazada a un objeto predeterminado.  
  
-   Está enlazada a una regla.  
  
> [!NOTE]  
>  Quitar una columna no recupera el espacio en disco de la columna. Tendrá que recuperar el espacio en disco de una columna quitada cuando el tamaño de fila de una tabla esté a punto de superar su límite o lo haya hecho ya. Recuperar espacio mediante la creación de un índice agrupado en la tabla o volver a generar un índice clúster existente mediante el uso de [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md). Para obtener información sobre las repercusiones de quitar los tipos de datos LOB, vea este [entrada de blog CSS](http://blogs.msdn.com/b/psssql/archive/2012/12/03/how-it-works-gotcha-varchar-max-caused-my-queries-to-be-slower.aspx).  
  
 PERIOD FOR SYSTEM_TIME  
 **Se aplica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Quita la especificación de las columnas que se va a utilizar el sistema de control de versiones de sistema.  
  
 CON \<drop_clustered_constraint_option >  
 Especifica que se han establecido una o más opciones para quitar restricciones en clúster.  
  
 MAXDOP = *max_degree_of_parallelism*  
 **Se aplica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Invalida el **grado máximo de paralelismo** opción de configuración durante la operación. Para obtener más información, vea [Configure the max degree of parallelism Server Configuration Option](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md).  
  
 Utilice la opción MAXDOP para limitar el número de procesadores utilizados en la ejecución de planes paralelos. El máximo es 64 procesadores.  
  
 *max_degree_of_parallelism* puede ser uno de los siguientes valores:  
  
 1  
 Suprime la generación de planes paralelos.  
  
 \>1  
 Restringe el número máximo de procesadores utilizados en una operación de índice paralelo para el número especificado.  
  
 0 (predeterminado)  
 Usa el número real de procesadores o menos, según la carga de trabajo actual del sistema.  
  
 Para obtener más información, vea [Configurar operaciones de índice en paralelo](../../relational-databases/indexes/configure-parallel-index-operations.md).  
  
> [!NOTE]  
>  Operaciones de índice en paralelo no están disponibles en todas las ediciones de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Para obtener más información, consulte [ediciones y características admitidas en SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 En línea  **=**  {ON | **OFF** } \<tal como se aplica a drop_clustered_constraint_option >  
 Especifica si las tablas subyacentes y los índices asociados están disponibles para realizar consultas y modificar datos durante la operación de índice. El valor predeterminado es OFF. REBUILD se puede realizar como una operación ONLINE.  
  
 ON  
 Los bloqueos de tabla de larga duración no se mantienen durante la operación de indización. Durante la fase principal de la operación de índice, solo se mantiene un bloqueo preventivo en la tabla de origen. De esta forma, las consultas o actualizaciones realizadas sobre la tabla y los índices subyacentes pueden continuar. Al principio de la operación, se mantiene un bloqueo compartido (S) sobre el objeto de origen durante un breve espacio de tiempo. Al final de la operación, durante un breve espacio de tiempo, se adquiere un bloqueo compartido (S) sobre el origen si se está creando un índice no clúster; o se adquiere un bloqueo SCH-M (modificación del esquema) cuando se crea o se quita un índice clúster en línea y cuando se regenera un índice clúster o no clúster. ONLINE no se puede establecer en ON cuando se crea un índice en una tabla temporal local. Solo se permite la operación de regeneración de montón de un único subproceso.  
  
 Para ejecutar la instrucción DDL para **conmutador** o regeneración de índice en línea, todos los activo de bloqueo de transacciones que se ejecutan en una tabla determinada debe completarse. Cuando se ejecuta, el **conmutador** o la operación de regeneración impide que la nueva transacción se inicie y podría afectar significativamente al rendimiento de la carga de trabajo y retrasar temporalmente el acceso a la tabla subyacente.  
  
 OFF  
 Los bloqueos de tabla se aplican durante la operación de índice. Una operación de índice sin conexión para crear, volver a crear o quitar un índice clúster, o para volver a crear o quitar un índice no clúster, adquiere un bloqueo de modificación del esquema (Sch-M) de la tabla. Esto evita que todos los usuarios tengan acceso a la tabla subyacente durante la operación. Una operación de índice sin conexión que crea un índice no clúster adquiere un bloqueo compartido (S) en la tabla. Esto evita que se realicen actualizaciones en la tabla subyacente, pero permite la realización de operaciones de lectura, como instrucciones SELECT. Se permiten operaciones multiproceso de regeneración del montón.  
  
 Para obtener más información, consulte [cómo funcionan de las operaciones de índice en línea](../../relational-databases/indexes/how-online-index-operations-work.md).  
  
> [!NOTE]  
>  Las operaciones de índices en línea no están disponibles en todas las ediciones de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Para obtener más información, consulte [ediciones y características admitidas en SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 Mover a { *partition_scheme_name***(***column_name* [1**,** ...  *n* ] **)** | *archivos* | **"**predeterminado**"**  }  
 **Se aplica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Especifica una ubicación a la que mover las filas de datos que se encuentran en el nivel hoja del índice clúster. La tabla se mueve a la nueva ubicación. Esta opción solo se aplica a las restricciones que crean un índice clúster.  
  
> [!NOTE]  
>  En este contexto, el valor predeterminado no es una palabra clave. Es un identificador para el grupo de archivos predeterminado y debe delimitarse, como en MOVE TO **"**predeterminado**"** o en MOVE TO **[**predeterminado**]**. Si **"**predeterminado**"** se especifica, la opción QUOTED_IDENTIFIER debe ser ON para la sesión actual. Esta es la configuración predeterminada. Para obtener más información, vea [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md).  
  
 { CHECK | NOCHECK } CONSTRAINT  
 Especifica que *constraint_name* está habilitada o deshabilitada. Esta opción solo se puede utilizar con las restricciones FOREIGN KEY y CHECK. Cuando se especifica NOCHECK, la restricción se deshabilita y las posteriores inserciones o actualizaciones de la columna no se validan con las condiciones de la restricción. Las restricciones DEFAULT, PRIMARY KEY y UNIQUE no se pueden deshabilitar.  
  
 ALL  
 Especifica que todas las restricciones están deshabilitadas con la opción NOCHECK o habilitadas con la opción CHECK.  
  
 { ENABLE | DISABLE } TRIGGER  
 Especifica que *trigger_name* está habilitada o deshabilitada. Aunque un desencadenador esté deshabilitado, sigue estando definido para la tabla; sin embargo, si se ejecutan las instrucciones INSERT, UPDATE o DELETE en la tabla, las acciones del desencadenador no se ejecutan hasta que este se vuelva a habilitar.  
  
 ALL  
 Especifica si todos los desencadenadores de la tabla están habilitados o deshabilitados.  
  
 *trigger_name*  
 Especifica el nombre del desencadenador que se va a habilitar o deshabilitar.  
  
 { ENABLE | DISABLE } CHANGE_TRACKING  
 **Se aplica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Especifica si el seguimiento de cambios está habilitado o deshabilitado para la tabla. El seguimiento de cambios está deshabilitado de manera predeterminada.  
  
 Esta opción solo está disponible cuando el seguimiento de cambios está habilitado para la base de datos. Para obtener más información, vea [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md).  
  
 Para habilitar el seguimiento de cambios, la tabla debe tener una clave principal.  
  
 CON **(** TRACK_COLUMNS_UPDATED  **=**  {ON | **OFF** } **)**  
 **Se aplica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Especifica si [!INCLUDE[ssDE](../../includes/ssde-md.md)] realiza el seguimiento de las columnas sometidas a seguimiento de cambios que se actualizaron. El valor predeterminado es OFF.  
  
 CONMUTADOR [partición *source_partition_number_expression* ] para [ *schema_name***.** ] *target_table* [partición *target_partition_number_expression* ]  
 **Se aplica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Modifica un bloqueo de datos de una de las formas siguientes:  
  
-   Vuelve a asignar todos los datos de una tabla como una partición en una tabla con particiones ya existente.  
  
-   Modifica una partición de una tabla con particiones a otra.  
  
-   Vuelve a asignar todos los datos de una partición de una tabla con particiones a una tabla sin particiones ya existente.  
  
Si *tabla* es una tabla con particiones, *source_partition_number_expression* debe especificarse. Si *target_table* tiene particiones, *target_partition_number_expression* debe especificarse. Si se vuelven a asignar los datos de una tabla como partición a una tabla con particiones ya existente, o se modifica una partición de una tabla con particiones a otra, la partición de destino debe existir y debe estar vacía.  
  
 Si se vuelven a asignar los datos de una partición para formar una sola tabla, la tabla de destino debe ya estar creada y vacía. Tanto la tabla o partición de origen como la tabla o partición de destino deben residir en el mismo grupo de archivos. Los índices correspondientes, o particiones de índice, también deben residir en el mismo grupo de archivos. Son muchas las restricciones adicionales que se aplican a las particiones que se modifican. *tabla* y *target_table* no puede ser el mismo. *target_table* puede ser un identificador formado por varias partes.  
  
 *source_partition_number_expression* y *target_partition_number_expression* son expresiones constantes que pueden hacer referencia a las funciones y variables. Incluyen las variables de tipos definidos por el usuario y las funciones definidas por el usuario. No pueden hacer referencia a expresiones de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Una tabla con particiones con un índice agrupado de almacenamiento en clúster se comporta como un montón con particiones:  
  
-   La clave principal debe incluir la clave de partición.  
  
-   Un índice único debe incluir la clave de partición.  Tenga en cuenta que la incluida la clave de partición para un índice único existente puede cambiar la unicidad.  
  
-   Para dividir las particiones, todos los índices no clúster deben incluir la clave de partición.  
  
Para **conmutador** restricción al utilizar la replicación, vea [replicar Partitioned Tables and Indexes](../../relational-databases/replication/publish/replicate-partitioned-tables-and-indexes.md).  
  
 Los índices no agrupados compilados para [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 CTP1 y para la base de datos de SQL antes de que la versión V12 estaban en un formato de solo lectura. Los índices no agrupados se deben volver a generar al formato actual (que es actualizable) para poder realizar cualquier operación de partición.  
  
 ESTABLECER **(** FILESTREAM_ON = { *partition_scheme_name* | *filestream_filegroup_name* |         **"** valor predeterminado**"** | **"**NULL**"** }**)**  
 **Se aplica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. |  
  
 Especifica dónde se almacenan los datos FILESTREAM.  
  
 La ejecución de ALTER TABLE con la cláusula SET FILESTREAM_ON será correcta únicamente si la tabla no tiene columnas FILESTREAM. Las columnas FILESTREAM se pueden agregar utilizando una segunda instrucción ALTER TABLE.  
  
 Si *partition_scheme_name* se especifica, las reglas de [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) aplicar. La tabla ya debería tener particiones para los datos de la fila y su esquema de partición debe utilizar la misma función de partición y columnas que el esquema de partición de FILESTREAM.  
  
 *filestream_filegroup_name* especifica el nombre de un grupo de archivos FILESTREAM. El grupo de archivos debe tener un archivo que se define para el grupo de archivos mediante el uso de un [CREATE DATABASE](../../t-sql/statements/create-database-sql-server-transact-sql.md) o [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md) se genera la instrucción o un error.  
  
 **"**predeterminado**"** especifica el grupo de archivos FILESTREAM con la propiedad DEFAULT establecida. Si no hay ningún grupo de archivos FILESTREAM, se produce un error.  
  
 **"**NULL**"** especifica que se quitarán todas las referencias a grupos de archivos FILESTREAM para la tabla. Se deben quitar primero todas las columnas FILESTREAM. Debe usar SET FILESTREAM_ON**= "**NULL**"** para eliminar todos los datos FILESTREAM que están asociados a una tabla.  
  
 ESTABLECER **(** SYSTEM_VERSIONING  **=**  {OFF | ON [(HISTORY_TABLE = schema_name. nombre_de_tabla_de_historial [, DATA_CONSISTENCY_CHECK = { **ON** | DESACTIVADO}])]} **)**  
 **Se aplica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Deshabilita las versiones de sistema de una tabla o permite el control de versiones de sistema de una tabla. Para habilitar el control de versiones de sistema de una tabla, el sistema comprueba que el tipo de datos, restricciones de nulabilidad y requisitos de la restricción de clave principal para las versiones de sistema se cumplen. Si no se utiliza el argumento HISTORY_TABLE, el sistema genera una nueva tabla de historial que coinciden con el esquema de la tabla actual, crear un vínculo entre las dos tablas y permite que el sistema registrar el historial de cada registro en la tabla actual en la tabla de historial. El nombre de esta tabla de historial será `MSSQL_TemporalHistoryFor<primary_table_object_id>`. Si el argumento HISTORY_TABLE se utiliza para crear un vínculo a y usar una tabla de historial existente, se crea el vínculo entre la tabla actual y la tabla especificada. Al crear un vínculo a una tabla de historial existente, puede realizar una comprobación de coherencia de datos. Esta comprobación de coherencia de datos garantiza que los registros existentes no se superponen. La comprobación de coherencia de datos se realiza de manera predeterminada. Para obtener más información, consulte [Temporal Tables](../../relational-databases/tables/temporal-tables.md).  
  
HISTORY_RETENTION_PERIOD = { **infinito** | número {día | DÍAS | SEMANA |  SEMANAS | MES | MESES | AÑO | AÑOS}} **se aplica a**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  

Especifica la retención finito o infinte los datos históricos de la tabla temporal. Si se omite, se supone la retención infinita.
  
 ESTABLECER **(** LOCK_ESCALATION = {AUTOMÁTICA | TABLA | DESHABILITAR} **)**  
 **Se aplica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Especifica los métodos permitidos de extensión de bloqueo para una tabla.  
  
 AUTO  
 Esta opción permite a [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] seleccionar la granularidad de la extensión de bloqueo que sea adecuada para el esquema de tabla.  
  
-   Si la tabla tiene particiones, la extensión del bloqueo se permitirá en la partición. Una vez realizada la extensión del bloqueo hasta el nivel de la partición, el bloqueo no se extenderá a la granularidad de TABLE más adelante.  
  
-   Si la tabla no tiene particiones, la extensión del bloqueo se aplicará a la granularidad de TABLE.  
  
TABLE  
 La extensión de bloqueo se aplicará a la granularidad en el nivel de tabla, independientemente de que la tabla tenga o no particiones. TABLE es el valor predeterminado.  
  
 DISABLE  
 Evita la extensión de bloqueo en la mayoría de los casos. No siempre se evitan los bloqueos de nivel de la tabla. Por ejemplo, si está examinando una tabla que no tiene ningún índice clúster en el nivel de aislamiento serializable, [!INCLUDE[ssDE](../../includes/ssde-md.md)] debe realizar un bloqueo de la tabla para proteger la integridad de los datos.  
  
 REBUILD  
 Utilice la sintaxis de REBUILD WITH para volver a generar una tabla completa que incluya todas las particiones en una tabla con particiones. Si la tabla tiene un índice clúster, la opción REBUILD vuelve a generarlo. REBUILD se puede realizar como una operación ONLINE.  
  
 Utilice la sintaxis de REBUILD PARTITION para volver a generar una partición única en una tabla con particiones.  
  
 PARTITION = ALL  
 **Se aplica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Vuelve a generar todas las particiones al cambiar los valores de compresión de la partición.  
  
 REBUILD WITH ( \<rebuild_option >)  
 Todas las opciones se aplican a una tabla con un índice clúster. Si la tabla no tiene un índice clúster, solo algunas de las opciones afectan a la estructura del montón.  
  
 Cuando no se especifica un valor de compresión específico con la operación REBUILD, se usa el valor de compresión actual de la partición. Para devolver el valor actual, consulte la **data_compression** columna en el **sys.partitions** vista de catálogo.  
  
 Para obtener una descripción completa de las opciones de recompilación, vea [index_option &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-table-index-option-transact-sql.md).  
  
 DATA_COMPRESSION  
 **Se aplica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Especifica la opción de compresión de datos para la tabla, el número de partición o el intervalo de particiones especificados. Las opciones son las siguientes:  
  
 NONE  
 No se comprimen la tabla ni las particiones especificadas. Esto no se aplica a las tablas de almacén de columnas.  
  
 ROW  
 La tabla o las particiones especificadas se comprimen utilizando la compresión de fila. Esto no se aplica a las tablas de almacén de columnas.  
  
 PAGE  
 La tabla o las particiones especificadas se comprimen utilizando la compresión de página. Esto no se aplica a las tablas de almacén de columnas.  
  
 COLUMNSTORE  
 **Se aplica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Solo se aplica a tablas de almacén de columnas. COLUMNSTORE especifica que se descomprima una partición que se comprimió con la opción COLUMNSTORE_ARCHIVE. Cuando se restauran los datos, seguirán estando comprimidos con la compresión de almacén de columnas que se usa para todas las tablas de almacén de columnas.  
  
 COLUMNSTORE_ARCHIVE  
 **Se aplica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Solo se aplica a las tablas de almacén de columnas almacenadas con un índice clúster de almacén de columnas. COLUMNSTORE_ARCHIVE comprimirá aún más la partición especificada a un tamaño mínimo. Esto se puede usar para el archivado o para otras situaciones que requieran menos almacenamiento y en las que pueda permitirse más tiempo para el almacenamiento y recuperación.  
  
 Para volver a crear varias particiones al mismo tiempo, consulte [index_option &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-table-index-option-transact-sql.md). Si la tabla no tiene un índice clúster, al cambiar la compresión de datos se vuelven a generar el montón y los índices no clúster. Para obtener más información acerca de la compresión, vea [compresión de datos](../../relational-databases/data-compression/data-compression.md).  
  
 En línea  **=**  {ON | **OFF** } \<tal como se aplica a single_partition_rebuild_option >  
 Especifica si una única partición de las tablas subyacentes y los índices asociados están disponibles para realizar consultas y modificar datos durante la operación de indización. El valor predeterminado es OFF. REBUILD se puede realizar como una operación ONLINE.  
  
 ON  
 Los bloqueos de tabla de larga duración no se mantienen durante la operación de indización. Requiere un bloqueo S en la tabla al principio de la recompilación del índice y un bloqueo Sch-M en la tabla en el extremo de la recompilación de índice en línea. Aunque ambos bloqueos son bloqueos de metadatos cortos, especialmente el bloqueo Sch-M debe esperar a que todas las transacciones de bloqueo se completen. Durante el tiempo de espera, bloqueo Sch-M bloquea las demás transacciones que esperen a este bloqueo al tener acceso a la misma tabla.  
  
> [!NOTE]  
>  La reconstrucción de índices en línea puede establecer el *low_priority_lock_wait* opciones descritas más adelante en esta sección.  
  
 OFF  
 Los bloqueos de tabla se aplican durante la operación de índice. Esto evita que todos los usuarios tengan acceso a la tabla subyacente durante la operación.  
  
 *nombredeconjuntodecolumnas* XML COLUMN_SET FOR ALL_SPARSE_COLUMNS  
 **Se aplica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Es el nombre del conjunto de columnas. Un conjunto de columnas es una representación XML sin tipo que combina todas las columnas dispersas de una tabla en una salida estructurada. No se puede agregar un conjunto de columnas a una tabla que contenga columnas dispersas. Para obtener más información sobre los conjuntos de columnas, vea [Usar conjuntos de columnas](../../relational-databases/tables/use-column-sets.md).  
  
 { ENABLE | DISABLE } FILETABLE_NAMESPACE  
 **Se aplica a**: desde [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] hasta [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Habilita o deshabilita las restricciones definidas por el sistema en un objeto FileTable. Solo se puede utilizar con un objeto FileTable.  
  
 ESTABLECER (FILETABLE_DIRECTORY = *directory_name* )  
 **Se aplica a**: desde [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] hasta [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Especifica el nombre de directorio de FileTable compatible con Windows. Este nombre debe ser único entre todos los nombres de directorio de FileTable en la base de datos. La comparación de unicidad no distingue mayúsculas de minúsculas, independientemente de la configuración de intercalación de SQL. Solo se puede utilizar con un objeto FileTable.  
```    
 SET (  
        REMOTE_DATA_ARCHIVE   
        {  
            = ON (  <table_stretch_options> )  
          | = OFF_WITHOUT_DATA_RECOVERY  
          ( MIGRATION_STATE = PAUSED ) | ( <table_stretch_options> [, ...n] )  
        } )  
```    
**Se aplica a**: [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Habilita o deshabilita Stretch Database para una tabla. Para obtener más información, vea [Stretch Database](../../sql-server/stretch-database/stretch-database.md).  
  
 **Para habilitar Stretch Database para una tabla**  
  
 Al habilitar Stretch para una tabla especificando `ON`, también tiene que especificar `MIGRATION_STATE = OUTBOUND` para empezar a migrar los datos inmediatamente, o `MIGRATION_STATE = PAUSED` para posponer la migración de datos. El valor predeterminado es `MIGRATION_STATE = OUTBOUND`. Para obtener más información sobre la habilitación de Stretch para una tabla, vea [Enable Stretch Database para una tabla](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md).  
  
 **Requisitos previos**. Antes de habilitar Stretch para una tabla, tendrá que habilitar Stretch en el servidor y en la base de datos. Para obtener más información, vea [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md).  
  
 **Permisos**. Habilitación de Stretch para una base de datos o una tabla, requiere permisos db_owner. Habilitación de Stretch para una tabla, también requiere permisos ALTER en la tabla.  
  
 **Al deshabilitar Stretch Database para una tabla**  
  
 Cuando se deshabilita Stretch para una tabla, tiene dos opciones para los datos remotos que ya se ha migrado a Azure. Para obtener más información, vea [Deshabilitar Stretch Database y recuperar datos remotos](../../sql-server/stretch-database/disable-stretch-database-and-bring-back-remote-data.md).  
  
-   Para deshabilitar Stretch para una tabla y copiar los datos remotos de la tabla de Azure en SQL Server, ejecute el siguiente comando. Este comando no se puede cancelar.  
  
    ```tsql  
ALTER TABLE \<table name>
       SET ( REMOTE_DATA_ARCHIVE ( MIGRATION_STATE = INBOUND ) ) ;  
    ```  
  
     Esta operación conlleva gastos de transferencia de datos y no se puede cancelar. Para obtener más información, consulte [Detalles de precios de Transferencias de datos](https://azure.microsoft.com/en-us/pricing/details/data-transfers/).  
  
     Una vez que todos los datos remotos se han copiado desde Azure en SQL Server, se deshabilita Stretch para la tabla.  
  
-   Para deshabilitar Stretch para una tabla y abandonar los datos remotos, ejecute el siguiente comando.  
  
    ```tsql  
ALTER TABLE \<table_name>
       SET ( REMOTE_DATA_ARCHIVE = OFF_WITHOUT_DATA_RECOVERY ( MIGRATION_STATE = PAUSED ) ) ;  
    ```  
  
 Después de deshabilitar Stretch Database para una tabla, se detiene la migración de datos y los resultados de la consulta ya no incluyen los resultados de la tabla remota.  
  
 Deshabilitar Stretch no quita la tabla remota. Si quiere eliminar la tabla remota, tiene que quitarla mediante el Portal de administración de Azure.  
  
[FILTER_PREDICATE = {null | *predicado* }]  
 **Se aplica a**: [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Opcionalmente, especifica un predicado de filtro para seleccionar las filas para migrar de una tabla que contiene datos históricos y actuales. El predicado debe llamar a una función con valores de tabla de determinista en línea. Para obtener más información, consulte [Enable Stretch Database para una tabla](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md) y [seleccionar filas para migrar mediante una función de filtro &#40; Ajuste de la base de datos &#41; ](../../sql-server/stretch-database/select-rows-to-migrate-by-using-a-filter-function-stretch-database.md).   
  
> [!IMPORTANT]  
>  Si se indica un predicado de filtro que tiene un rendimiento bajo, la migración de datos también tendrá un rendimiento bajo. Stretch Database aplica el predicado de filtro a la tabla mediante el operador CROSS APPLY.  
  
 Si no se especifica un predicado de filtro, se migrará toda la tabla.  
  
 Cuando se especifica un predicado de filtro, también tiene que especificar *MIGRATION_STATE*.  
  
 MIGRATION_STATE = {SALIENTE |  ENTRADA | EN PAUSA}  
 **Se aplica a**: [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
-   Especificar `OUTBOUND` para migrar datos de SQL Server en Azure.  
  
-   Especificar `INBOUND` para copiar el control remoto copia los datos de la tabla de Azure para SQL Server y deshabilitar Stretch para la tabla. Para obtener más información, vea [Deshabilitar Stretch Database y recuperar datos remotos](../../sql-server/stretch-database/disable-stretch-database-and-bring-back-remote-data.md).  
  
     Esta operación conlleva gastos de transferencia de datos y no se puede cancelar.  
  
-   Especificar `PAUSED` para pausar o posponer la migración de datos. Para obtener más información, consulte [pausar y reanudar la migración de datos &#40; Ajuste de la base de datos &#41; ](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md).  
  
WAIT_AT_LOW_PRIORITY  
 **Se aplica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Una recompilación de índices en línea tiene que esperar a las operaciones de bloqueo en esta tabla. **WAIT_AT_LOW_PRIORITY** indica que la operación de regeneración de índice en línea esperará bloqueos de prioridad baja, lo que permite a otras operaciones podrán continuar mientras está esperando la operación de generación de índice en línea. Si se omite la **WAIT AT LOW PRIORITY** opción es equivalente a WA`IT_AT_LOW_PRIORITY ( MAX_DURATION = 0 minutes, ABORT_AFTER_WAIT = NONE)`.  
  
 MAX_DURATION = *tiempo* [**minutos** ]  
 **Se aplica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 El tiempo de espera (valor entero especificado en minutos) que el **conmutador** o bloqueos de regeneración de índice en línea esperarán con prioridad baja al ejecutar el comando DDL. Si la operación se bloquea durante la **MAX_DURATION** tiempo, uno de los **ABORT_AFTER_WAIT** acciones se ejecutarán. **MAX_DURATION** hora es siempre en minutos y la palabra **minutos** puede omitirse.  
  
 ABORT_AFTER_WAIT = [**NONE** | **SELF** | **BLOQUEADORES** }]  
 **Se aplica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Ninguno  
 Se continúa esperando al bloqueo con prioridad normal.  
  
 SELF  
 Salida del **conmutador** o la operación de DDL de regeneración de índice en línea que se está ejecutando actualmente sin realizar ninguna acción.  
  
 BLOCKERS  
 Elimine todas las transacciones de usuario que bloqueen actualmente la **conmutador** u operación DDL de regeneración para que pueda continuar la operación de índice en línea.  
  
 Requiere **ALTER ANY CONNECTION** permiso.  
  
IF EXISTE  
 **Se aplica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a través de [versión actual](http://go.microsoft.com/fwlink/p/?LinkId=299658)) y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Quita condicionalmente la columna o la restricción solo si ya existe.  
  
## <a name="remarks"></a>Comentarios  
 Para agregar nuevas filas de datos, use [insertar](../../t-sql/statements/insert-transact-sql.md). Para quitar filas de datos, use [eliminar](../../t-sql/statements/delete-transact-sql.md) o [TRUNCATE TABLE](../../t-sql/statements/truncate-table-transact-sql.md). Para cambiar los valores de las filas existentes, utilice [actualización](../../t-sql/queries/update-transact-sql.md).  
  
 Si hubiera algún plan de ejecución en la memoria caché del procedimiento que hace referencia a la tabla, ALTER TABLE los marca para que se vuelvan a compilar en la siguiente ejecución.  
  
## <a name="changing-the-size-of-a-column"></a>Cambiar el tamaño de una columna  
 Puede cambiar la longitud, precisión o escala de una columna especificando un nuevo tamaño para el tipo de datos de columna en la cláusula ALTER COLUMN. Si hay datos en la columna, el nuevo tamaño no puede ser menor que el tamaño máximo de los datos. Además, la columna no se puede definir en un índice, a menos que la columna es una **varchar**, **nvarchar**, o **varbinary** tipo de datos y el índice no es el resultado de una clave principal restricción. Vea el ejemplo P.  
  
## <a name="locks-and-alter-table"></a>Bloqueos y ALTER TABLE  
 Los cambios especificados en ALTER TABLE se ejecutan inmediatamente. Si los cambios requieren modificaciones de las filas de la tabla, ALTER TABLE actualiza las filas. ALTER TABLE adquiere un bloqueo de modificación del esquema (SCH-M) sobre la tabla para asegurar que ninguna otra conexión haga referencia ni a los metadatos de la tabla durante el cambio, excepto las operaciones de indización en línea que precisen un breve bloqueo SCH-M al final. En una operación ALTER TABLE…SWITCH, el bloqueo se adquiere tanto en las tablas de origen como en las de destino. Las modificaciones realizadas en la tabla se registran y son completamente recuperables. Los cambios que afectan a todas las filas de tablas muy grandes, como quitar una columna o, en algunas ediciones de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], agregar una columna NOT NULL con un valor predeterminado, pueden tardar mucho tiempo en completarse y generan muchos registros. Estas instrucciones ALTER TABLE deben ejecutarse con el mismo cuidado que cualquier instrucción INSERT, UPDATE o DELETE que afecte a un gran número de filas.  
  
### <a name="adding-not-null-columns-as-an-online-operation"></a>Agregar columnas NOT NULL como una operación en línea  
 A partir de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Enterprise Edition, agregar una columna NOT NULL con un valor predeterminado es una operación en línea cuando el valor predeterminado es una *constante en tiempo de ejecución*. Esto significa que la operación se ha completado de forma casi instantánea, independientemente del número de filas de la tabla. Esto se debe a que las filas existentes en la tabla no se actualizan durante la operación; en su lugar, el valor predeterminado se almacena únicamente en los metadatos de la tabla y el valor se busca según sea necesario en las consultas que tienen acceso a estas filas. Este comportamiento es automático; no se requiere sintaxis adicional alguna para implementar la operación en línea aparte de la sintaxis de COLUMN ADD. Una constante de tiempo de ejecución es una expresión que genera el mismo valor en tiempo de ejecución para cada fila de la tabla independientemente de su determinismo. Por ejemplo, la expresión constante “mis datos temporales” o la función del sistema GETUTCDATETIME() son constantes de tiempo de ejecución. En cambio, las funciones NEWID() o NEWSEQUENTIALID() no son constantes de tiempo de ejecución porque se genera un valor único para cada fila de la tabla. Cuando se agrega una columna NOT NULL con un valor predeterminado que no es una constante de tiempo de ejecución, se realiza siempre sin conexión y se adquiere un bloqueo exclusivo (SCH-M) mientras dura la operación.  
  
 Mientras que las filas existentes hacen referencia al valor almacenado en los metadatos, el valor predeterminado se almacena en la fila para aquellas filas nuevas que se inserten y que no especifiquen otro valor para la columna. El valor predeterminado que se almacena en los metadatos se traslada a una fila existente cuando se actualiza la fila (aunque la columna real no se especifique en la instrucción UPDATE) o bien, si la tabla o el índice clúster se vuelve a generar.  
  
 Las columnas de tipo **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, **xml**, **texto**, **ntext**, **imagen**, **hierarchyid**, **geometry**, **geography**, o no puede UDTS de CLR Agregar una operación en línea. Una columna no se puede agregar en línea si al hacerlo provoca que el tamaño máximo posible de fila supere el límite de 8.060 bytes. En este caso, la columna se agrega como una operación sin conexión.  
  
## <a name="parallel-plan-execution"></a>Ejecutar planes paralelos  
 En [!INCLUDE[ssEnterpriseEd11](../../includes/ssenterpriseed11-md.md)] y versiones posteriores, el número de procesadores que se emplea para ejecutar una sola ALTER TABLE ADD (basada en índices) CONSTRAINT o DROP (índice clúster) CONSTRAINT instrucción viene determinada por la **grado máximo de paralelismo** configuración opción y la carga de trabajo actual. Si el [!INCLUDE[ssDE](../../includes/ssde-md.md)] detecta que el sistema está ocupado, el grado de paralelismo de la operación se reduce automáticamente antes de comenzar la ejecución de la instrucción. Puede configurar manualmente el número de procesadores que se utilizan para ejecutar la instrucción si especifica la opción MAXDOP. Para obtener más información, vea [Configure the max degree of parallelism Server Configuration Option](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md).  
  
## <a name="partitioned-tables"></a>Tablas con particiones  
 Además de realizar operaciones SWITCH que implican a tablas con particiones, ALTER TABLE puede utilizarse para cambiar el estado de las columnas, restricciones y desencadenadores de una tabla con particiones, de la misma forma que se utiliza para las tablas sin particiones. Sin embargo, esta sentencia no puede utilizarse para cambiar la forma en que se realizan las particiones de la tabla misma. Para volver a particionar una tabla con particiones, utilice [ALTER PARTITION SCHEME](../../t-sql/statements/alter-partition-scheme-transact-sql.md) y [ALTER PARTITION FUNCTION](../../t-sql/statements/alter-partition-function-transact-sql.md). Además, no puede cambiar el tipo de datos de una columna de una tabla con particiones.  
  
## <a name="restrictions-on-tables-with-schema-bound-views"></a>Realizar restricciones en tablas con vistas enlazadas a esquema  
 Las restricciones que se aplican a instrucciones ALTER TABLE en tablas con vistas enlazadas a esquema son las mismas que las restricciones que se aplican actualmente cuando se alteran tablas con un solo índice. Se permite agregar una columna. No obstante, no se permite quitar ni cambiar una columna que participa en una vista enlazada a esquema. Si la instrucción ALTER TABLE requiere la alteración de una columna que se utiliza en una vista enlazada a esquema, se produce un error en ALTER TABLE y el [!INCLUDE[ssDE](../../includes/ssde-md.md)] genera un mensaje de error. Para obtener más información acerca de los enlaces de esquema y las vistas indizadas, vea [CREATE VIEW &#40; Transact-SQL &#41; ](../../t-sql/statements/create-view-transact-sql.md).  
  
 La creación de una vista enlazada a esquema que hace referencia a las tablas no afecta a la adición ni a la eliminación de desencadenadores en las tablas base.  
  
## <a name="indexes-and-alter-table"></a>Índices y ALTER TABLE  
 Los índices creados como parte de una restricción se quitan cuando se quita la restricción. Los índices que se crearon con CREATE INDEX deben quitarse con DROP INDEX. La instrucción ALTER INDEX se puede emplear para volver a crear un índice que es parte de una definición de restricción; no es necesario quitar o agregar de nuevo la restricción con ALTER TABLE.  
  
 Todos los índices y restricciones basados en una columna deben eliminarse para que se pueda quitar la columna.  
  
 Cuando se elimina una restricción que ha creado un índice clúster, las filas de datos que se han almacenado en el nivel hoja del índice clúster se almacenan en una tabla no clúster. Puede quitar el índice clúster y mover la tabla resultante a otro grupo de archivos o esquema de partición en una sola transacción especificando la opción MOVE TO. La opción MOVE TO tiene las siguientes restricciones:  
  
-   MOVE TO no es válido para vistas indizadas o índices no clúster.  
  
-   El esquema de partición o el grupo de archivos debe existir previamente.  
  
-   Si no se especifica MOVE TO, la tabla se ubicará en el mismo esquema de partición o grupo de archivos que se definió para el índice clúster.  
  
Cuando se quita un índice agrupado, puede especificar en línea  **=**  en la opción para que la transacción DROP INDEX no bloquee las consultas y modificaciones a los datos subyacentes y los índices no clúster asociados.  
  
 En línea  **=**  ON tiene las siguientes restricciones:  
  
-   En línea  **=**  ON no es válida para los índices clúster que también estén deshabilitados. Índices deshabilitados deben quitarse con ONLINE  **=**  OFF.  
  
-   Solo un índice puede quitarse cada vez.  
  
-   En línea  **=**  ON no es válida para vistas indizadas, índices no clúster ni índices en tablas temporales locales.  
  
-   En línea  **=**  ON no es válida para los índices de almacén de columnas.  
  
Para quitar un índice clúster, se necesita un espacio temporal en disco del mismo tamaño que el del índice clúster existente. Este espacio adicional se libera en cuanto se completa la operación.  
  
> [!NOTE]  
>  Las opciones enumeradas en  *\<drop_clustered_constraint_option >* se aplican a los índices agrupados en tablas y no se puede aplicar a los índices agrupados en las vistas o índices no clúster.  
  
## <a name="replicating-schema-changes"></a>Replicar cambios de esquema  
 De forma predeterminada, cuando se ejecuta ALTER TABLE en una tabla publicada en un publicador de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], el cambio se propaga a todos los suscriptores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Esta funcionalidad tiene algunas restricciones y se puede deshabilitar. Para más información, vea [Realizar cambios de esquema en bases de datos de publicaciones](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).  
  
## <a name="data-compression"></a>Data Compression  
 En las tablas del sistema no se puede habilitar la compresión. Si la tabla es un montón, la operación de regeneración en modo ONLINE será de un solo subproceso. Utilice el modo OFFLINE para una operación de regeneración de montón de varios subprocesos. Para obtener más información acerca de la compresión de datos, vea[compresión de datos](../../relational-databases/data-compression/data-compression.md).  
  
 Para evaluar cómo afecta el cambio del estado de compresión a una tabla, índice o partición, use el procedimiento almacenado [sp_estimate_data_compression_savings](../../relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql.md) .  
  
 Las restricciones siguientes se aplican a las tablas con particiones:  
  
-   No se puede cambiar la configuración de compresión de una partición única si la tabla tiene índices no alineados.  
  
-   La instrucción ALTER TABLE \<tabla > REBUILD PARTITION... vuelve la partición especificada.  
  
-   La instrucción ALTER TABLE \<tabla > REBUILD WITH... vuelve a generar todas las particiones.  
  
## <a name="dropping-ntext-columns"></a>Quitar columnas NTEXT  
 Al quitar las columnas NTEXT, la limpieza de los datos eliminados se produce como una operación serializada en todas las filas. Esto puede requerir un tiempo sustancial. Al quitar una columna NTEXT de una tabla con un gran número de filas, actualice la columna NTEXT con el valor NULL en primer lugar y luego quite la columna. Esto puede hacerse con operaciones en paralelo y puede ser mucho más rápido.  
  
## <a name="online-index-rebuild"></a>Volver a generar índice en línea  
 Para ejecutar la instrucción DDL para regenerar el índice en línea, todas las transacciones activas de bloqueo que se ejecutan en una tabla determinada deben completarse. Cuando la regeneración de índice en línea se ejecuta, bloquea todas las nuevas transacciones que están listas para iniciar la ejecución en esta tabla. Aunque la vigencia del bloqueo para volver a generar el índice en línea es muy corta, si se espera a que las transacciones abiertas en una tabla dada se completen y se bloquean las nuevas transacciones que se inician, se podría afectar significativamente al rendimiento, produciendo un retraso o un tiempo de espera en la carga de trabajo y se limitaría mucho el acceso a la tabla base. El **WAIT_AT_LOW_PRIORITY** opción permite al DBA para administrar bloqueos S-lock y Sch-M necesarios para el índice en línea se vuelve a generar y les permite seleccionar uno de los 3 opciones. En los tres casos, si durante el tiempo de espera ( `(MAX_DURATION =n [minutes])` ) no hay actividades de bloqueo, la regeneración de índice en línea se ejecuta inmediatamente sin esperar y termina la instrucción DDL.  
  
## <a name="compatibility-support"></a>Soporte de compatibilidad  
 La instrucción ALTER TABLE solo permite nombres de tabla de dos partes (esquema.objeto). En [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], la especificación de un nombre de tabla con uno de los siguientes formatos produce el error 117 en tiempo de compilación.  
  
-   servidor.baseDeDatos.esquema.tabla  
  
-   .baseDeDatos.esquema.tabla  
  
-   ..esquema.tabla  
  
En versiones anteriores, al especificar el formato servidor.baseDeDatos.esquema.tabla se devolvía el error 4902. La especificación del formato .baseDeDatos.esquema.tabla o ..esquema.tabla se realizaba correctamente.  
  
 Para resolver el problema, quite el uso de un prefijo de 4 partes.  
  
## <a name="permissions"></a>Permissions  
 Requiere el permiso ALTER en la tabla.  
  
 Los permisos ALTER TABLE se aplican a las tablas relacionadas con una instrucción ALTER TABLE SWITCH. Los datos que se modifican heredan la seguridad de la tabla de destino.  
  
 Si se define alguna columna de la instrucción ALTER TABLE para que sea un tipo definido por el usuario de CLR (Common Language Runtime) o un tipo de datos del alias, se necesita el permiso REFERENCES sobre el tipo.  
  
 Agregar una columna que actualiza las filas de la tabla, es necesario **actualización** permiso en la tabla. Por ejemplo, al agregar un **NOT NULL** columna con un valor predeterminado o agregar una columna de identidad cuando la tabla no está vacía.  
  
##  <a name="Example_Top"></a> Ejemplos  
  
|Categoría|Elementos de sintaxis ofrecidos|  
|--------------|------------------------------|  
|[Agregar columnas y restricciones](#add)|ADD • PRIMARY KEY con opciones de índice • columnas dispersas y conjuntos de columnas •|  
|[Quitar columnas y restricciones](#Drop)|DROP|  
|[Modificar una definición de columna](#alter_column)|cambiar tipo de datos • cambiar tamaño de columna • intercalación|  
|[Modificar una definición de tabla](#alter_table)|DATA_COMPRESSION • SWITCH PARTITION • LOCK ESCALATION • seguimiento de cambios|  
|[Deshabilitar y habilitar restricciones y desencadenadores](#disable_enable)|CHECK • NO CHECK • ENABLE TRIGGER • DISABLE TRIGGER|  
  
###  <a name="add"></a>Agregar columnas y restricciones  
 En los ejemplos de esta sección se muestra cómo agregar columnas y restricciones a una tabla.  
  
#### <a name="a-adding-a-new-column"></a>A. Agregar una columna nueva  
 En el ejemplo siguiente se agrega una columna que permite valores NULL y a la que no se han proporcionado valores mediante una definición DEFAULT. En la nueva columna, cada fila tendrá valores `NULL`.  
  
```  
CREATE TABLE dbo.doc_exa (column_a INT) ;  
GO  
ALTER TABLE dbo.doc_exa ADD column_b VARCHAR(20) NULL ;  
GO  
  
```  
  
#### <a name="b-adding-a-column-with-a-constraint"></a>B. Agregar una columna con una restricción  
 En el ejemplo siguiente se agrega una nueva columna con una restricción `UNIQUE`.  
  
```  
CREATE TABLE dbo.doc_exc (column_a INT) ;  
GO  
ALTER TABLE dbo.doc_exc ADD column_b VARCHAR(20) NULL   
    CONSTRAINT exb_unique UNIQUE ;  
GO  
EXEC sp_help doc_exc ;  
GO  
DROP TABLE dbo.doc_exc ;  
GO  
```  
  
#### <a name="c-adding-an-unverified-check-constraint-to-an-existing-column"></a>C. Agregar una restricción CHECK no comprobada a una columna existente  
 En el ejemplo siguiente se agrega una restricción a una columna existente de la tabla. La columna tiene un valor que infringe la restricción. Por tanto, `WITH NOCHECK` se usa para evitar que la restricción se valide en las filas existentes y para poder agregar la restricción.  
  
```  
CREATE TABLE dbo.doc_exd ( column_a INT) ;  
GO  
INSERT INTO dbo.doc_exd VALUES (-1) ;  
GO  
ALTER TABLE dbo.doc_exd WITH NOCHECK   
ADD CONSTRAINT exd_check CHECK (column_a > 1) ;  
GO  
EXEC sp_help doc_exd ;  
GO  
DROP TABLE dbo.doc_exd ;  
GO  
```  
  
#### <a name="d-adding-a-default-constraint-to-an-existing-column"></a>D. Agregar una restricción DEFAULT a una columna existente  
 En el ejemplo siguiente se crea una tabla con dos columnas y se inserta un valor en la primera columna, y la otra columna sigue siendo NULL. A continuación se agrega una restricción `DEFAULT` a la segunda columna. Para comprobar que se aplica el valor predeterminado, se inserta otro valor en la primera columna y se consulta la tabla.  
  
```  
CREATE TABLE dbo.doc_exz ( column_a INT, column_b INT) ;  
GO  
INSERT INTO dbo.doc_exz (column_a)VALUES ( 7 ) ;  
GO  
ALTER TABLE dbo.doc_exz  
ADD CONSTRAINT col_b_def  
DEFAULT 50 FOR column_b ;  
GO  
INSERT INTO dbo.doc_exz (column_a) VALUES ( 10 ) ;  
GO  
SELECT * FROM dbo.doc_exz ;  
GO  
DROP TABLE dbo.doc_exz ;  
GO  
```  
  
#### <a name="e-adding-several-columns-with-constraints"></a>E. Agregar varias columnas con restricciones  
 En el ejemplo siguiente se agregan varias columnas con restricciones que se definen con la nueva columna. La primera columna nueva tiene una propiedad `IDENTITY`. Cada fila de la tabla tiene nuevos valores incrementales en la columna de identidad.  
  
```  
CREATE TABLE dbo.doc_exe ( column_a INT CONSTRAINT column_a_un UNIQUE) ;  
GO  
ALTER TABLE dbo.doc_exe ADD   
  
-- Add a PRIMARY KEY identity column.  
column_b INT IDENTITY  
CONSTRAINT column_b_pk PRIMARY KEY,   
  
-- Add a column that references another column in the same table.  
column_c INT NULL    
CONSTRAINT column_c_fk   
REFERENCES doc_exe(column_a),  
  
-- Add a column with a constraint to enforce that   
-- nonnull data is in a valid telephone number format.  
column_d VARCHAR(16) NULL   
CONSTRAINT column_d_chk  
CHECK   
(column_d LIKE '[0-9][0-9][0-9]-[0-9][0-9][0-9][0-9]' OR  
column_d LIKE  
'([0-9][0-9][0-9]) [0-9][0-9][0-9]-[0-9][0-9][0-9][0-9]'),  
  
-- Add a nonnull column with a default.  
column_e DECIMAL(3,3)  
CONSTRAINT column_e_default  
DEFAULT .081 ;  
GO  
EXEC sp_help doc_exe ;  
GO  
DROP TABLE dbo.doc_exe ;  
GO  
```  
  
#### <a name="f-adding-a-nullable-column-with-default-values"></a>F. Agregar una columna que admite valores NULL con valores predeterminados  
 En el ejemplo siguiente se agrega una columna que acepta valores NULL con una definición `DEFAULT` y se usa `WITH VALUES` para proporcionar valores para cada fila existente en la tabla. Si no se utiliza WITH VALUES, cada fila tiene el valor NULL en la nueva columna.  
  
```  
  
CREATE TABLE dbo.doc_exf ( column_a INT) ;  
GO  
INSERT INTO dbo.doc_exf VALUES (1) ;  
GO  
ALTER TABLE dbo.doc_exf   
ADD AddDate smalldatetime NULL  
CONSTRAINT AddDateDflt  
DEFAULT GETDATE() WITH VALUES ;  
GO  
DROP TABLE dbo.doc_exf ;  
GO  
```  
  
#### <a name="g-creating-a-primary-key-constraint-with-index-options"></a>G. Crear una restricción PRIMARY KEY con opciones de índice  
 En el ejemplo siguiente se crea la restricción PRIMARY KEY `PK_TransactionHistoryArchive_TransactionID` y se establecen las opciones `FILLFACTOR`, `ONLINE` y `PAD_INDEX`. El índice clúster resultante tendrá el mismo nombre que la restricción.  
  
**Se aplica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
```  
USE AdventureWorks2012;  
GO  
ALTER TABLE Production.TransactionHistoryArchive WITH NOCHECK   
ADD CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY CLUSTERED (TransactionID)  
WITH (FILLFACTOR = 75, ONLINE = ON, PAD_INDEX = ON);  
GO  
```  
  
#### <a name="h-adding-a-sparse-column"></a>H. Agregar una columna dispersa  
 En los ejemplos siguientes se muestra cómo agregar y modificar columnas dispersas en la tabla T1. El código para crear la tabla `T1` es el siguiente.  
  
```  
CREATE TABLE T1  
(C1 int PRIMARY KEY,  
C2 varchar(50) SPARSE NULL,  
C3 int SPARSE NULL,  
C4 int ) ;  
GO  
```  
  
 Para agregar una columna dispersa adicional `C5`, ejecute la instrucción siguiente.  
  
```  
ALTER TABLE T1  
ADD C5 char(100) SPARSE NULL ;  
GO  
```  
  
 Para convertir la columna no dispersa `C4` en una columna dispersa, ejecute la instrucción siguiente.  
  
```  
ALTER TABLE T1  
ALTER COLUMN C4 ADD SPARSE ;  
GO  
```  
  
 Para convertir el `C4` columnas dispersas para una columna no dispersa, ejecute la instrucción siguiente.  
  
```  
ALTER TABLE T1  
ALTER COLUMN C4 DROP SPARSE;  
GO  
```  
  
#### <a name="i-adding-a-column-set"></a>I. Agregar un conjunto de columnas  
 En los ejemplos siguientes se muestra cómo agregar una columna a la tabla `T2`. No se puede agregar un conjunto de columnas a una tabla si esta ya contiene columnas dispersas. El código para crear la tabla `T2` es el siguiente.  
  
```  
CREATE TABLE T2  
(C1 int PRIMARY KEY,  
C2 varchar(50) NULL,  
C3 int NULL,  
C4 int ) ;  
GO  
```  
  
 Las tres instrucciones siguientes agregan un conjunto de columnas denominado `CS` y, a continuación, modifican las columnas `C2` y `C3` a `SPARSE`.  
  
```  
ALTER TABLE T2  
ADD CS XML COLUMN_SET FOR ALL_SPARSE_COLUMNS ;  
GO  
  
ALTER TABLE T2  
ALTER COLUMN C2 ADD SPARSE ;   
GO  
  
ALTER TABLE T2  
ALTER COLUMN C3 ADD SPARSE ;  
GO  
```  
  
#### <a name="j-adding-an-encrypted-column"></a>J. Agregar una columna cifrada  
 La siguiente instrucción agrega una columna cifrada con el nombre `PromotionCode`.  
  
```  
ALTER TABLE Customers ADD  
    PromotionCode nvarchar(100)   
    ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = MyCEK,  
    ENCRYPTION_TYPE = RANDOMIZED,  
    ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') ;  
```  
  
###  <a name="Drop"></a>Quitar columnas y restricciones  
 En los ejemplos de esta sección se muestra cómo quitar columnas y restricciones.  
  
#### <a name="a-dropping-a-column-or-columns"></a>A. Quitar una o varias columnas  
 En el primer ejemplo se modifica una tabla para quitar una columna. En el segundo ejemplo se quitan varias columnas.  
  
```  
CREATE TABLE dbo.doc_exb   
    (column_a INT  
     ,column_b VARCHAR(20) NULL  
     ,column_c datetime  
     ,column_d int) ;  
GO  
-- Remove a single column.  
ALTER TABLE dbo.doc_exb DROP COLUMN column_b ;  
GO  
-- Remove multiple columns.  
ALTER TABLE dbo.doc_exb DROP COLUMN column_c, column_d;  
  
```  
  
#### <a name="b-dropping-constraints-and-columns"></a>B. Quitar restricciones y columnas  
 En el primer ejemplo se quita una restricción `UNIQUE` de una tabla. En el segundo ejemplo se quitan dos restricciones y una sola columna.  
  
```  
CREATE TABLE dbo.doc_exc ( column_a int NOT NULL CONSTRAINT my_constraint UNIQUE) ;  
GO  
  
-- Example 1. Remove a single constraint.  
ALTER TABLE dbo.doc_exc DROP my_constraint ;  
GO  
  
DROP TABLE dbo.doc_exc;  
GO  
  
CREATE TABLE dbo.doc_exc ( column_a int    
                          NOT NULL CONSTRAINT my_constraint UNIQUE  
                          ,column_b int   
                          NOT NULL CONSTRAINT my_pk_constraint PRIMARY KEY) ;  
GO  
  
-- Example 2. Remove two constraints and one column  
-- The keyword CONSTRAINT is optional. The keyword COLUMN is required.  
ALTER TABLE dbo.doc_exc   
  
    DROP CONSTRAINT CONSTRAINT my_constraint, my_pk_constraint, COLUMN column_b ;  
GO  
  
```  
  
#### <a name="c-dropping-a-primary-key-constraint-in-the-online-mode"></a>C. Quitar una restricción PRIMARY KEY en modo ONLINE  
 En el ejemplo siguiente se elimina una restricción KEY PRIMARY con la opción `ONLINE` establecida en `ON`.  
  
```  
  
ALTER TABLE Production.TransactionHistoryArchive  
DROP CONSTRAINT PK_TransactionHistoryArchive_TransactionID  
WITH (ONLINE = ON);  
GO  
```  
  
#### <a name="d-adding-and-dropping-a-foreign-key-constraint"></a>D. Agregar y quitar una restricción FOREIGN KEY  
 En el ejemplo siguiente se crea la tabla `ContactBackup` y, a continuación, se modifica la tabla; primero se agrega una restricción `FOREIGN KEY` que hace referencia a la tabla `Person.Person` y, a continuación, se quita la restricción `FOREIGN KEY`.  
  
```  
CREATE TABLE Person.ContactBackup  
    (ContactID int) ;  
GO  
  
ALTER TABLE Person.ContactBackup  
ADD CONSTRAINT FK_ContactBacup_Contact FOREIGN KEY (ContactID)  
    REFERENCES Person.Person (BusinessEntityID) ;  
GO  
  
ALTER TABLE Person.ContactBackup  
DROP CONSTRAINT FK_ContactBacup_Contact ;  
GO  
  
DROP TABLE Person.ContactBackup ;  
```  
  
 ![Icono de flecha usado con Back vínculo al principio](../../analysis-services/instances/media/uparrow16x16.gif "icono de flecha usado con Back vínculo al principio") [ejemplos](#Example_Top)  
  
###  <a name="alter_column"></a>Modificar una definición de columna  
  
#### <a name="a-changing-the-data-type-of-a-column"></a>A. Cambiar el tipo de datos de una columna  
 En el ejemplo siguiente se modifica una columna de una tabla de `INT` a `DECIMAL`.  
  
```  
CREATE TABLE dbo.doc_exy (column_a INT ) ;  
GO  
INSERT INTO dbo.doc_exy (column_a) VALUES (10) ;  
GO  
ALTER TABLE dbo.doc_exy ALTER COLUMN column_a DECIMAL (5, 2) ;  
GO  
DROP TABLE dbo.doc_exy ;  
GO  
```  
  
#### <a name="b-changing-the-size-of-a-column"></a>B. Cambiar el tamaño de una columna  
 El ejemplo siguiente aumenta el tamaño de un **varchar** columna y la precisión y escala de un **decimal** columna. Dado que las columnas contienen datos, solo se puede aumentar el tamaño de columna. Observe también que `col_a` se define en un índice único. El tamaño de `col_a` aún se puede aumentar porque el tipo de datos es un **varchar** y el índice no es el resultado de una restricción PRIMARY KEY.  
  
```  
-- Create a two-column table with a unique index on the varchar column.  
CREATE TABLE dbo.doc_exy ( col_a varchar(5) UNIQUE NOT NULL, col_b decimal (4,2));  
GO  
INSERT INTO dbo.doc_exy VALUES ('Test', 99.99);  
GO  
-- Verify the current column size.  
SELECT name, TYPE_NAME(system_type_id), max_length, precision, scale  
FROM sys.columns WHERE object_id = OBJECT_ID(N'dbo.doc_exy');  
GO  
-- Increase the size of the varchar column.  
ALTER TABLE dbo.doc_exy ALTER COLUMN col_a varchar(25);  
GO  
-- Increase the scale and precision of the decimal column.  
ALTER TABLE dbo.doc_exy ALTER COLUMN col_b decimal (10,4);  
GO  
-- Insert a new row.  
INSERT INTO dbo.doc_exy VALUES ('MyNewColumnSize', 99999.9999) ;  
GO  
-- Verify the current column size.  
SELECT name, TYPE_NAME(system_type_id), max_length, precision, scale  
FROM sys.columns WHERE object_id = OBJECT_ID(N'dbo.doc_exy');  
```  
  
#### <a name="c-changing-column-collation"></a>C. Cambiar la intercalación de columnas  
 En el siguiente ejemplo se muestra cómo cambiar la intercalación de una columna. Primero se crea una tabla con la intercalación predeterminada del usuario.  
  
```  
CREATE TABLE T3  
(C1 int PRIMARY KEY,  
C2 varchar(50) NULL,  
C3 int NULL,  
C4 int ) ;  
GO  
```  
  
 Después, la intercalación de la columna `C2` se cambia a Latin1_General_BIN. Observe que el tipo de datos se requiere, incluso aunque no se cambie.  
  
```  
ALTER TABLE T3  
ALTER COLUMN C2 varchar(50) COLLATE Latin1_General_BIN;  
GO  
  
```  

  
###  <a name="alter_table"></a>Modificar una definición de tabla  
 En los ejemplos de esta sección se muestra cómo modificar la definición de una tabla.  
  
#### <a name="a-modifying-a-table-to-change-the-compression"></a>A. Modificar una tabla para cambiar la compresión  
 En el ejemplo siguiente se cambia la compresión de una tabla sin particiones. Se volverá a generar el montón o el índice clúster. Si la tabla es un montón, se volverán a generar todos los índices no clúster.  
  
```  
ALTER TABLE T1   
REBUILD WITH (DATA_COMPRESSION = PAGE);  
```  
  
 En el ejemplo siguiente se cambia la compresión de una tabla con particiones. La sintaxis `REBUILD PARTITION = 1` hace que solo se vuelva a generar la partición número `1`.  
  
**Se aplica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
```  
ALTER TABLE PartitionTable1   
REBUILD PARTITION = 1 WITH (DATA_COMPRESSION =  NONE) ;  
GO  
```  
  
La misma operación que utiliza la sintaxis alternativa siguiente hace que se vuelvan a generar todas las particiones de la tabla.  
  
**Se aplica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
```  
ALTER TABLE PartitionTable1   
REBUILD PARTITION = ALL   
WITH (DATA_COMPRESSION = PAGE ON PARTITIONS(1) ) ;  
```  
  
 Para obtener ejemplos de compresión de datos adicionales, consulte [compresión de datos](../../relational-databases/data-compression/data-compression.md).  
  
#### <a name="b-modifying-a-columnstore-table-to-change-archival-compression"></a>B. Modificar una tabla de almacén de columnas para cambiar la compresión de archivo  
 En el ejemplo siguiente se comprime aún más una partición de tabla de almacén de columnas aplicando un algoritmo de compresión adicional. Esto reduce la tabla a un tamaño mínimo, pero también aumenta el tiempo necesario para el almacenamiento y la recuperación. Esto resulta útil para el archivado o para otras situaciones que requieran menos espacio y en las que pueda permitirse más tiempo para el almacenamiento y recuperación.  
  
**Se aplica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
```  
ALTER TABLE PartitionTable1   
REBUILD PARTITION = 1 WITH (DATA_COMPRESSION =  COLUMNSTORE_ARCHIVE) ;  
GO  
```  
  
En el siguiente ejemplo se descomprime una partición de tabla de almacén de columnas que se comprimió con la opción COLUMNSTORE_ARCHIVE. Cuando se restauran los datos, seguirán estando comprimidos con la compresión de almacén de columnas que se usa para todas las tablas de almacén de columnas.  
  
**Se aplica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
```  
ALTER TABLE PartitionTable1   
REBUILD PARTITION = 1 WITH (DATA_COMPRESSION =  COLUMNSTORE) ;  
GO  
```  
  
#### <a name="c-switching-partitions-between-tables"></a>C. Cambiar las particiones entre tablas  
 En el ejemplo siguiente se crea una tabla con particiones, suponiendo que el esquema de partición `myRangePS1` ya esté creado en la base de datos. A continuación, se crea una tabla sin particiones con la misma estructura que la tabla con particiones y en el mismo grupo de archivos que `PARTITION 2` de la tabla `PartitionTable`. Los datos de `PARTITION 2` de la tabla `PartitionTable` se cambian entonces a la tabla `NonPartitionTable`.  
  
```  
CREATE TABLE PartitionTable (col1 int, col2 char(10))  
ON myRangePS1 (col1) ;  
GO  
CREATE TABLE NonPartitionTable (col1 int, col2 char(10))  
ON test2fg ;  
GO  
ALTER TABLE PartitionTable SWITCH PARTITION 2 TO NonPartitionTable ;  
GO  
```  
  
#### <a name="d-allowing-lock-escalation-on-partitioned-tables"></a>D. Permitir la extensión de bloqueo en tablas con particiones  
 En el ejemplo siguiente se habilita la extensión de bloqueo al nivel de partición en una tabla con particiones. Si la tabla no tiene particiones, la extensión de bloqueo se establece en el nivel TABLE.  
  
**Se aplica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
```  
ALTER TABLE dbo.T1 SET (LOCK_ESCALATION = AUTO);  
GO  
```  
  
#### <a name="e-configuring-change-tracking-on-a-table"></a>E. Configurar el seguimiento de cambios en una tabla  
 En el ejemplo siguiente se habilita el seguimiento de cambios en la tabla `Person.Person`.  
  
**Se aplica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
```  
USE AdventureWorks2012;  
ALTER TABLE Person.Person  
ENABLE CHANGE_TRACKING;  
```  
  
El ejemplo siguiente habilita el seguimiento de cambios y el seguimiento de las columnas que se actualizan durante un cambio.  
  
**Se aplica a**: desde [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] hasta [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
USE AdventureWorks2012;  
GO  
ALTER TABLE Person.Person  
ENABLE CHANGE_TRACKING  
WITH (TRACK_COLUMNS_UPDATED = ON)  
```  
  
En el ejemplo siguiente se deshabilita el seguimiento de cambios en la tabla `Person.Person`.  
  
**Se aplica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
```  
USE AdventureWorks2012;  
Go  
ALTER TABLE Person.Person  
DISABLE CHANGE_TRACKING;  
```  

  
###  <a name="disable_enable"></a>Deshabilitar y habilitar restricciones y desencadenadores  
  
#### <a name="a-disabling-and-re-enabling-a-constraint"></a>A. Deshabilitar y volver a habilitar una restricción  
 En el ejemplo siguiente se deshabilita una restricción que limita los salarios aceptados en los datos. `NOCHECK CONSTRAINT` se usa con `ALTER TABLE` para deshabilitar la restricción y permitir una inserción que normalmente infringiría la restricción. `CHECK CONSTRAINT` vuelve a habilitar la restricción.  
  
```  
CREATE TABLE dbo.cnst_example   
(id INT NOT NULL,  
 name VARCHAR(10) NOT NULL,  
 salary MONEY NOT NULL  
    CONSTRAINT salary_cap CHECK (salary < 100000)  
);  
  
-- Valid inserts  
INSERT INTO dbo.cnst_example VALUES (1,'Joe Brown',65000);  
INSERT INTO dbo.cnst_example VALUES (2,'Mary Smith',75000);  
  
-- This insert violates the constraint.  
INSERT INTO dbo.cnst_example VALUES (3,'Pat Jones',105000);  
  
-- Disable the constraint and try again.  
ALTER TABLE dbo.cnst_example NOCHECK CONSTRAINT salary_cap;  
INSERT INTO dbo.cnst_example VALUES (3,'Pat Jones',105000);  
  
-- Re-enable the constraint and try another insert; this will fail.  
ALTER TABLE dbo.cnst_example CHECK CONSTRAINT salary_cap;  
INSERT INTO dbo.cnst_example VALUES (4,'Eric James',110000) ;  
```  
  
#### <a name="b-disabling-and-re-enabling-a-trigger"></a>B. Deshabilitar y volver a habilitar un desencadenador  
 En el ejemplo siguiente se usa la opción `DISABLE TRIGGER` de `ALTER TABLE` para deshabilitar el desencadenador y permitir una inserción que normalmente infringiría el desencadenador. Después se usa `ENABLE TRIGGER` para volver a habilitar el desencadenador.  
  
```  
CREATE TABLE dbo.trig_example   
(id INT,   
name VARCHAR(12),  
salary MONEY) ;  
GO  
-- Create the trigger.  
CREATE TRIGGER dbo.trig1 ON dbo.trig_example FOR INSERT  
AS  
IF (SELECT COUNT(*) FROM INSERTED  
WHERE salary > 100000) > 0  
BEGIN  
    print 'TRIG1 Error: you attempted to insert a salary > $100,000'  
    ROLLBACK TRANSACTION  
END ;  
GO  
-- Try an insert that violates the trigger.  
INSERT INTO dbo.trig_example VALUES (1,'Pat Smith',100001) ;  
GO  
-- Disable the trigger.  
ALTER TABLE dbo.trig_example DISABLE TRIGGER trig1 ;  
GO  
-- Try an insert that would typically violate the trigger.  
INSERT INTO dbo.trig_example VALUES (2,'Chuck Jones',100001) ;  
GO  
-- Re-enable the trigger.  
ALTER TABLE dbo.trig_example ENABLE TRIGGER trig1 ;  
GO  
-- Try an insert that violates the trigger.  
INSERT INTO dbo.trig_example VALUES (3,'Mary Booth',100001) ;  
GO  
```  
 
  
### <a name="online-operations"></a>Operaciones en línea  
  
#### <a name="a-online-index-rebuild-using-low-priority-wait-options"></a>A. Volver a generar el índice en línea mediante opciones de espera de prioridad baja  
 En el ejemplo siguiente se muestra cómo realizar una regeneración de índice en línea que especifica las opciones de espera de prioridad baja.  
  
**Se aplica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
```  
ALTER TABLE T1   
REBUILD WITH   
(  
    PAD_INDEX = ON,  
    ONLINE = ON ( WAIT_AT_LOW_PRIORITY ( MAX_DURATION = 4 MINUTES, 
                                         ABORT_AFTER_WAIT = BLOCKERS ) )  
)  
;  
```  
  
#### <a name="b-online-alter-column"></a>B. Alteración de columna en línea  
 En el ejemplo siguiente se muestra cómo realizar una operación de alteración de columna con la opción ONLINE.  
  
**Se aplica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
```  
CREATE TABLE dbo.doc_exy (column_a INT ) ;  
GO  
INSERT INTO dbo.doc_exy (column_a) VALUES (10) ;  
GO  
ALTER TABLE dbo.doc_exy   
    ALTER COLUMN column_a DECIMAL (5, 2) WITH (ONLINE = ON);  
GO  
sp_help doc_exy;  
DROP TABLE dbo.doc_exy ;  
GO  
```  
  
##  <a name="system_versioning"></a>Control de versiones de sistema  
 Los cuatro ejemplos siguientes le ayudará a familiarizarse con la sintaxis para usar el control de versiones del sistema. Para obtener asistencia adicional, consulte [Introducción a las tablas temporales con versión del sistema](../../relational-databases/tables/getting-started-with-system-versioned-temporal-tables.md).  
  
**Se aplica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a través de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
### <a name="a-add-system-versioning-to-existing-tables"></a>A. Control de versiones del sistema a las tablas existentes  
 En el ejemplo siguiente se muestra cómo agregar el control de versiones de sistema a una tabla existente y crear una tabla de historial futuras. En este ejemplo se supone que hay una tabla existente denominada `InsurancePolicy` con una clave principal definida. Este ejemplo rellena las columnas de período recién creadas para las versiones de sistema utilizando los valores predeterminados para los tiempos de inicio y finalización porque estos valores no pueden ser null. Este ejemplo utiliza la cláusula HIDDEN para no asegurarse de ningún impacto en las aplicaciones existentes que interactúan con la tabla actual.  También usa HISTORY_RETENTION_PERIOD que está disponible en [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] solo. 
  
```  
--Alter non-temporal table to define periods for system versioning  
ALTER TABLE InsurancePolicy  
ADD PERIOD FOR SYSTEM_TIME (SysStartTime, SysEndTime),   
SysStartTime datetime2 GENERATED ALWAYS AS ROW START HIDDEN NOT NULL 
    DEFAULT GETUTCDATE(),   
SysEndTime datetime2 GENERATED ALWAYS AS ROW END HIDDEN NOT NULL 
    DEFAULT CONVERT(DATETIME2, '9999-12-31 23:59:59.99999999');  
--Enable system versioning with 1 year retention for historical data
ALTER TABLE InsurancePolicy 
SET (SYSTEM_VERSIONING = ON (HISTORY_RETENTION_PERIOD = 1 YEAR));  
```  
  
### <a name="b-migrate-an-existing-solution-to-use-system-versioning"></a>B. Migrar una solución existente para usar las versiones de sistema  
 En el ejemplo siguiente se muestra cómo migrar a las versiones del sistema desde una solución que utiliza desencadenadores para imitar una compatibilidad temporal. En el ejemplo se da por supuesto que hay una solución existente que usa un `ProjectTaskCurrent` tabla y un `ProjectTaskHistory` columnas de tabla para su solución existente, que utiliza la fecha de modificación y fecha de revisión para sus períodos, que estas columnas de periodo no usan el tipo de datos datetime2 y que la `ProjectTaskCurrent` tabla tiene definida una clave principal.  
  
```  
-- Drop existing trigger  
DROP TRIGGER ProjectTaskCurrent_Trigger;  
-- Adjust the schema for current and history table  
-- Change data types for existing period columns  
ALTER TABLE ProjectTaskCurrent ALTER COLUMN [Changed Date] datetime2 NOT NULL;  
ALTER TABLE ProjectTaskCurrent ALTER COLUMN [Revised Date] datetime2 NOT NULL;  
  
ALTER TABLE ProjectTaskHistory ALTER COLUMN [Changed Date] datetime2 NOT NULL;  
ALTER TABLE ProjectTaskHistory ALTER COLUMN [Revised Date] datetime2 NOT NULL;  
  
-- Add SYSTEM_TIME period and set system versioning with linking two existing tables  
-- (a certain set of data checks happen in the background)  
ALTER TABLE ProjectTaskCurrent  
ADD PERIOD FOR SYSTEM_TIME ([Changed Date], [Revised Date])  
  
ALTER TABLE ProjectTaskCurrent  
SET (SYSTEM_VERSIONING = ON (HISTORY_TABLE = dbo.ProjectTaskHistory, DATA_CONSISTENCY_CHECK = ON))  
```  
  
### <a name="c-disabling-and-re-enabling-system-versioning-to-change-table-schema"></a>C. Deshabilitar y volver a habilitar el control de versiones del sistema para cambiar el esquema de tabla  
 Este ejemplo muestra cómo deshabilitar el control de versiones de sistema en el `Department` de tabla, agregar una columna y volver a habilitar el control de versiones de sistema. Deshabilitar el control de versiones de sistema es necesario para modificar el esquema de tabla. Siga estos pasos en una transacción para impedir las actualizaciones al actualizar el esquema de tabla, lo que permite al DBA para omitir la coherencia de datos comprueba al volver a habilitar el control de versiones de sistema y obtener un rendimiento beneficiarse de ambas tablas. Tenga en cuenta que no requieren tareas como la creación de estadísticas, la conmutación de particiones o aplicar compresión a tablas de uno o ambos, al deshabilitar el control de versiones de sistema.  
  
```  
BEGIN TRAN  
/* Takes schema lock on both tables */  
ALTER TABLE Department  
    SET (SYSTEM_VERSIONING = OFF);  
/* expand table schema for temporal table */  
ALTER TABLE Department  
     ADD Col5 int NOT NULL DEFAULT 0;  
/* Expand table schema for history table */  
ALTER TABLE DepartmentHistory  
    ADD Col5 int NOT NULL DEFAULT 0;  
/* Re-establish versioning again  */
ALTER TABLE Department  
    SET (SYSTEM_VERSIONING = ON (HISTORY_TABLE=dbo.DepartmentHistory, 
                                 DATA_CONSISTENCY_CHECK = OFF));  
COMMIT   
```  
  
### <a name="d-removing-system-versioning"></a>D. Quitar las versiones del sistema  
 Este ejemplo muestra cómo quitar completamente el control de versiones de sistema de la tabla de departamento y colocar el `DepartmentHistory` tabla. Si lo desea, también puede quitar las columnas de periodo utilizadas por el sistema para registrar información de control de versiones del sistema. Tenga en cuenta que no se puede quitar cualquiera el `Department` o `DepartmentHistory` tablas mientras esté habilitado el control de versiones del sistema.  
  
```  
ALTER TABLE Department  
    SET (SYSTEM_VERSIONING = OFF);  
ALTER TABLE Department  
DROP PEROD FOR SYSTEM_TIME;  
DROP TABLE DepartmentHistory;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Ejemplos: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] y[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Los ejemplos siguientes A través de C usan la tabla FactResellerSales en la [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)] base de datos.  
  
### <a name="e-determining-if-a-table-is-partitioned"></a>E. Determinar si una tabla tiene particiones  
 La consulta siguiente devuelve una o más filas si la tabla tiene particiones `FactResellerSales` . Si la tabla no tiene particiones, no se devuelve ninguna fila.  
  
```  
SELECT * FROM sys.partitions AS p  
JOIN sys.tables AS t  
    ON  p.object_id = t.object_id  
WHERE p.partition_id IS NOT NULL  
    AND t.name = 'FactResellerSales';  
```  
  
### <a name="f-determining-boundary-values-for-a-partitioned-table"></a>F. Determine los valores de límite de una tabla con particiones  
 La consulta siguiente devuelve los valores de límite para cada partición de la tabla `FactResellerSales` .  
  
```  
SELECT t.name AS TableName, i.name AS IndexName, p.partition_number, 
    p.partition_id, i.data_space_id, f.function_id, f.type_desc, 
    r.boundary_id, r.value AS BoundaryValue   
FROM sys.tables AS t  
JOIN sys.indexes AS i  
    ON t.object_id = i.object_id  
JOIN sys.partitions AS p  
    ON i.object_id = p.object_id AND i.index_id = p.index_id   
JOIN  sys.partition_schemes AS s   
    ON i.data_space_id = s.data_space_id  
JOIN sys.partition_functions AS f   
    ON s.function_id = f.function_id  
LEFT JOIN sys.partition_range_values AS r   
    ON f.function_id = r.function_id and r.boundary_id = p.partition_number  
WHERE t.name = 'FactResellerSales' AND i.type <= 1  
ORDER BY p.partition_number;  
```  
  
### <a name="g-determining-the-partition-column-for-a-partitioned-table"></a>G. Determinar la columna de partición de una tabla con particiones  
 La consulta siguiente devuelve el nombre de la columna de partición de la tabla. `FactResellerSales`.  
  
```  
SELECT t.object_id AS Object_ID, t.name AS TableName, 
    ic.column_id as PartitioningColumnID, c.name AS PartitioningColumnName   
FROM sys.tables AS t  
JOIN sys.indexes AS i  
    ON t.object_id = i.object_id  
JOIN sys.columns AS c  
    ON t.object_id = c.object_id  
JOIN sys.partition_schemes AS ps  
    ON ps.data_space_id = i.data_space_id  
JOIN sys.index_columns AS ic  
    ON ic.object_id = i.object_id 
    AND ic.index_id = i.index_id AND ic.partition_ordinal > 0  
WHERE t.name = 'FactResellerSales'  
AND i.type <= 1  
AND c.column_id = ic.column_id;  
```  
  
### <a name="h-merging-two-partitions"></a>H. Mezclar dos particiones  
 En el ejemplo siguiente se combinan dos particiones en una tabla.  
  
 El `Customer` tabla tiene la siguiente definición:  
  
```  
CREATE TABLE Customer (  
    id int NOT NULL,  
    lastName varchar(20),  
    orderCount int,  
    orderDate date)  
WITH   
    ( DISTRIBUTION = HASH(id),  
    PARTITION ( orderCount RANGE LEFT  
    FOR VALUES (1, 5, 10, 25, 50, 100)));  
```  
  
 El comando siguiente combina los límites de partición 10 y 25.  
  
```  
ALTER TABLE Customer MERGE RANGE (10);  
```  
  
 El nuevo archivo DDL para la tabla es:  
  
```  
CREATE TABLE Customer (  
    id int NOT NULL,  
    lastName varchar(20),  
    orderCount int,  
    orderDate date)  
WITH   
    ( DISTRIBUTION = HASH(id),  
    PARTITION ( orderCount RANGE LEFT  
    FOR VALUES (1, 5, 25, 50, 100)));  
```  
  
### <a name="i-splitting-a-partition"></a>I. Dividir una partición  
 En el ejemplo siguiente se divide una partición en una tabla.  
  
 El `Customer` tabla tiene el siguiente DDL:  
  
```  
DROP TABLE Customer;  
  
CREATE TABLE Customer (  
    id int NOT NULL,  
    lastName varchar(20),  
    orderCount int,  
    orderDate date)  
WITH   
    ( DISTRIBUTION = HASH(id),  
    PARTITION ( orderCount RANGE LEFT  
    FOR VALUES (1, 5, 10, 25, 50, 100 )));  
```  
  
 El siguiente comando crea una nueva partición enlazada por el valor 75, entre 50 y 100.  
  
```  
ALTER TABLE Customer SPLIT RANGE (75);  
```  
  
 El nuevo archivo DDL para la tabla es:  
  
```  
CREATE TABLE Customer (  
   id int NOT NULL,  
   lastName varchar(20),  
   orderCount int,  
   orderDate date)  
   WITH DISTRIBUTION = HASH(id),  
   PARTITION ( orderCount (RANGE LEFT  
      FOR VALUES (1, 5, 10, 25, 50, 75, 100 )));  
```  
  
### <a name="j-using-switch-to-move-a-partition-to-a-history-table"></a>J. Usar el modificador para mover una partición a una tabla de historial  
 El siguiente ejemplo mueve los datos en una partición de la `Orders` tabla a una partición en el `OrdersHistory` tabla.  
  
 El `Orders` tabla tiene el siguiente DDL:  
  
```  
CREATE TABLE Orders (  
    id INT,  
    city VARCHAR (25),  
    lastUpdateDate DATE,  
    orderDate DATE )  
WITH   
    (DISTRIBUTION = HASH ( id ),  
    PARTITION ( orderDate RANGE RIGHT   
    FOR VALUES ('2004-01-01', '2005-01-01', '2006-01-01', '2007-01-01' )));  
```  
  
 En este ejemplo, el `Orders` tabla tiene las siguientes particiones. Cada partición contiene datos.  
  
|Partición|¿Tiene datos?|Intervalo de límite|  
|---------------|---------------|--------------------|  
|1|Sí|OrderDate < "2004-01-01'|  
|2|Sí|' 2004-01-01' < = OrderDate < ' 2005-01-01'|  
|3|Sí|' 2005-01-01' < = OrderDate < ' 2006-01-01'|  
|4|Sí|' 2006-01-01'< = OrderDate < ' 2007-01-01'|  
|5|Sí|' 2007-01-01' < = OrderDate|  
  
-   La partición 1 (tiene datos): OrderDate < "2004-01-01'  
-   Partición 2 (tiene datos): "2004-01-01' < = OrderDate < ' 2005-01-01'  
-   Partición 3 (tiene datos): ' 2005-01-01' < = OrderDate < ' 2006-01-01'  
-   Partición 4 (tiene datos): "2006-01-01'< = OrderDate < ' 2007-01-01'  
-   La partición 5 (tiene datos): ' 2007-01-01' < = OrderDate  
  
El `OrdersHistory` tabla tiene la siguiente instrucción de DDL, que tiene columnas idénticas y nombres de columna como el `Orders` tabla. Ambos están distribuidas de hash en la `id` columna.  
  
```  
CREATE TABLE OrdersHistory (  
   id INT,  
   city VARCHAR (25),  
   lastUpdateDate DATE,  
   orderDate DATE )  
WITH   
    (DISTRIBUTION = HASH ( id ),  
    PARTITION ( orderDate RANGE RIGHT   
    FOR VALUES ( '2004-01-01' )));  
```  
  
 Aunque las columnas y los nombres de columna deben ser los mismos, los límites de partición no es necesario ser el mismo. En este ejemplo, el `OrdersHistory` tabla tiene las siguientes dos particiones y ambas particiones están vacíos:  
  
-   La partición 1 (ningún dato): OrderDate < "2004-01-01'  
-   Partición 2 (vacío): "2004-01-01' < = OrderDate  
  
Para las dos tablas anteriores, el siguiente comando mueve todas las filas con `OrderDate < '2004-01-01'` desde el `Orders` la tabla a la `OrdersHistory` tabla.  
  
```  
ALTER TABLE Orders SWITCH PARTITION 1 TO OrdersHistory PARTITION 1;  
```  
  
 Como resultado, la primera partición en `Orders` está vacía y la primera partición en `OrdersHistory` contiene datos. Ahora, las tablas aparecen como se indica a continuación:  
  
 `Orders`tabla  
  
-   La partición 1 (vacío): OrderDate < "2004-01-01'  
-   Partición 2 (tiene datos): "2004-01-01' < = OrderDate < ' 2005-01-01'  
-   Partición 3 (tiene datos): ' 2005-01-01' < = OrderDate < ' 2006-01-01'  
-   Partición 4 (tiene datos): "2006-01-01'< = OrderDate < ' 2007-01-01'  
-   La partición 5 (tiene datos): ' 2007-01-01' < = OrderDate  
  
 `OrdersHistory`tabla  
  
-   La partición 1 (tiene datos): OrderDate < "2004-01-01'  
-   Partición 2 (vacío): "2004-01-01' < = OrderDate  
  
Para limpiar el `Orders` tabla, puede quitar la partición vacía mezclar particiones 1 y 2 como sigue:  
  
```  
ALTER TABLE Orders MERGE RANGE ('2004-01-01');  
```  
  
 Después de la combinación, el `Orders` tabla tiene las siguientes particiones:  
  
 `Orders`tabla  
  
-   La partición 1 (tiene datos): OrderDate < ' 2005-01-01'  
-   Partición 2 (tiene datos): ' 2005-01-01' < = OrderDate < ' 2006-01-01'  
-   Partición 3 (tiene datos): "2006-01-01'< = OrderDate < ' 2007-01-01'  
-   Partición 4 (tiene datos): ' 2007-01-01' < = OrderDate  
  
Suponga que pasa otro año y esté listo para archivar el año 2005. Puede asignar una partición vacía para el año 2005 en el `OrdersHistory` tabla dividiendo la partición vacía como se indica a continuación:  
  
```  
ALTER TABLE OrdersHistory SPLIT RANGE ('2005-01-01');  
```  
  
 Después de la división, la `OrdersHistory` tabla tiene las siguientes particiones:  
  
 `OrdersHistory`tabla  
  
-   La partición 1 (tiene datos): OrderDate < "2004-01-01'  
-   Partición 2 (vacío): "2004-01-01' < ' 2005-01-01'  
-   Partición 3 (vacío): ' 2005-01-01' < = OrderDate  
  
## <a name="see-also"></a>Vea también  
 [sys.tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)   
 [sp_rename &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [Eliminar tabla &#40; Transact-SQL &#41;](../../t-sql/statements/drop-table-transact-sql.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [ALTER PARTITION SCHEME &#40; Transact-SQL &#41;](../../t-sql/statements/alter-partition-scheme-transact-sql.md)   
 [ALTER PARTITION FUNCTION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-partition-function-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  


