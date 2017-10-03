---
title: "Modificar configuración de ámbito de base de datos (Transact-SQL) | Documentos de Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/27/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ALTER_DATABASE_SCOPED_CONFIGURATION
- ALTER_DATABASE_SCOPED_CONFIGURATION_TSQL
- DATABASE_SCOPED_CONFIGURATION_TSQL
- SCOPED_CONFIGURATION_TSQL
- SCOPED_TSQL
- ALTER_DATABASE_SCOPED_TSQL
- DATABASE_SCOPED_TSQL
helpviewer_keywords:
- ALTER DATABASE SCOPED CONFIGURATION statement
- configuration [SQL Server], ALTER DATABASE SCOPED CONFIGURATION statement
ms.assetid: 63373c2f-9a0b-431b-b9d2-6fa35641571a
caps.latest.revision: 32
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 19d2d42ff513020b5d4bb9492f0714893101bdcb
ms.contentlocale: es-es
ms.lasthandoff: 09/27/2017

---
# <a name="alter-database-scoped-configuration-transact-sql"></a>Modificar configuración de ámbito de base de datos (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Esta instrucción permite varios valores de configuración de base de datos en el **base de datos individual** nivel. Esta instrucción está disponible tanto en [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] y en [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. Los valores son:  
  
- Borrar la caché de procedimientos.  
  
- Definir el parámetro MAXDOP en un valor arbitrario (1, 2, ...) para la base de datos principal en función del valor que funciona mejor para una base de datos determinada y definir un valor distinto (por ejemplo, 0) para todas las bases de datos secundarias que se usan (por ejemplo, para informar las consultas).  
  
- Definir el modelo de estimación de la cardinalidad del optimizador de consultas independiente de la base de datos en el nivel de compatibilidad.  
  
- Habilitar o deshabilitar el examen de parámetros en el nivel de base de datos.
  
- Habilitar o deshabilitar las revisiones de optimización de consulta en el nivel de base de datos.

- Habilitar o deshabilitar la memoria caché de identidad en el nivel de base de datos.
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
ALTER DATABASE SCOPED CONFIGURATION  
{        
     {  [ FOR SECONDARY] SET <set_options>  }    
}  
| CLEAR PROCEDURE_CACHE  
| SET IDENTITY_CACHE = { ON | OFF }
[;]    
  
< set_options > ::=    
{  
    MAXDOP = { <value> | PRIMARY}    
    | LEGACY_CARDINALITY_ESTIMATION = { ON | OFF | PRIMARY}    
    | PARAMETER_SNIFFING = { ON | OFF | PRIMARY}    
    | QUERY_OPTIMIZER_HOTFIXES = { ON | OFF | PRIMARY}    
}  
  
```  
  
## <a name="arguments"></a>Argumentos  
 
PARA LA BASE DE DATOS SECUNDARIA  
 
Especifica la configuración de bases de datos secundarias (todas las bases de datos secundarias deben tener los valores idénticos).  
  
MAXDOP  **=**  {\<valor > | PRINCIPAL}  
**\<valor >**  
  
Especifica el valor predeterminado MAXDOP configuración que debe utilizarse para las instrucciones. 0 es el valor predeterminado y se indica que se utilizará en su lugar la configuración del servidor. Reemplaza a la MAXDOP en el ámbito de la base de datos (a menos que se establece en 0) la **grado máximo de paralelismo** establece en el nivel de servidor mediante sp_configure. Sugerencias de consulta aún pueden reemplazar a la base de datos con ámbito de MAXDOP con el fin de optimizar las consultas específicas que requieran configuración diferente. Todas estas configuraciones están limitadas por el MAXDOP establecidos para el grupo de cargas de trabajo.   

Puede utilizar la opción Grado máximo de paralelismo para limitar el número de procesadores que debe utilizarse en la ejecución de planes en paralelo. SQL Server considera los planes de ejecución en paralelo para las consultas, las operaciones DDL (lenguaje) de definición de datos de índice, inserción en paralelo, de columnas, collectiion stats paralelo y el rellenado de cursor estático y controlado por la alteración en línea.
 
Para establecer esta opción en el nivel de instancia, consulte [configurar la max degree of parallelism Server Configuration Option](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md). 

> [!TIP] 
> Para lograr esto en el nivel de consulta, agregue el **MAXDOP** [sugerencia de consulta](../../t-sql/queries/hints-transact-sql-query.md).  
  
PRIMARY  
  
Solo puede establecerse para los elementos secundarios, mientras la base de datos en el servidor principal e indica que la configuración se realizará la definida para la réplica principal. Si va a cambiar la configuración de los cambios principales, el valor en los servidores secundarios en consecuencia sin necesidad de establecer los servidores secundarios valor explícitamente. **PRINCIPAL** es la configuración predeterminada para los servidores secundarios.  
  
LEGACY_CARDINALITY_ESTIMATION  **=**  {ON | **OFF** | PRINCIPAL}  

Permite establecer el modelo de estimación de cardinalidad del optimizador de consultas para el SQL Server 2012 y la versión anterior independiente del nivel de compatibilidad de la base de datos. El valor predeterminado es **OFF**, que establece el modelo de estimación de cardinalidad del optimizador de consultas basado en el nivel de compatibilidad de la base de datos. Si se establece en **ON** es equivalente a habilitar [marca de seguimiento 9481](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md). 

> [!TIP] 
> Para lograr esto en el nivel de consulta, agregue el **QUERYTRACEON** [sugerencia de consulta](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md). A partir de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1, para lograr esto en el nivel de consulta, agregue el **sugerencia USE** [sugerencia de consulta](../../t-sql/queries/hints-transact-sql-query.md) en lugar de utilizar la marca de seguimiento. 
  
PRIMARY  
  
Este valor solo es válido en los elementos secundarios mientras la base de datos en el servidor principal y especifica que la configuración de modelo de estimación de consulta optimizador cardinalidad en todas las secundarias será el valor establecido para el servidor principal. Si cambia la configuración en el servidor principal para el modelo de estimación de cardinalidad del optimizador de consultas, el valor en los servidores secundarios cambiará en consecuencia. **PRINCIPAL** es la configuración predeterminada para los servidores secundarios.  
  
PARAMETER_SNIFFING  **=**  { **ON** | DESACTIVAR | PRINCIPAL}  

Habilita o deshabilita [examen de parámetros](../../relational-databases/query-processing-architecture-guide.md#ParamSniffing). El valor predeterminado es ON. Es equivalente a la [Marca de seguimiento 4136](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md).   

> [!TIP] 
> Para lograr esto en el nivel de consulta, vea el **OPTIMIZE FOR UNKNOWN** [sugerencia de consulta](../../t-sql/queries/hints-transact-sql-query.md). A partir de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1, para lograr esto en el nivel de consulta, el **sugerencia USE** [sugerencia de consulta](../../t-sql/queries/hints-transact-sql-query.md) también está disponible. 
  
PRIMARY  
  
Este valor solo es válido en los elementos secundarios mientras la base de datos en el servidor principal y especifica que el valor de esta configuración en todas las secundarias será el valor establecido para el servidor principal. Si la configuración en el servidor principal para el uso de [examen de parámetros](../../relational-databases/query-processing-architecture-guide.md#ParamSniffing) cambios, el valor en los servidores secundarios cambiará en consecuencia, sin necesidad de establecer los servidores secundarios valor explícitamente. Se trata de la configuración predeterminada para los servidores secundarios.  
  
QUERY_OPTIMIZER_HOTFIXES  **=**  {ON | **OFF** | PRINCIPAL}  

Habilita o deshabilita las revisiones de optimización de consulta, independientemente del nivel de compatibilidad de la base de datos. El valor predeterminado es **OFF**. Esto es equivalente a habilitar [marca de seguimiento 4199](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md).   

> [!TIP] 
> Para lograr esto en el nivel de consulta, agregue el **QUERYTRACEON** [sugerencia de consulta](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md). A partir de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1, para lograr esto en el nivel de consulta, agregue la sugerencia USE [sugerencia de consulta](../../t-sql/queries/hints-transact-sql-query.md) en lugar de utilizar la marca de seguimiento.  
  
PRIMARY  
  
Este valor solo es válido en los elementos secundarios mientras la base de datos en el servidor principal y especifica que el valor de esta configuración en todas las secundarias será el valor establecido para el servidor principal. Si va a cambiar la configuración de los cambios principales, el valor en los servidores secundarios en consecuencia sin necesidad de establecer los servidores secundarios valor explícitamente. Se trata de la configuración predeterminada para los servidores secundarios.  
  
DESACTIVE PROCEDURE_CACHE  

Borra la caché de procedimientos para la base de datos. Esto se puede ejecutar tanto en el servidor principal y los servidores secundarios.  

IDENTITY_CACHE = { **ON** | {OFF}  

**Se aplica a**: SQL Server 2017 y Azure SQL Database (característica está en versión preliminar pública) 

Habilita o deshabilita la memoria caché de identidad en el nivel de base de datos. El valor predeterminado es **ON**. Almacenamiento en caché de identidad se utiliza para mejorar el rendimiento de INSERT en tablas con columnas de identidad. Para evitar los huecos en los valores de la columna de identidad en los casos en que el servidor se reinicia inesperadamente o conmuta por error a un servidor secundario, deshabilite la opción IDENTITY_CACHE. Esta opción es similar a la 272 de marca de existente SQL Server seguimiento, excepto en que se puede establecer en el nivel de base de datos, en lugar de hacerlo en el nivel de servidor.   

> [!NOTE] 
> Esta opción solo puede establecerse para la réplica principal. Para obtener más información, consulte [las columnas de identidad](create-table-transact-sql-identity-property.md).  
>

##  <a name="Permissions"></a> Permisos  
 Requiere modificar cualquier configuración de ámbito de base de datos   
en la base de datos. Este permiso se puede conceder a un usuario con permiso CONTROL en una base de datos  
  
## <a name="general-remarks"></a>Notas generales  
 Aunque puede configurar bases de datos secundarias para tener valores de configuración de ámbito diferente desde su servidor principal, todas las bases de datos secundarias usará la misma configuración. No se puede configurar diferentes valores de los elementos secundarios individuales.  
  
 Al ejecutar esta instrucción, se borrará la caché de procedimientos en la base de datos actual, lo que significa que todas las consultas tendrá que volver a compilar.  
  
 Para las consultas de nombre de parte 3, la configuración de la conexión de base de datos actual para la consulta se puede respetar, distinto de módulos SQL (por ejemplo, procedimientos, funciones y desencadenadores) que se compilan en el contexto de base de datos actual y, por tanto, usará las opciones de la base de datos en las que residen.  
  
 El evento ALTER_DATABASE_SCOPED_CONFIGURATION se agrega como un evento DDL que puede usarse para activar un desencadenador DDL. Se trata de un elemento secundario del grupo de desencadenador ALTER_DATABASE_EVENTS.  
  
## <a name="limitations-and-restrictions"></a>Limitaciones y restricciones  
 **MAXDOP**  
  
 La configuración granular puede invalidar los globales y que el regulador de recursos puede limitar todas las demás opciones de MAXDOP.  La lógica para la configuración de MAXDOP es el siguiente:  
  
-   Sugerencia de consulta invalida sp_configure y la base de datos con ámbito de configuración. Si el grupo de recursos MAXDOP se establece para el grupo de cargas de trabajo:  
  
    -   Si la sugerencia de consulta se establece en 0 se reemplaza por el regulador de recursos establecer.  
  
    -   Si la sugerencia de consulta no es 0, está limitada por el regulador de recursos establecer.  
  
-   La base de datos con ámbito de configuración (a menos que sea 0) invalida el valor de sp_configure a menos que haya una sugerencia de consulta y está limitada por el regulador de recursos establecer.  
  
-   El regulador de recursos configuración reemplaza el valor de sp_configure.  
  
 **QUERY_OPTIMIZER_HOTFIXES**  
  
 Cuando se utiliza la sugerencia QUERYTRACEON para habilitar el optimizador de consultas heredado o las revisiones del optimizador de consultas, sería una condición OR entre la sugerencia de consulta y la configuración de base de datos con ámbito de configuración, lo que significa que si está habilitada, se aplicarán las opciones.  
  
 **GeoDR**  
  
 Legibles bases de datos secundarias, por ejemplo, grupos de disponibilidad AlwaysOn y GeoReplication, utilizan el valor secundario comprobando el estado de la base de datos. Aunque se no vuelve a compilar en la conmutación por error y técnicamente el nuevo elemento principal tiene consultas que utilizan la configuración de secundaria, la idea es que la configuración entre principal y secundaria solo varían cuando la carga de trabajo es diferente y, por tanto, las consultas en caché con la configuración óptima, mientras que las nuevas consultas seleccionará la nueva configuración que es adecuada para ellos.  
  
 **DacFx**  
  
 Puesto que ALTER DATABASE SCOPED CONFIGURATION es una nueva característica de base de datos de SQL Azure y SQL Server 2016 que afecta al esquema de base de datos, las exportaciones del esquema (con o sin datos) no podrá importarse a una versión anterior de SQL Server, por ejemplo, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] o < C2 > [!INCLUDE[ssSQLv14](../../includes/sssqlv14-md.md)] . Por ejemplo, una exportación a un [DACPAC](https://msdn.microsoft.com/library/ee210546.aspx#Anchor_3) o un [BACPAC](https://msdn.microsoft.com/library/ee210546.aspx#Anchor_4) desde una [!INCLUDE[ssSDS](../../includes/sssds-md.md)] o [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] base de datos que usa esta nueva característica no podrá importarse a un servidor de nivel inferior.  
  
## <a name="metadata"></a>Metadatos  

El [sys.database_scoped_configurations &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md) vista del sistema proporciona información acerca de las configuraciones con ámbito en una base de datos. Opciones de configuración de ámbito de base de datos sólo se muestran en sys.database_scoped_configurations tal como están invalidaciones a la configuración predeterminada de todo el servidor. El [sys.configurations &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md) vista del sistema solo muestra la configuración del servidor.  
  
## <a name="examples"></a>Ejemplos  
Estos ejemplos muestran el uso de ALTER DATABASE SCOPED CONFIGURATION  
  
### <a name="a-grant-permission"></a>A. Conceder permiso  

En este ejemplo conceder el permiso necesario para ejecutar ALTER DATABASE SCOPED CONFIGURATION     
para el usuario [Juan].  
  
```tsql  
GRANT ALTER ANY DATABASE SCOPED CONFIGURATION to [Joe] ;  
```  
  
### <a name="b-set-maxdop"></a>B. Conjunto MAXDOP  

Este ejemplo establece MAXDOP = 1 para una base de datos principal y MAXDOP = 4 para una base de datos secundaria en un escenario de replicación geográfica.  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION SET MAXDOP = 1 ;  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET MAXDOP=4 ;  
```  
  
En este ejemplo se establece MAXDOP de una base de datos secundaria para ser el mismo que se establece para su base de datos principal en un escenario de replicación geográfica.  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET MAXDOP=PRIMARY ;
```  
  
### <a name="c-set-legacycardinalityestimation"></a>C. Establecer LEGACY_CARDINALITY_ESTIMATION  

Este ejemplo establece en ON LEGACY_CARDINALITY_ESTIMATION para una base de datos secundaria en un escenario de replicación geográfica.  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET LEGACY_CARDINALITY_ESTIMATION=ON ;  
```  
  
Este ejemplo establece LEGACY_CARDINALITY_ESTIMATION para una base de datos secundaria como para su base de datos principal en un escenario de replicación geográfica.  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET LEGACY_CARDINALITY_ESTIMATION=PRIMARY ;  
```  
  
### <a name="d-set-parametersniffing"></a>D. Establecer PARAMETER_SNIFFING  

Este ejemplo establece PARAMETER_SNIFFING en OFF para una base de datos principal en un escenario de replicación geográfica.  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION SET PARAMETER_SNIFFING =OFF ;  
```  
  
Este ejemplo establece PARAMETER_SNIFFING en OFF para una base de datos principal en un escenario de replicación geográfica.  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET PARAMETER_SNIFFING=OFF ;  
```  
  
Este ejemplo establece PARAMETER_SNIFFING para la base de datos secundaria como está en la base de datos principal   
en un escenario de replicación geográfica.  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET PARAMETER_SNIFFING =PRIMARY ;  
```  
  
### <a name="e-set-queryoptimizerhotfixes"></a>E. Establecer QUERY_OPTIMIZER_HOTFIXES  

Establece QUERY_OPTIMIZER_HOTFIXES en ON para una base de datos principal   
en un escenario de replicación geográfica.  

```tsql  
ALTER DATABASE SCOPED CONFIGURATION SET QUERY_OPTIMIZER_HOTFIXES=ON ;  
```  
  
### <a name="f-clear-procedure-cache"></a>F. Borrar caché de procedimientos  

Este ejemplo borra la caché de procedimientos (es posible sólo para una base de datos principal).  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE ;  
```  

### <a name="g-set-identitycache"></a>G. Establecer IDENTITY_CACHE

**Se aplica a**: SQL Server 2017 y Azure SQL Database (característica está en versión preliminar pública) 

Este ejemplo deshabilita la caché de identidad.

```tsql 
ALTER DATABASE SCOPED CONFIGURATION SET IDENTITY_CACHE=OFF ; 
```

## <a name="additional-resources"></a>Recursos adicionales

### <a name="maxdop-resources"></a>Recursos MAXDOP 
* [Recomendaciones y directrices para la opción de configuración "max degree of parallelism" en SQL Server](https://support.microsoft.com/en-us/kb/2806535) 

### <a name="legacycardinalityestimation-resources"></a>Recursos LEGACY_CARDINALITY_ESTIMATION    
* [Estimación de cardinalidad (SQL Server)](../../relational-databases/performance/cardinality-estimation-sql-server.md)
* [Optimizar los planes de consulta con el estimador de cardinalidad de SQL Server 2014](https://msdn.microsoft.com/library/dn673537.aspx)

### <a name="parametersniffing-resources"></a>Recursos PARAMETER_SNIFFING    
* ["Tomarse un parámetro"](https://blogs.msdn.microsoft.com/queryoptteam/2006/03/31/i-smell-a-parameter/)

### <a name="queryoptimizerhotfixes-resources"></a>Recursos QUERY_OPTIMIZER_HOTFIXES    
* [SQL Server modelo optimizador de consultas revisión seguimiento marca 4199 mantenimiento](https://support.microsoft.com/en-us/kb/974006)

## <a name="more-information"></a>Más información  
 [Sys.database_scoped_configurations &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md)   
 [sys.configurations&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)   
 [Vistas de catálogo de archivos y bases de datos &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [Opciones de configuración de servidor &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [Marcas de seguimiento &#40; Transact-SQL &#41;](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)   
 [Sys.Configurations &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)  
  
  

