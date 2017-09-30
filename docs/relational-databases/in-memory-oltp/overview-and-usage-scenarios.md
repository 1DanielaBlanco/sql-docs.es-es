---
title: "Información general y escenarios de uso | Microsoft Docs"
ms.custom: 
ms.date: 04/10/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62c964c5-eae4-4cf1-9024-d5a19adbd652
caps.latest.revision: 5
author: jodebrui
ms.author: jodebrui
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 13128a755dcfd302224a8291a006878a68bdd09f
ms.contentlocale: es-es
ms.lasthandoff: 09/27/2017

---
# <a name="overview-and-usage-scenarios"></a>Información general y escenarios de uso
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

OLTP en memoria es la tecnología principal disponible en SQL Server y Azure SQL Database para optimizar el rendimiento de escenarios de datos transitorios, carga de datos, ingesta de datos y procesamiento de transacciones. En este tema se incluye información general sobre la tecnología y se describen escenarios de uso de OLTP en memoria. Use esta información para determinar si OLTP en memoria es adecuado para la aplicación. El tema concluye con un ejemplo que muestra objetos de OLTP en memoria, hace referencia a una demostración de rendimiento y a recursos que puede usar para los pasos siguientes.

Este artículo trata sobre la tecnología de OLTP en memoria de SQL Server y Azure SQL Database. La siguiente entrada de blog contiene una explicación exhaustivo sobre el rendimiento y los beneficios de utilizar los recursos de Azure SQL Database: 
- [OLTP en memoria en Azure SQL Database](https://azure.microsoft.com/blog/in-memory-oltp-in-azure-sql-database/)

## <a name="in-memory-oltp-overview"></a>Información general de OLTP en memoria

OLTP en memoria puede proporcionar excelentes ganancias de rendimiento para las cargas de trabajo adecuadas. Bwin, un cliente, logró [alcanzar 1,2 millones de solicitudes por segundo](https://blogs.msdn.microsoft.com/sqlcat/2016/10/26/how-bwin-is-using-sql-server-2016-in-memory-oltp-to-achieve-unprecedented-performance-and-scale/) con una sola máquina con SQL Server 2016 en la que ejecutaba OLTP en memoria. Otro cliente, Quorum, logró duplicar su carga de trabajo a la vez que [disminuía en 70% su uso de recursos](https://customers.microsoft.com/en-US/story/quorum-doubles-key-databases-workload-while-lowering-dtu-with-sql-database)mediante el uso de OLTP en memoria en Azure SQL Database. A pesar de que los clientes han visto una ganancia de rendimiento de hasta 30 veces en algunos casos, la ganancia que obtendrá depende de la carga de trabajo.

¿De dónde proviene esta ganancia de rendimiento? Básicamente, OLTP en memoria mejora el rendimiento del procesamiento de transacciones al hacer que la ejecución de las transacciones y el acceso a los datos sea más eficaz y al quitar la contención de bloqueo y bloqueo temporal entre transacciones que se ejecutan de manera simultánea: no es rápido porque se haga en memoria, sino que es rápido porque está optimizado en torno a los datos que están en memoria. Los algoritmos de procesamiento, acceso y almacenamiento de datos se rediseñaron desde el principio para aprovechar las mejoras más recientes en los cálculos de alta simultaneidad y en memoria.

Ahora, solo porque los datos residen en memoria, no significa que los pierda si se produce un error. De manera predeterminada, todas las transacciones son completamente duraderas, lo que significa que tiene las mismas garantías de durabilidad que obtiene para cualquier otra tabla en SQL Server: como parte de la confirmación de transacciones, todos los cambios se escriben en el registro de transacciones en el disco. Si se produce algún error en cualquier momento después de la confirmación de la transacción, los datos se mantienen cuando la base de datos vuelve a estar en línea. Además, OLTP en memoria funciona con todas las funcionalidades de alta disponibilidad y recuperación ante desastres de SQL Server, como AlwaysOn, copia de seguridad/restauración, etc.

Para usar OLTP en memoria en la base de datos, debe usar uno o varios de los siguientes tipos de objetos:

- Las*tablas con optimización para memoria* se usan para almacenar datos de usuario. Declara que una tabla es una tabla con optimización para memoria en el momento de su creación.
- Las*tablas no duraderas* se usan para los datos transitorios, ya sea para el almacenamiento en caché o para un conjunto de resultados intermedio (que reemplaza las tablas temporales tradicionales). Una tabla no duradera es una tabla con optimización para memoria que se declara con DURABILITY=SCHEMA_ONLY, lo que significa que los cambios en estas tablas no generan ningún E/S. Esto evita que consuman recursos de E/S de registro en los casos donde la durabilidad no es tema.
- Los*tipos de tablas con optimización para memoria* se usan para los parámetros con valores de tabla (TVP), así como conjuntos de resultados intermedios en procedimientos almacenados. Se pueden usar en lugar de los tipos de tablas tradicionales. Las variables de tabla y los TVP que se declaran con un tipo de tabla con optimización para memoria heredan las ventajas de las tablas no duraderas con optimización para memoria: acceso eficaz a los datos y no E/S.
- Los*módulos T-SQL compilados de manera nativa* se usan para reducir aún más el tiempo que demora una transacción individual mediante la disminución de los ciclos de CPU que se requieren para procesar las operaciones. Declara un módulo Transact-SQL como compilado de manera nativa en el momento de su creación. En este momento, se pueden compilar de manera nativa los siguientes módulos T-SQL: procedimientos almacenados, desencadenadores y funciones escalares definidas por el usuario.

OLTP en memoria está integrado en SQL Server y Azure SQL Database. Además, y dado que estos objetos tienen un comportamiento muy similar al de sus contrapartes tradicionales, a menudo puede obtener ventajas de rendimiento si solo hace cambios mínimos en la base de datos y la aplicación. Además, puede tener tablas con optimización para memoria y tablas basadas en discos tradicionales en la misma base de datos, y ejecutar consultas entre ambas. Hacia el final de este tema encontrará un script Transact-SQL que muestra un ejemplo de cada uno de estos tipos de objetos.

## <a name="usage-scenarios-for-in-memory-oltp"></a>Escenarios de uso de OLTP en memoria

OLTP en memoria no es un botón rápido mágico y no funciona en todas las cargas de trabajo. Por ejemplo, las tablas con optimización para memoria no disminuyen realmente el uso de la CPU si la mayoría de las consultas ejecutan la agregación en grandes intervalos de datos; son los índices de almacén de columnas los que ayudan en ese escenario.

A continuación, puede ver una lista de escenarios y patrones de aplicaciones en los que se han visto buenos resultados con OLTP en memoria.

### <a name="high-throughput-and-low-latency-transaction-processing"></a>Procesamiento de transacciones de baja latencia y alto rendimiento

Este es el escenario central para el que compilamos OLTP en memoria: se admiten grandes volúmenes de transacciones con una baja latencia coherente para transacciones individuales.

Los escenarios de carga de trabajo comunes son: comercialización de instrumentos financieros, apuestas deportivas, juegos móviles y publicación de anuncios. Otro patrón común que hemos visto es un "catálogo" que se lee o actualiza con frecuencia. Un ejemplo es donde tiene archivos de gran tamaño, cada uno de ellos distribuido sobre un número de nodos en un clúster, y se cataloga la ubicación de cada partición de cada archivo en una tabla con optimización para memoria.

#### <a name="implementation-considerations"></a>Consideraciones de implementación

Use las tablas con optimización para memoria para sus tablas de transacciones principales, es decir, las tablas con las transacciones con rendimiento más crítico. Use los procedimientos almacenados compilados de manera nativa para optimizar la ejecución de la lógica asociada con la transacción comercial. Mientras más lógica pueda insertar en los procedimientos almacenados de la base de datos, más ventajas verá gracias a OLTP en memoria.

Para empezar a trabajar en una aplicación existente:
1. Use el [informe de análisis de rendimiento de transacciones](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md) para identificar los objetos que desea migrar. 
2. Use los asesores de [optimización para memoria](memory-optimization-advisor.md) y [compilación nativa](native-compilation-advisor.md) para ayudar en la migración.

#### <a name="customer-case-studies"></a>Casos prácticos de clientes

- CMC Markets usa OLTP en memoria en SQL Server 2016 para obtener una baja latencia coherente: [Because a second is too long to wait, this financial services firm is updating its trading software now](https://customers.microsoft.com/en-us/story/because-a-second-is-too-long-to-wait-this-financial-services-firm-is-updating-its-trading-software)(Como esperar un segundo es demasiado, esta empresa de servicios financieros está actualizando su software comercial en este momento).
- Derivco usa OLTP en memoria en SQL Server 2016 para admitir un mayor rendimiento y poder manejar los picos en la carga de trabajo: [When an online gaming company doesn’t want to risk its future, it bets on SQL Server 2016](https://customers.microsoft.com/en-us/story/when-an-online-gaming-company-doesnt-want-to-risk-its-future-it-bets-on-sql-server-2016)(Si una empresa de juegos en línea no quiere poner en riesgo su futuro, apuesta por SQL Server 2016).


### <a name="data-ingestion-including-iot-internet-of-things"></a>Ingesta de datos, incluida IoT (Internet de las cosas)

OLTP en memoria es excelente en la ingesta de grandes volúmenes de datos desde distintos orígenes al mismo tiempo. Además, la ingesta de datos en una base de datos de SQL Server suele ser beneficiosa en comparación con otros destinos, porque SQL permite ejecutar realmente rápido las consultas de datos y, además, le permite obtener información en tiempo real.

Los patrones de aplicaciones comunes son: la ingestión de eventos y lecturas de sensores, para permitir la notificación, además del análisis histórico. La administración de actualizaciones por lotes, incluso desde varios orígenes, mientras se minimiza el impacto en la carga de trabajo de lectura simultánea.

#### <a name="implementation-considerations"></a>Consideraciones de implementación

Use una tabla con optimización para memoria para la ingesta de datos. Si la ingesta consta principalmente de inserciones (en lugar de actualizaciones) y el espacio que ocupa el almacenamiento de OLTP en memoria de los datos es una preocupación, puede hacer una de las acciones siguientes:

- Use un trabajo para descargar por lote de manera regular los datos en una tabla basada en discos con un [índice de almacén de columnas en clúster](../indexes/columnstore-indexes-overview.md), a través de un trabajo que hace `INSERT INTO <disk-based table> SELECT FROM <memory-optimized table>`; o bien,
- Use una [tabla temporal con optimización para memoria](../tables/system-versioned-temporal-tables-with-memory-optimized-tables.md) para administrar los datos históricos; en este modo, los datos históricos residen en el disco y es el sistema el que administra el movimiento de los datos.

El repositorio de ejemplos de SQL Server contiene una aplicación de cuadrícula inteligente que usa una tabla temporal con optimización para memoria, un tipo de tabla con optimización para memoria y un procedimiento almacenado compilado de manera nativa para acelerar la ingesta de datos, mientras que se administra el espacio de almacenamiento de OLTP en memoria de los datos del sensor: 

 - [smart-grid-release](https://github.com/Microsoft/sql-server-samples/releases/tag/iot-smart-grid-v1.0) 
 - [smart-grid-source-code](https://github.com/Microsoft/sql-server-samples/tree/master/samples/applications/iot-smart-grid)
 
#### <a name="customer-case-studies"></a>Casos prácticos de clientes

- [Quorum duplica la carga de trabajo de la base de datos clave mientras disminuye el uso en 70% con el uso de OLTP en memoria en Azure SQL Database](http://customers.microsoft.com/story/quorum-doubles-key-databases-workload-while-lowering-dtu-with-sql-database)
- EdgeNet mejoró el rendimiento de la carga de datos por lote y eliminó la necesidad de mantener una caché de nivel intermedio gracias a OLTP en memoria en SQL Server 2014: [Data Services Firm Gains Real-Time Access to Product Data with In-Memory Technology](https://customers.microsoft.com/en-us/story/data-services-firm-gains-real-time-access-to-product-d)(Empresa de servicios de datos obtiene acceso en tiempo real a los datos de productos con la tecnología en memoria)
- Beth Israel Deaconess Medical Center pudo mejorar considerablemente la tasa de ingesta de datos desde los controladores de dominio y manejar los picos en la carga de trabajo con OLTP en memoria en SQL Server 2014: [https://customers.microsoft.com/es-es/story/strengthening-data-security-and-creating-more-time-for]

### <a name="caching-and-session-state"></a>Almacenamiento en caché y estado de sesión

La tecnología de OLTP en memoria hace que SQL sea realmente atractivo para mantener el estado de la sesión (por ejemplo, en una aplicación ASP.NET) y para el almacenamiento en caché.

El estado de sesión de ASP.NET es un caso de uso muy exitoso de OLTP en memoria. Con SQL Server, un cliente estuvo a punto de lograr 1,2 millones de solicitudes por segundo. Mientras tanto, comenzó a usar OLTP en memoria para cumplir con las necesidades de almacenamiento en caché de todas las aplicaciones de nivel intermedio de la empresa. Detalles: [How bwin is using SQL Server 2016 In-Memory OLTP to achieve unprecedented performance and scale](https://blogs.msdn.microsoft.com/sqlcat/2016/10/26/how-bwin-is-using-sql-server-2016-in-memory-oltp-to-achieve-unprecedented-performance-and-scale/)(Cómo bwin usa OLTP en memoria de SQL Server 2016 para obtener un rendimiento y escala sin precedentes)

#### <a name="implementation-considerations"></a>Consideraciones de implementación

Puede usar tablas no duraderas con optimización e memoria como un almacén de clave-valor simple mediante el almacenamiento de un BLOB en una columna varbinary(max). De manera alternativa, puede implementar una memoria caché semiestructurada con [compatibilidad de JSON](https://azure.microsoft.com/blog/json-support-is-generally-available-in-azure-sql-database/) en SQL Server y Azure SQL Database. Por último, puede crear una caché completamente relacional a través de tablas no duraderas con un esquema completamente relacional, incluidas diversas restricciones y tipos de datos.

Comience con un estado de sesión de ASP.NET con optimización para memoria usando los scripts publicados en GitHub para reemplazar los objetos creados por el proveedor de estado de sesión de SQL Server integrado:

- [aspnet-session-state](https://github.com/Microsoft/sql-server-samples/tree/master/samples/applications/aspnet-session-state)

#### <a name="customer-case-studies"></a>Casos prácticos de clientes

- bwin pudo aumentar considerablemente el rendimiento y disminuir la superficie de hardware para el estado de sesión de ASP.NET con OLTP en memoria en SQL Server 2014: [Gaming Site Can Scale to 250,000 Requests Per Second and Improve Player Experience](https://customers.microsoft.com/en-us/story/gaming-site-can-scale-to-250000-requests-per-second-an)(Sitio de juegos puede escalar hasta 250.000 solicitudes por segundo y mejorar la experiencia de los jugadores)
- bwin aumentó incluso más el rendimiento con estado de sesión de ASP.NET e implementó un sistema de almacenamiento de nivel intermedio en toda la empresa con OLTP en memoria en SQL Server 2016: [How bwin is using SQL Server 2016 In-Memory OLTP to achieve unprecedented performance and scale](https://blogs.msdn.microsoft.com/sqlcat/2016/10/26/how-bwin-is-using-sql-server-2016-in-memory-oltp-to-achieve-unprecedented-performance-and-scale/)(Cómo bwin usa OLTP en memoria de SQL Server 2016 para obtener un rendimiento y escala sin precedentes)

### <a name="tempdb-object-replacement"></a>Reemplazo de objeto tempdb

Use las tablas no duraderas y los tipos de tabla con optimización para memoria para reemplazar las tablas #temp basadas en tempdb tradicionales, las variables de tabla y los parámetros con valores de tabla (TVP).

Las tablas no duraderas y las variables de tabla con optimización para memoria normalmente reducen la CPU y quitan completamente E/S del registro en comparación con la tabla #temp y las variables de tabla tradicionales.



#### <a name="implementation-considerations"></a>Consideraciones de implementación

Para comenzar, consulte: [Mejora del rendimiento de la tabla temporal y de variable de tabla mediante optimización de memoria.](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/21/improving-temp-table-and-table-variable-performance-using-memory-optimization/)

#### <a name="customer-case-studies"></a>Casos prácticos de clientes

- Un cliente pudo mejorar el rendimiento en un 40% simplemente reemplazando los TVP tradicionales con TVP con optimización para memoria: [High Speed IoT Data Ingestion Using In-Memory OLTP in Azure](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/04/07/a-technical-case-study-high-speed-iot-data-ingestion-using-in-memory-oltp-in-azure/)(Cómo acelerar la ingesta de datos de IoT con OLTP en memoria en Azure)


### <a name="etl-extract-transform-load"></a>ETL (extracción, transformación, carga)

A menudo, los flujos de trabajo de ETL incluyen cargar datos en una tabla provisional, transformaciones de los datos y su carga en las tablas finales.

#### <a name="implementation-considerations"></a>Consideraciones de implementación

Use tablas no duraderas con optimización para memoria para el almacenamiento provisional de datos. Estas tablas quitan completamente E/S y hacen que el acceso a los datos sea más eficaz.

Si hace transformaciones en la tabla de almacenamiento provisional como parte del flujo de trabajo, puede usar procedimientos almacenados compilados de manera nativa para acelerar estas transformaciones. Si puede hacer estas transformaciones en paralelo, obtendrá ventajas adicionales de escalabilidad a partir de la optimización de memoria.

## <a name="sample-script"></a>Script de ejemplo

Antes de que pueda comenzar a usar OLTP en memoria, debe crear un grupo de archivos MEMORY_OPTIMIZED_DATA. Además, se recomienda que use el nivel 130 (o superior) de compatibilidad de base de datos y establezca la opción MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT de base de datos en ON.

Puede usar el script que se encuentra en la siguiente ubicación para crear el grupo de archivos en la carpeta de datos predeterminada y configurar los valores recomendados:

- [enable-in-memory-oltp.sql](https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/in-memory/t-sql-scripts/enable-in-memory-oltp.sql)

El script siguiente ilustra los objetos de OLTP en memoria que puede crear en la base de datos:
  
     -- configure recommended DB option
     ALTER DATABASE CURRENT SET MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT=ON
     GO
     -- memory-optimized table
     CREATE TABLE dbo.table1
     ( c1 INT IDENTITY PRIMARY KEY NONCLUSTERED,
       c2 NVARCHAR(MAX))
     WITH (MEMORY_OPTIMIZED=ON)
     GO
     -- non-durable table
     CREATE TABLE dbo.temp_table1
     ( c1 INT IDENTITY PRIMARY KEY NONCLUSTERED,
       c2 NVARCHAR(MAX))
     WITH (MEMORY_OPTIMIZED=ON,
           DURABILITY=SCHEMA_ONLY)
     GO
     -- memory-optimized table type
     CREATE TYPE dbo.tt_table1 AS TABLE
     ( c1 INT IDENTITY,
       c2 NVARCHAR(MAX),
       is_transient BIT NOT NULL DEFAULT (0),
       INDEX ix_c1 HASH (c1) WITH (BUCKET_COUNT=1024))
     WITH (MEMORY_OPTIMIZED=ON)
     GO
     -- natively compiled stored procedure
     CREATE PROCEDURE dbo.usp_ingest_table1
       @table1 dbo.tt_table1 READONLY
     WITH NATIVE_COMPILATION, SCHEMABINDING
     AS
     BEGIN ATOMIC
         WITH (TRANSACTION ISOLATION LEVEL=SNAPSHOT,
               LANGUAGE=N'us_english')
     
       DECLARE @i INT = 1
     
       WHILE @i > 0
       BEGIN
         INSERT dbo.table1
         SELECT c2
         FROM @table1
         WHERE c1 = @i AND is_transient=0
     
         IF @@ROWCOUNT > 0
           SET @i += 1
         ELSE
         BEGIN
           INSERT dbo.temp_table1
           SELECT c2
           FROM @table1
           WHERE c1 = @i AND is_transient=1
     
           IF @@ROWCOUNT > 0
             SET @i += 1
           ELSE
             SET @i = 0
         END
       END
     
     END
     GO
     -- sample execution of the proc
     DECLARE @table1 dbo.tt_table1
     INSERT @table1 (c2, is_transient) VALUES (N'sample durable', 0)
     INSERT @table1 (c2, is_transient) VALUES (N'sample non-durable', 1)
     EXECUTE dbo.usp_ingest_table1 @table1=@table1
     SELECT c1, c2 from dbo.table1
     SELECT c1, c2 from dbo.temp_table1
     GO
   

## <a name="resources-to-learn-more"></a>Recursos para obtener más información:

- [Inicio rápido 1: Tecnologías de OLTP en memoria para acelerar el rendimiento de T-SQL](http://msdn.microsoft.com/library/mt694156.aspx)
- Puede encontrar una demostración de rendimiento con OLTP en memoria en: [in-memory-oltp-perf-demo-v1.0](https://github.com/Microsoft/sql-server-samples/releases/tag/in-memory-oltp-demo-v1.0)
- [Vídeo de 17 minutos que explica OLTP en memoria y exhibe una demostración](https://www.youtube.com/watch?v=l5l5eophmK4) (la demostración está en el minuto 8:25)
- [Script para habilitar OLTP en memoria y establecer las opciones recomendadas](https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/in-memory/t-sql-scripts/enable-in-memory-oltp.sql)
- [Documentación principal de OLTP en memoria](in-memory-oltp-in-memory-optimization.md)
- [Beneficios del uso de los recursos y el rendimiento de OLTP en memoria en Azure SQL Database](https://azure.microsoft.com/blog/in-memory-oltp-in-azure-sql-database/)
- [Mejora del rendimiento de la tabla temporal y de variable de tabla mediante optimización de memoria](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/21/improving-temp-table-and-table-variable-performance-using-memory-optimization/)
[Optimizar el rendimiento con las tecnologías en memoria en SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-in-memory)
- [Tablas temporales con control de versiones del sistema con tablas con optimización para memoria](../tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)
- [OLTP en memoria y los patrones de carga de trabajo comunes y consideraciones para la migración](http://msdn.microsoft.com/library/dn673538.aspx). 

