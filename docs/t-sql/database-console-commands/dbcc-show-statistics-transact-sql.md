---
title: DBCC SHOW_STATISTICS (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SHOW_STATISTICS_TSQL
- DBCC SHOW_STATISTICS
- SHOW_STATISTICS
- DBCC_SHOW_STATISTICS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- query optimization statistics [SQL Server], densities
- histograms [SQL Server]
- statistical information [SQL Server], viewing statistics objects
- current distribution statistics
- query optimization statistics [SQL Server], histograms
- DBCC SHOW_STATISTICS statement
- distribution statistics
- statistical information [SQL Server], densities
- statistics objects
- statistical information [SQL Server], histograms
- query optimization statistics [SQL Server], viewing statistics objects
- statistical information [SQL Server], distribution
- densities [SQL Server]
- displaying distribution statistics
ms.assetid: 12be2923-7289-4150-b497-f17e76a50b2e
caps.latest.revision: 75
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: 38abfb552f1bb969c132d5086ca007d36541a76c
ms.contentlocale: es-es
ms.lasthandoff: 10/17/2017

---
# <a name="dbcc-showstatistics-transact-sql"></a>DBCC SHOW_STATISTICS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

DBCC SHOW_STATISTICS muestra las estadísticas de optimización de consulta actuales de una tabla o vista indizada. El optimizador de consultas utiliza las estadísticas para estimar la cardinalidad o el número de filas del resultado de la consulta, lo que hace posible que el optimizador de consultas pueda crear un plan de consulta de alta calidad. Por ejemplo, el optimizador de consultas podría utilizar las estimaciones de cardinalidad para elegir el operador index seek en lugar del operador index scan en el plan de consulta, lo que mejoraría el rendimiento de las consultas al evitar el examen de índices con una gran cantidad de recursos.
  
El optimizador de consultas almacena las estadísticas de una tabla o vista indizada en un objeto de estadísticas. En una tabla, el objeto de estadísticas se crea en un índice o en una lista de columnas de la tabla. El objeto de estadísticas incluye un encabezado con metadatos sobre las estadísticas, un histograma con la distribución de valores de la primera columna de clave del objeto de estadísticas y un vector de la densidad para medir la correlación entre las columnas. [!INCLUDE[ssDE](../../includes/ssde-md.md)] puede calcular las estimaciones de cardinalidad con cualquiera de los datos del objeto de estadísticas.
  
DBCC SHOW_STATISTICS muestra el encabezado, el histograma y el vector de densidad en función de los datos guardados en el objeto de estadísticas. La sintaxis le permite especificar una tabla o vista indizada junto con un nombre del índice de destino, un nombre de las estadísticas o un nombre de columna. En este tema se describe cómo se muestran las estadísticas y cómo se interpretan los resultados mostrados.
  
Para obtener más información, vea [Statistics](../../relational-databases/statistics/statistics.md).
  
![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintaxis  
  
```
-- Syntax for SQL Server and Azure SQL Database  
  
DBCC SHOW_STATISTICS ( table_or_indexed_view_name , target )   
[ WITH [ NO_INFOMSGS ] < option > [ , n ] ]  
< option > :: =  
    STAT_HEADER | DENSITY_VECTOR | HISTOGRAM | STATS_STREAM  
```  
  
```
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  

DBCC SHOW_STATISTICS ( table_name , target )   
    [ WITH {STAT_HEADER | DENSITY_VECTOR | HISTOGRAM } [ ,...n ] ]  
[;]  
```  
  
## <a name="arguments"></a>Argumentos  
 *table_or_indexed_view_name*  
 Nombre de la tabla o de la vista indizada cuya información de estadísticas se va a presentar.  
  
 *table_name*  
 Nombre de la tabla que contiene las estadísticas para mostrar. La tabla no puede ser una tabla externa.  
  
 *destino*  
 Nombre del índice, estadística o columna cuya información de estadísticas se va a presentar. *destino* se incluye entre corchetes, solo las comillas, comillas dobles o sin comillas. Si *destino* es un nombre de un índice existente o se devuelven las estadísticas de una tabla o vista indizada, la información de estadísticas acerca de este destino. Si *destino* es el nombre de una columna existente, y existe una estadísticas creadas automáticamente en esta columna, se devuelve información sobre dicha estadística creada automáticamente. Si una estadística creada automáticamente no existe para el destino de una columna, se devuelve el mensaje de error 2767.  
 En [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] y [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], *destino* no puede ser un nombre de columna.  
  
 NO_INFOMSGS  
 Suprime todos los mensajes informativos con niveles de gravedad entre 0 y 10.  
  
 STAT_HEADER | DENSITY_VECTOR | HISTOGRAMA | STATS_STREAM [ **,** * n * ]  
 La especificación de una o varias de estas opciones limita los conjuntos de resultados devueltos por la instrucción a la opción u opciones especificadas. Si no se especifican opciones, se devuelve información de todas las estadísticas.  
  
 STATS_STREAM es [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="result-sets"></a>Conjuntos de resultados  
En la tabla siguiente se describen las columnas devueltas en el conjunto de resultados si se especifica STAT_HEADER.
  
|Nombre de columna|Description|  
|-----------------|-----------------|  
|Nombre|Nombre del objeto de estadísticas.|  
|Actualizado|Fecha y hora de la última actualización de las estadísticas. El [STATS_DATE](../../t-sql/functions/stats-date-transact-sql.md) función es un medio alternativo para recuperar esta información.|  
|Filas|Número total de filas que tenía la tabla o vista indizada la última vez que se actualizaron las estadísticas. Si las estadísticas se filtran o corresponden a un índice filtrado, el número de filas puede ser inferior al número de filas de la tabla. Para obtener más información, consulte[estadísticas](../../relational-databases/statistics/statistics.md).|  
|Rows Sampled|Número total de filas muestreadas para cálculos de estadísticas. Si Rows Sampled < Rows, el histograma y los resultados de la densidad que se muestren serán estimaciones extraídas de las filas muestreadas.|  
|Pasos|Número de pasos del histograma. Cada paso abarca un intervalo de valores de columna seguido de un valor de columna límite superior. Los pasos del histograma se definen en la primera columna de clave de las estadísticas. El número máximo de pasos es 200.|  
|Densidad|Se calcula como 1 / *valores distintos* en todos los valores de la primera columna de clave del objeto de estadísticas, excepto en los valores límite del histograma. El optimizador de consultas no usa este valor de densidad y solo se muestra por motivos de compatibilidad con versiones anteriores a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].|  
|Promedio de longitud de clave|Número promedio de bytes por cada uno de los valores de las columnas de clave del objeto de estadísticas.|  
|String Index|Sí indica que el objeto de estadísticas contiene estadísticas de resumen de las cadenas para mejorar los cálculos de cardinalidad de los predicados de consulta que utilizan el operador LIKE; por ejemplo, `WHERE ProductName LIKE '%Bike'`. Estadísticas de resumen se almacenan por separado desde el histograma y se crean en la primera columna de clave del objeto de estadísticas cuando es del tipo de cadena **char**, **varchar**, **nchar**, **nvarchar**, **varchar (max)**, **nvarchar (max)**, **texto**, o **ntext.**.|  
|Expresión de filtro|Predicado del subconjunto de filas de la tabla incluido en el objeto de estadísticas. NULL = Estadísticas no filtradas. Para obtener más información sobre predicados filtrados, vea [Create Filtered Indexes](../../relational-databases/indexes/create-filtered-indexes.md). Para obtener más información acerca de las estadísticas filtradas, vea [estadísticas](../../relational-databases/statistics/statistics.md).|  
|Filas sin filtrar|Número total de filas de la tabla antes de aplicar la expresión de filtro. Si Expresión de filtro es NULL, las Filas sin filtrar son iguales a Filas.|  
|Conserva el porcentaje de ejemplo|Conserva el porcentaje de ejemplo que se usan para las actualizaciones de estadísticas que no especifican explícitamente un porcentaje de muestreo. Si el valor es cero, no hay ningún porcentaje de ejemplo persistente se establece para esta estadística.<br /><br /> **Se aplica a:** [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 CU4| 
  
En la tabla siguiente se describen las columnas devueltas en el conjunto de resultados si se especifica DENSITY_VECTOR.
  
|Nombre de columna|Description|  
|-----------------|-----------------|  
|Toda la densidad|La densidad es 1 / *valores distintos*. Los resultados muestran la densidad de cada prefijo de columnas del objeto de estadísticas (una fila por cada densidad). Un valor distinto es una lista Distinct de los valores de columna de cada fila y prefijo de columna. Por ejemplo, si el objeto de estadísticas contiene las columnas de clave (A, B, C), los resultados indican la densidad de las listas de valores distintos de cada uno de estos prefijos de columna: (A), (A,B) y (A, B, C). Con el prefijo (A, B, C), cada una de estas listas es una lista de valores distintos: (3, 5, 6) (4, 4, 6) (4, 5, 6) (4, 5, 7). Con el prefijo (A, B) los mismos valores de columna tiene estas listas de valores distintos: (3, 5), (4, 4) y (4, 5)|  
|Promedio de longitud|Promedio de longitud, en bytes, para almacenar una lista de los valores de columna del prefijo de columna. Por ejemplo, si cada valor de la lista (3, 5, 6) necesita 4 bytes, la longitud es 12 bytes.|  
|Columnas|Nombres de las columnas en el prefijo para las que se muestran Toda la densidad y Promedio de longitud.|  
  
En la tabla siguiente se describen las columnas devueltas en el conjunto de resultados si se especifica la opción HISTOGRAM.
  
|Nombre de columna|Description|  
|---|---|
|RANGE_HI_KEY|Valor de columna límite superior de un paso del histograma. El valor de columna también se denomina valor de clave.|  
|RANGE_ROWS|Número calculado de filas cuyo valor de columna está comprendido en un paso del histograma, sin incluir el límite superior.|  
|EQ_ROWS|Número calculado de filas cuyo valor de columna es igual al límite superior del paso del histograma.|  
|DISTINCT_RANGE_ROWS|Número calculado de filas que tienen un valor de columna distinto en un paso del histograma, sin incluir el límite superior.|  
|AVG_RANGE_ROWS|Número medio de filas que tienen valores de columna duplicados en un paso del histograma, sin incluir el límite superior (RANGE_ROWS/DISTINCT_RANGE_ROWS para DISTINCT_RANGE_ROWS > 0).| 
  
## <a name="remarks"></a>Comentarios  
  
## <a name="histogram"></a>Histograma  
Un histograma mide la frecuencia de aparición de cada valor distinto en un conjunto de datos. El optimizador de consultas calcula un histograma de los valores de la primera columna de clave del objeto de estadísticas; para ello, selecciona los valores de la columna tomando una muestra estadística de las filas o realizando un análisis completo de todas las filas de la tabla o vista. Si el histograma se crea a partir de muestras de un conjunto de filas, los totales almacenados para el número de filas y el número de valores distintos son las estimaciones y no es necesario que sean números enteros.
  
Para crear el histograma, el optimizador de consultas ordena los valores de columna, calcula el número de valores que coinciden con cada valor de columna distinto y, a continuación, agrupa los valores de columna en un máximo de 200 pasos de histograma contiguos. Cada paso incluye un intervalo de valores de columna seguido de un valor de columna de límite superior. El intervalo incluye todos los valores de columna posibles comprendidos entre los valores límite (sin incluir los propios valores límite). El valor de columna ordenado más pequeño es el valor del límite superior del primer paso del histograma.
  
En el diagrama siguiente se muestra un histograma con seis pasos. El área a la izquierda del primer valor límite superior es el primer paso.
  
![](../../relational-databases/system-dynamic-management-views/media/a0ce6714-01f4-4943-a083-8cbd2d6f617a.gif "a0ce6714-01f4-4943-a083-8cbd2d6f617a")
  
En cada paso del histograma:
-   La línea gruesa representa el valor de límite superior (RANGE_HI_KEY) y el número de veces que tiene lugar (EQ_ROWS).  
-   El área de color sólido situada a la izquierda RANGE_HI_KEY representa el intervalo de valores de columna y el número medio de veces que tiene lugar cada valor de columna (AVG_RANGE_ROWS). El valor de AVG_RANGE_ROWS en el primer paso del histograma siempre es 0.  
-   Las líneas de puntos representan los valores de las muestras utilizados para estimar el número total de valores distintos que hay en el intervalo (DISTINCT_RANGE_ROWS) y el número total de valores que hay en el intervalo (RANGE_ROWS). El optimizador de consultas utiliza RANGE_ROWS y DISTINCT_RANGE_ROWS para calcular AVG_RANGE_ROWS y no almacena los valores de las muestras.  
  
El optimizador de consultas define los pasos del histograma en función de su importancia estadística. Utiliza un algoritmo de diferencias máximas para minimizar el número de pasos del histograma a la vez que minimiza las diferencias entre los valores límite. El número máximo de pasos es 200. El número de pasos del histograma puede ser menor que el número de valores distintos, incluso para las columnas con menos de 200 puntos de límite. Por ejemplo, una columna con 100 valores distintos puede tener un histograma con menos de 100 puntos de límite.
  
## <a name="density-vector"></a>Vector de densidad  
El optimizador de consultas utiliza las densidades para mejorar las estimaciones de cardinalidad de las consultas que devuelven varias columnas de la misma tabla o vista indizada. El vector de densidad contiene una densidad para cada prefijo de columnas del objeto de estadísticas. Por ejemplo, si un objeto de estadísticas tiene las columnas de clave IdCliente, IdArtículo, Precio, la densidad se calcula en cada uno de los siguientes prefijos de columna.
  
|Prefijo de columna|Densidad calculada en|  
|---|---|
|(IdCliente)|Filas con valores que se corresponden con IdCliente|  
|(IdCliente, IdArtículo)|Filas con valores que se corresponden con IdCliente e IdArtículo|  
|(IdCliente, IdArtículo, Precio)|Filas con valores que se corresponden con IdCliente, IdArtículo y Precio|  
  
## <a name="restrictions"></a>Restricciones  
 DBCC SHOW_STATISTICS no proporciona estadísticas de índices de almacén de columnas optimizadas en memoria xVelocity o espaciales.  
  
## <a name="permissions-for-includessnoversionincludesssnoversion-mdmd-and-includesssdsincludessssds-mdmd"></a>Permisos para [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y[!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
Para ver el objeto de estadísticas, el usuario propietario de la tabla o el usuario debe ser miembro de la `sysadmin` fija de servidor sysadmin el `db_owner` función fija de base de datos, o la `db_ddladmin` rol fijo de base de datos.
  
SQL Server 2012 SP1 modifica las restricciones de permisos y permite que los usuarios que dispongan del permiso SELECT pueden usar este comando. Tenga en cuenta los siguientes requisitos para que los permisos SELECT sean suficientes para ejecutar el comando:
-   Los usuarios deben tener permisos en todas las columnas del objeto de estadísticas  
-   Los usuarios deben tener permiso en todas las columnas de una condición de filtro (si existe alguna)  
-   La tabla no puede tener una directiva de seguridad de nivel de fila.  
  
Para deshabilitar este comportamiento, use la marca de seguimiento 9485.
  
## <a name="permissions-for-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Permisos para [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] y[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
DBCC SHOW_STATISTICS requiere el permiso SELECT en la tabla o la pertenencia a uno de los siguientes:
-   rol fijo de servidor sysadmin  
-   base de datos fijo db_owner  
-   db_ddladmin, rol fijo de base de datos  
  
## <a name="limitations-and-restrictions-for-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Limitaciones y restricciones para [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] y[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
DBCC SHOW_STATISTICS muestra las estadísticas almacenadas en la base de datos de Shell en el nivel de nodo de Control. No muestra las estadísticas creadas automáticamente por [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de los nodos.
  
DBCC SHOW_STATISTICS no se admite en tablas externas.
  
## <a name="examples-includessnoversionincludesssnoversion-mdmd-and-includesssdsincludessssds-mdmd"></a>Ejemplos: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y[!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
### <a name="a-returning-all-statistics-information"></a>A. Devolver información de todas las estadísticas  
En el ejemplo siguiente se muestra toda la información de estadísticas para la `AK_Address_rowguid` índice de la `Person.Address` tabla el [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] base de datos.
  
```t-sql
DBCC SHOW_STATISTICS ("Person.Address", AK_Address_rowguid);  
GO  
```  
  
### <a name="b-specifying-the-histogram-option"></a>B. Especificar la opción HISTOGRAM  
Esto limita la información de estadísticas mostrada para Customer_LastName a los datos del HISTOGRAMA.
  
```t-sql
DBCC SHOW_STATISTICS ("dbo.DimCustomer",Customer_LastName) WITH HISTOGRAM;  
GO  
```  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Ejemplos: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] y[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="c-display-the-contents-of-one-statistics-object"></a>C. Mostrar el contenido de las estadísticas de un objeto  
 En el ejemplo siguiente se muestra el contenido de las estadísticas de Customer_LastName en la tabla DimCustomer.  
  
```t-sql
-- Uses AdventureWorks  
--First, create a statistics object  
CREATE STATISTICS Customer_LastName   
ON AdventureWorksPDW2012.dbo.DimCustomer (LastName);  
GO  
DBCC SHOW_STATISTICS ("dbo.DimCustomer",Customer_LastName);  
GO  
```  
  
Los resultados muestran el encabezado, el vector de densidad y parte del histograma.
  
![Resultados de DBCC SHOW_STATISTICS](../../t-sql/database-console-commands/media/aps-sql-dbccshow-statistics.JPG "resultados de DBCC SHOW_STATISTICS")
  
## <a name="see-also"></a>Vea también  
[Estadísticas](../../relational-databases/statistics/statistics.md)  
[CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)  
[CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md)  
[DROP STATISTICS & #40; Transact-SQL & #41;](../../t-sql/statements/drop-statistics-transact-sql.md)  
[sp_autostats & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-autostats-transact-sql.md)  
[sp_createstats & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-createstats-transact-sql.md)  
[STATS_DATE & #40; Transact-SQL & #41;](../../t-sql/functions/stats-date-transact-sql.md)  
[UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)  
[Sys.dm_db_stats_properties (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-properties-transact-sql.md)  
[Sys.dm_db_stats_histogram (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md)   

