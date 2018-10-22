---
title: Novedades de SQL Server 2019 | Microsoft Docs
ms.custom: ''
ms.date: 09/27/2018
ms.prod: sql-server-2018
ms.reviewer: ''
ms.technology:
- server-general
ms.topic: article
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 015a6d65f1d225ab5a8752352d41fd2201f871b5
ms.sourcegitcommit: ef78cc196329a10fc5c731556afceaac5fd4cb13
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2018
ms.locfileid: "49461120"
---
# <a name="whats-new-in-sql-server-2019"></a>Novedades de SQL Server 2019

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](..\includes\sssqlv15-md.md)] se basa en versiones anteriores para potenciar SQL Server como una plataforma que proporciona diversas opciones de lenguajes de desarrollo, tipos de datos, entornos locales o en la nube, y sistemas operativos. En este artículo se resumen las novedades de SQL Server 2019. Para obtener más información y problemas conocidos, consulte [Notas de la versión de SQL Server 2019](sql-server-ver15-release-notes.md).

**Pruebe SQL Server 2019.**
- [![Descargar desde el Centro de evaluación](../includes/media/download2.png)](http://go.microsoft.com/fwlink/?LinkID=862101) [Descargar SQL Server 2019 para instalar en Windows](http://go.microsoft.com/fwlink/?LinkID=862101)
- Instalar en Linux para [Red Hat Enterprise Server](../linux/quickstart-install-connect-red-hat.md), [SUSE Linux Enterprise Server](../linux/quickstart-install-connect-suse.md) y [Ubuntu](../linux/quickstart-install-connect-ubuntu.md)
- [Ejecutar SQL Server 2019 en Docker](../linux/quickstart-install-connect-docker.md)

## <a name="ctp-20"></a>CTP 2.0 

Community Technology Preview (CTP) 2.0 es la primera versión pública de [!INCLUDE[sql-server-2019](..\includes\sssqlv15-md.md)]. En [!INCLUDE[sql-server-2019](..\includes\sssqlv15-md.md)] CTP 2.0 se han incorporado o mejorado las siguientes características.

- [Clústeres de macrodatos](#bigdatacluster)
  - Implementación de un clúster de macrodatos con contenedores SQL y Spark Linux en Kubernetes
  - Acceso a los macrodatos desde HDFS
  - Ejecución de análisis avanzado y aprendizaje automático con Spark
  - Uso de Spark Streaming en grupos de datos a datos de SQL
  - Uso de Azure Data Studio para ejecutar libros de consulta que proporcionan una experiencia de cuadernos

- [Motor de base de datos](#databaseengine)
  - Compatibilidad con UTF-8
  - Característica Resumable online index create que permite crear índices que pueden reanudarse después de una interrupción
  - Compilación y recompilación de índices en línea de almacén de columnas en clúster
  - Always Encrypted con enclaves seguros
  - Procesamiento de consultas inteligentes
  - Extensión de programación del lenguaje Java
  - Características de SQL Graph
  - Configuración de ámbito de base de datos para operaciones DDL en línea y reanudables
  - Grupos de disponibilidad Always On: redireccionamiento de la conexión de réplicas secundarias
  - Clasificación y detección de datos integradas de forma nativa en SQL Server
  - Compatibilidad ampliada con los dispositivos de memoria persistente
  - Compatibilidad con las estadísticas de almacén de columnas en `DBCC CLONEDATABASE`
  - Nuevas opciones agregadas a `sp_estimate_data_compression_savings`
  - Clústeres de conmutación por error de Machine Learning Services en SQL Server
  - Infraestructura de generación de perfiles ligera de consultas habilitada de forma predeterminada
  - Nuevos conectores de PolyBase
  - Nueva función del sistema `sys.dm_db_page_info` que devuelve información de la página

- [SQL Server en Linux](#sqllinux)
  - Compatibilidad con la replicación
  - Compatibilidad con el Coordinador de transacciones distribuidas de Microsoft (MSDTC)
  - Grupo de disponibilidad Always On en contenedores de Docker con Kubernetes
  - Compatibilidad de OpenLDAP con proveedores terceros de AD
  - Machine Learning en Linux
  - Nuevo registro de contenedor
  - Nuevas imágenes de contenedor basadas en RHEL
  - Notificación de presión de memoria

- [Master Data Services](#mds)
  - Controles de Silverlight reemplazados

- [Seguridad](#security)
  - Administración de certificados en el Administrador de configuración de SQL Server

- [Herramientas](#tools)
  - SQL Server Management Studio (SSMS) 18.0 (versión preliminar)
  - Azure Data Studio

Siga leyendo para obtener más detalles sobre estas características.

## <a id="bigdatacluster"></a>Clústeres de macrodatos

Los [clústeres de macrodatos](../big-data-cluster/big-data-cluster-overview.md) de [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] habilitan nuevos escenarios, como los siguientes:

- Implementación de un clúster de macrodatos con contenedores [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] y Spark Linux en Kubernetes
- Acceso a los macrodatos desde HDFS
- Ejecución de análisis avanzado y aprendizaje automático con Spark
- Uso de Spark Streaming en grupos de datos a datos de SQL
- Ejecución de libros de consulta que proporcionan una experiencia de cuadernos en [**Azure Data Studio**](../sql-operations-studio/what-is.md)
  
[!INCLUDE [Big Data Clusters preview](../includes/big-data-cluster-preview-note.md)]

## <a id="databaseengine"></a> Motor de base de datos

CTP 2.0 presenta o mejora las siguientes nuevas características en [!INCLUDE[ssdeNoVersion](../includes/ssdenoversion_md.md)].

### <a name="database-compatibility-level"></a>El nivel de compatibilidad de la base de datos.

Se agregó el nivel de compatibilidad **COMPATIBILITY_LEVEL 150** de base de datos. Si quiere habilitarlo para una base de datos de usuario específica, ejecute lo siguiente:

   ```sql
   ALTER DATABASE database_name SET COMPATIBILITY_LEVEL =  150;
   ```

### <a name="utf-8-support"></a>Compatibilidad con UTF-8

Compatibilidad total para utilizar la ampliamente utilizada codificación de caracteres UTF-8 como codificación de importación o exportación, o bien como intercalación columna o base de datos para datos de texto. UTF-8 se permite en los tipos de datos `CHAR` y `VARCHAR`, y se habilita al crear o cambiar la intercalación de un objeto a una intercalación con el sufijo `UTF8`. 

Por ejemplo, de `LATIN1_GENERAL_100_CI_AS_SC` a `LATIN1_GENERAL_100_CI_AS_SC_UTF8`. UTF-8 solo está disponible para las intercalaciones de Windows que admiten caracteres adicionales, tal y como se presentó en SQL Server 2012. `NCHAR` y `NVARCHAR` solo permiten la codificación UTF-16 y no se han realizado cambios.

Esta característica puede proporcionar ahorros significativos de almacenamiento, según el juego de caracteres que se esté usando. Por ejemplo, si se cambia un tipo de datos de columna existente con cadenas ASCII de `NCHAR(10)` a `CHAR(10)` utilizando una intercalación habilitada para UTF-8, se reducen a la mitad los requisitos de almacenamiento. Esto se debe a que `NCHAR(10)` requiere 22 bytes para el almacenamiento, mientras que `CHAR(10)` necesita 12 bytes para la misma cadena Unicode.

### <a name="resumable-online-index-create"></a>Característica Resumable online index create

- La característica **Resumable online index create** permite que una operación de creación de índices se pause y se reanude más adelante desde el punto en que la operación se pausó o falló, en lugar de tener que reiniciarla desde el principio.

  Resumable online index create admite los escenarios siguientes:
  - Reanudar una operación de creación de índices después de un error de creación de índices, por ejemplo, después de una conmutación por error de base de datos o de quedarse sin espacio en disco.
  - Pausar una operación de creación de índices en curso y reanudarla más adelante permitiendo que temporalmente se liberen los recursos del sistema según sea necesario, y reanudar esta operación más tarde.
  - Crear índices grandes sin usar tanto espacio de registro y una transacción de larga ejecución que bloquea otras actividades de mantenimiento truncando el registro.

  En el caso de que se produzca un error de creación de índices, sin esta característica, debe ejecutarse de nuevo una operación de creación de índices en línea y reiniciarla desde el principio.

Con esta versión, se amplía la funcionalidad reanudable agregando esta característica a las [recompilaciones de índices en línea reanudables](http://azure.microsoft.com/blog/modernize-index-maintenance-with-resumable-online-index-rebuild/).

Además, esta característica se puede establecer como predeterminada en una base de datos específica mediante la [configuración predeterminada de ámbito de base de datos para operaciones DDL en línea y reanudables](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).

Para obtener más información, consulte [Característica Resumable online index create](../t-sql/statements/create-index-transact-sql.md#resumable-indexes).

### <a name="build-and-rebuild-clustered-columnstore-indexes-online"></a>Compilación y recompilación de índices en línea de almacén de columnas en clúster

Convierta tablas de almacén de filas en formato de almacén de columnas. El proceso de creación de índices de almacén de columnas en clúster (CCI) se realizaba sin conexión en las versiones anteriores de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], y había que detener todos los cambios mientras se creaban estos índices CCI. Con [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] y [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] puede crear o volver a crear índices CCI en línea. La carga de trabajo no se bloqueará y todos los cambios realizados en los datos subyacentes se agregan de forma transparente en la tabla de almacén de columnas de destino. Estos son algunos ejemplos de nuevas instrucciones [!INCLUDE[tsql](../includes/tsql-md.md)] que se pueden usar:

  ```sql
  CREATE CLUSTERED COLUMNSTORE INDEX cci
    ON <tableName>
    WITH (ONLINE = ON);
  ```

  ```sql
  ALTER INDEX cci
    ON <tableName>
    REBUILD WITH (ONLINE = ON);
  ```

### <a name="always-encrypted-with-secure-enclaves"></a>Always Encrypted con enclaves seguros

Expande Always Encrypted con cifrado in situ y cálculos enriquecidos. Las expansiones se producen por la habilitación de los cálculos en datos de texto simple, dentro de un enclave seguro en el servidor.

Las operaciones criptográficas incluyen el cifrado de columnas y la rotación de claves de cifrado de columna. Estas operaciones ahora se pueden emitir utilizando [!INCLUDE[tsql](../includes/tsql-md.md)] y no requieren que los datos se mueven fuera de la base de datos. Los enclaves seguros proporcionan Always Encrypted a un conjunto más amplio de escenarios que tienen los dos siguientes requisitos:  

- La demanda de que la información confidencial esté protegida de los usuarios con privilegios elevados, pero no autorizados, como los administradores de base de datos, los administradores del sistema, los operadores en la nube o el malware.
- El requisito de que se admitan cálculos enriquecidos en datos protegidos dentro del sistema de base de datos.

Para obtener más información, consulte [Always Encrypted con enclaves seguros](../relational-databases/security/encryption/always-encrypted-enclaves.md).

> [!NOTE]
> Always Encrypted con enclaves seguros solo está disponible en el sistema operativo Windows.

### <a name="intelligent-query-processing"></a>Procesamiento de consultas inteligentes

- Los **comentarios de concesión de memoria del modo de fila** se expanden en la característica de comentarios de concesión de memoria presentada en [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] al ajustar los tamaños de concesión de memoria tanto para los operadores del modo de proceso por lotes como del modo de fila.  En el caso de una condición de concesión de memoria excesiva, si la memoria concedida es más de dos veces el tamaño de la memoria usada real, los comentarios de concesión de memoria volverán a calcular la concesión de memoria. Por tanto, las ejecuciones consecutivas solicitarán menos memoria. En el caso de las concesiones de memoria de tamaño insuficiente que provocan un desbordamiento en disco, los comentarios de concesión de memoria desencadenarán un nuevo cálculo de la concesión de memoria. Por tanto, las ejecuciones consecutivas solicitarán más memoria. Esta característica está habilitada de forma predeterminada en el nivel de compatibilidad de base de datos 150.

- La función **Approximate COUNT DISTINCT**devuelve el número aproximado de valores no nulos únicos de un grupo. Esta función está diseñada para usarse en escenarios de macrodatos. Además, está optimizada para las consultas donde se cumplen todas las condiciones siguientes:
   - Tiene acceso a conjuntos de datos de, al menos, millones de filas.
   - Agrega una columna o varias columnas con muchos valores distintos.
   - La capacidad de respuesta es más importante que la precisión absoluta.
      - `APPROX_COUNT_DISTINCT` devuelve los resultados que se encuentran normalmente dentro del 2 % de la respuesta exacta.
      - Y también devuelve la respuesta aproximada en una pequeña fracción del tiempo necesario para la respuesta exacta.

- El **modo de proceso por lotes en el almacén de filas** ya no requiere que un índice de almacén de columnas procese una consulta por lotes. El modo de proceso por lotes permite a los operadores de consulta trabajar en un conjunto de filas, en lugar de fila por fila. Esta característica está habilitada de forma predeterminada en el nivel de compatibilidad de base de datos 150. El modo de proceso por lotes mejora la velocidad de las consultas que acceden a tablas de almacén de filas cuando se cumplen todas estas condiciones:
   - La consulta utiliza operadores analíticos como combinaciones u operadores de agregación.
   - La consulta implica 100 000 o más filas.
   - La consulta está enlazado a la CPU, en lugar de a los datos de entrada/salida.
   - La creación y el uso de un índice de almacén de columnas tendría una de las siguientes desventajas:
      - Agregaría demasiada sobrecarga a la consulta.
      - O bien, no sería factible porque la aplicación depende de una característica que no es compatible aún con los índices de almacén de columnas.

- La **compilación diferida de variables de tabla** mejora la calidad del plan y el rendimiento general de las consultas que hacen referencia a las variables de tabla. Durante la optimización y la compilación inicial, esta característica propagará las estimaciones de cardinalidad que se basan en los recuentos de filas de variables de tabla reales.  Con la compilación diferida de variables de tabla, la compilación de una instrucción que hace referencia a una variable de tabla se difiere hasta la primera ejecución real de la instrucción. Esta característica está habilitada de forma predeterminada en el nivel de compatibilidad de base de datos 150.

Para usar el procesamiento de consultas inteligentes, establezca la base datos `COMPATIBILITY_LEVEL = 150`.

### <a id="programmability"></a> Extensiones de programación del lenguaje Java

- **Extensión del lenguaje Java (versión preliminar)**: use la extensión del lenguaje Java para ejecutar código de Java en [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. En [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)], esta extensión está instalada cuando se agrega la característica "Machine Learning Services (en base de datos)" a la instancia de SQL Server.

### <a id="sqlgraph"></a> Características de SQL Graph

- La **compatibilidad de coincidencias en el DML** `MERGE` permite especificar las relaciones de gráfico en una sola instrucción, en lugar de las instrucciones `INSERT`,`UPDATE` o `DELETE`. Combine los datos de gráfico actuales de las tablas perimetrales o de nodo con nuevos datos mediante los predicados `MATCH` en la instrucción `MERGE`. Esta característica permite escenarios `UPSERT` en tablas perimetrales. Los usuarios ahora pueden usar una instrucción merge única para insertar un borde nuevo o actualizar uno existente entre dos nodos.

- Las **restricciones perimetrales** se presentaron para las tablas perimetrales en SQL Graph. Las tablas perimetrales pueden conectarse a cualquier otro nodo en la base de datos. Con la introducción de las restricciones perimetrales, ahora puede aplicar algunas restricciones en este comportamiento. La nueva restricción `CONNECTION` puede utilizarse para especificar el tipo de nodos a la que una tabla perimetral determinada podrá conectarse en el esquema.

### <a name="database-scoped-default-setting-for-online-and-resumable-ddl-operations"></a>Configuración predeterminada de ámbito de base de datos para operaciones DDL en línea y reanudables 

- La **configuración predeterminada de ámbito de base de datos para las operaciones DDL en línea y reanudables** permite una configuración de comportamiento predeterminado en las operaciones de índice `ONLINE` y `RESUMABLE` en el nivel de base de datos, en lugar de definir estas opciones en cada instrucción DDL de índice, como recompilaciones o creaciones de índices.

- Establezca estos valores predeterminados mediante las opciones de configuración de ámbito de base de datos `ELEVATE_ONLINE` y `ELEVATE_RESUMABLE`. Ambas opciones harán que el motor eleve automáticamente las operaciones compatibles a la ejecución de índices ONLINE o RESUMABLE. Puede habilitar los siguientes comportamientos con estas opciones:

  - La opción `FAIL_UNSUPPORTED` permite todas las operaciones de índices en línea o reanudables y las operaciones de índices con errores que no se admiten para las opciones en línea o reanudables.
  - La opción `WHEN_SUPPPORTED` permite las operaciones admitidas en línea o reanudables y ejecutan operaciones no admitidas de índices sin conexión o no reanudables.
  - La opción `OFF` permite el comportamiento actual de la ejecución de todas las operaciones de índices sin conexión y no reanudables, salvo que se especifique explícitamente lo contrario en la instrucción DDL.

Para invalidar la configuración predeterminada, incluya la opción ONLINE o RESUMABLE en los comandos de recompilación y creación de índices.  

Sin esta característica, hay que especificar las opciones en línea y reanudables directamente en la instrucción DDL de índice, como la recompilación y la creación de índices.

Más información: para obtener más información sobre las opciones reanudables de índices, consulte [Característica Resumable online index create](http://azure.microsoft.com/blog/resumable-online-index-create-is-in-public-preview-for-azure-sql-db/).

### <a id="ha"></a>Grupos de disponibilidad Always On: más réplicas sincrónicas 

- **Hasta cinco réplicas sincrónicas**: [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] aumenta el número máximo de réplicas sincrónicas en 5, de las 3 que eran en [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. Puede configurar este grupo de 5 réplicas para que habilitar la conmutación automática por error dentro del grupo. Hay 1 réplica principal, además de 4 réplicas secundarias sincrónicas.

- **Redireccionamiento de la conexión de réplicas de secundaria a principal**: permite que las conexiones de las aplicaciones cliente se dirijan a la réplica principal, independientemente del servidor de destino especificado en la cadena de conexión. Esta funcionalidad permite el redireccionamiento de la conexión sin un agente de escucha. Use el redireccionamiento de la conexión de réplicas de secundaria a principal en los casos siguientes:

  - La tecnología del clúster no ofrece una funcionalidad de agente de escucha.
  - Una configuración de múltiples subredes en la que el redireccionamiento se vuelve complejo.
  - Escenarios de escalado horizontal de lectura o de recuperación ante desastres en los que el tipo de clúster es `NONE`.

Para obtener más información, consulte [Secondary to primary replica read/write connection redirection (Always On Availability Groups)](../database-engine/availability-groups/windows/secondary-replica-connection-redirection-always-on-availability-groups.md) (Redireccionamiento de la conexión de lectura/escrita de réplicas de secundaria a principal [Grupos de disponibilidad Always On]).

### <a name="data-discovery-and-classification"></a>Clasificación y detección de datos

La característica de clasificación y detección de datos proporciona funcionalidades avanzadas que se integran de forma nativa en [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Clasificar y etiquetar la información más confidencial proporciona las siguientes ventajas:
- Ayuda a cumplir los requisitos de cumplimiento reglamentario y los estándares de privacidad de datos.
- Admite escenarios de seguridad, como la supervisión (auditoría) y las alertas por accesos anómalos a información confidencial.
- Resulta más fácil identificar donde reside la información confidencial de la empresa, para que los administradores pueden adoptar los pasos adecuados para proteger la base de datos.

Para obtener más información, consulte [Clasificación y detección de datos de SQL](../relational-databases/security/sql-data-discovery-and-classification.md).

La [auditoría](../relational-databases/security/auditing/sql-server-audit-database-engine.md) también se ha mejorado para incluir un nuevo campo en el registro de auditoría denominado `data_sensitivity_information`, que registra las clasificaciones de confidencialidad (etiquetas) de los datos reales que devuelve la consulta. Para obtener información detallada y ejemplos, vea [ADD SENSITIVITY CLASSIFICATION (Transact-SQL)](../t-sql/statements/add-sensitivity-classification-transact-sql.md).

>[!NOTE]
>No hay ningún cambio en cuanto a cómo se habilita la auditoría. Hay un nuevo campo en los registros de auditoría, `data_sensitivity_information`, que registra las clasificaciones de confidencialidad (etiquetas) de los datos reales que devuelve la consulta. Consulte [Auditoría del acceso a datos confidenciales](https://docs.microsoft.com/azure/sql-database/sql-database-data-discovery-and-classification#subheading-3).

### <a name="expanded-support-for-persistent-memory-devices"></a>Compatibilidad ampliada con los dispositivos de memoria persistente

Ahora, cualquier archivo [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] que se coloque en un dispositivo de memoria persistente puede usarse en el modo *habilitado*. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] accede directamente al dispositivo, de modo que ignora la pila de almacenamiento del sistema operativo mediante operaciones memcpy eficaces. Este modo mejora el rendimiento porque permite una entrada/salida de latencia baja en estos dispositivos.
    - Estos son algunos ejemplos de archivos [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:
        - Archivos de base de datos
        - Archivos de registro de transacciones
        - Archivos de punto de control de OLTP en memoria
    - La memoria persistente también se denomina "memoria de la clase de almacenamiento".
    - A la memoria persistente se le conoce informalmente como *pmem* en algunos sitios web de terceros.

> [!NOTE]
> En esta versión preliminar, la habilitación de archivos en los dispositivos de memoria persistente solo está disponible en Linux. SQL Server en Windows es compatible con los dispositivos de memoria persistente a partir de SQL Server 2016.

### <a name="support-for-columnstore-statistics-in-dbcc-clonedatabase"></a>Compatibilidad con las estadísticas de almacén de columnas en DBCC CLONEDATABASE

`DBCC CLONEDATABASE` crea una copia de solo esquema de una base de datos que incluye todos los elementos necesarios para solucionar problemas de rendimiento de consultas sin copiar los datos.  En versiones anteriores de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], el comando no copió las estadísticas necesarias para solucionar con precisión los problemas de las consultas del índice de almacén de columnas y se tuvieron que realizar pasos manuales para capturar esta información. Ahora en [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)], DBCC CLONEDATABASE captura automáticamente los blobs de estadísticas de índices de almacén de columnas, por lo que no será necesario realizar ningún paso manual.

### <a name="new-options-added-to-spestimatedatacompressionsavings"></a>Nuevas opciones agregadas a sp_estimate_data_compression_savings

`sp_estimate_data_compression_savings` devuelve el tamaño actual del objeto solicitado y calcula el tamaño del objeto para el estado de compresión solicitado.  Actualmente, este procedimiento admite tres opciones: `NONE`, `ROW` y `PAGE`. SQL Server 2019 presenta dos opciones nuevas: `COLUMNSTORE` y `COLUMNSTORE_ARCHIVE`. Estas nuevas opciones permiten estimar los ahorros de espacio si se crea un índice de almacén de columnas se crea la tabla mediante la compresión de almacén de columnas estándar o de archivo.

### <a id="ml"></a> Modelado basado en particiones y clústeres de conmutación por error de Machine Learning Services en SQL Server

- **Modelado basado en particiones**: procese scripts externos por partición de los datos mediante los nuevos parámetros agregados a `sp_execute_external_script`. Esta funcionalidad admite el aprendizaje de muchos modelos pequeños (un modelo por cada partición de datos) en lugar de uno grande.

- **Clúster de conmutación por error de Windows Server**: configure la alta disponibilidad de Machine Learning Services en un clúster de conmutación por error de Windows Server.

Para obtener más información, consulte [Novedades de SQL Server Machine Learning Services](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md).

### <a name="lightweight-query-profiling-infrastructure-enabled-by-default"></a>Infraestructura de generación de perfiles ligera de consultas habilitada de forma predeterminada

La infraestructura de generación de perfiles ligera de consultas (LWP) proporciona datos de rendimiento de consulta de forma más eficaz que con las tecnologías de generación de perfiles estándar. La generación de perfiles ligera ahora está habilitada de forma predeterminada. Se presentó en [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] SP1. La generación de perfiles ligera ofrece un mecanismo de recopilación de estadísticas de ejecución de consultas con una sobrecarga esperada del 2 % de CPU, en comparación con una sobrecarga de hasta un 75 % de CPU con el mecanismo de generación de perfiles de consultas estándar. En versiones anteriores, estaba desactivada de forma predeterminada. Los administradores de base de datos pueden habilitarla con la función [trace flag 7412](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md). 

Para obtener más información sobre la generación de perfiles ligera, consulte [Developers Choice: Query progress – anytime, anywhere](http://blogs.msdn.microsoft.com/sql_server_team/query-progress-anytime-anywhere/) (Elección de los desarrolladores: progreso de la consulta, en cualquier momento y en cualquier lugar).

### <a id="polybase"></a>Nuevos conectores de PolyBase

- **Nuevos conectores de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], Oracle, Teradata y MongoDB**: [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] presenta nuevos conectores de datos externos para [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], Oracle, Teradata y MongoDB.

### <a name="new-sysdmdbpageinfo-system-function-returns-page-information"></a>Nueva función del sistema sys.dm_db_page_info que devuelve información de la página

`sys.dm_db_page_info(database_id, file_id, page_id, mode)` devuelve información sobre una página de una base de datos. La función devuelve una fila que contiene la información de encabezado en la página, incluidos `object_id`, `index_id` y `partition_id`. Esta función reemplaza la necesidad de usar `DBCC PAGE` en la mayoría de los casos.  

Para facilitar la solución de problemas de esperas relacionadas con la página, también se agregó una nueva columna denominada "page_resource" a `sys.dm_exec_requests` y `sys.sysprocesses`. Esta nueva columna permite unir `sys.dm_db_page_info` a estas vistas a través de otra nueva función del sistema: `sys.fn_PageResCracker`. Vea el siguiente script como ejemplo:

```sql
SELECT page_info.* 
FROM sys.dm_exec_requests AS d 
  CROSS APPLY sys.fn_PageResCracker(d.page_resource) AS r
  CROSS APPLY sys.dm_db_page_info(r.db_id, r.file_id, r.page_id,'DETAILED')
    AS page_info;
```

## <a id="sqllinux"></a> SQL Server en Linux

- **Compatibilidad con la replicación**: [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] admite la replicación de SQL Server en Linux. Una máquina virtual Linux con el Agente SQL puede ser un editor, distribuidor o suscriptor. 

  Cree los siguientes tipos de publicaciones:
  - Transaccional
  - Snapshot
  - Mezcla

  Configure la replicación [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] o use [procedimientos almacenados de replicación](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).

- **Compatibilidad con el Coordinador de transacciones distribuidas de Microsoft (MSDTC)**: SQL Server 2019 en Linux es compatible con el Coordinador de transacciones distribuidas de Microsoft (MSDTC). Para obtener más información, consulte [How to configure MSDTC on Linux](../linux/sql-server-linux-configure-msdtc.md) (Cómo configurar el Coordinador de transacciones distribuidas de Microsoft (MSDTC) en Linux).

- **Grupo de disponibilidad Always On en contenedores de Docker con Kubernetes**: Kubernetes puede orquestar contenedores que ejecutan instancias de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] para proporcionar un conjunto de bases de datos de alta disponibilidad con grupos de disponibilidad Always On de SQL Server. Un operador de Kubernetes implementa un objeto StatefulSet incluyendo un contenedor con el **contenedor mssql-server** y un monitor de estado.

- **Compatibilidad de OpenLDAP con proveedores terceros de AD**: [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] en Linux es compatible con OpenLDAP, que permite a los proveedores terceros unirse a Active Directory.

- **Machine Learning en Linux**: Machine Learning Services (en base de datos) en SQL Server 2019 ahora es compatible con Linux. Entre esta compatibilidad se encuentra el procedimiento almacenado `sp_execute_external_script`. Para obtener instrucciones sobre cómo instalar Microsoft Machine Learning Services en Linux, consulte [Instalar SQL Server 2019 Machine Learning Services (R, Python y Java) en Linux](../linux/sql-server-linux-setup-machine-learning.md) (Instalación de Machine Learning Services en SQL Server 2019 (R, Python y Java) en Linux).

- **Nuevo registro de contenedor**: todas las imágenes de contenedor de [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] y [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] ahora se encuentran en Microsoft Container Registry. Microsoft Container Registry es el registro de contenedor oficial para la distribución de los contenedores de producto de Microsoft. Además, ahora se publican imágenes certificadas basadas en RHEL.

  - Microsoft Container Registry: `mcr.microsoft.com/mssql/server:vNext-CTP2.0`
  - Imágenes de contenedor certificadas basadas en RHEL: `mcr.microsoft.com/mssql/rhel/server:vNext-CTP2.0`

## <a id="mds"></a> Master Data Services (MDS)

- **Controles de Silverlight reemplazados por HTML**: el portal de Master Data Services (MDS) ya no depende de Silverlight. Todos los componentes de Silverlight anteriores se han reemplazado por controles HTML.

## <a id="security"></a>Seguridad

- **Administración de certificados en el Administrador de configuración de SQL Server**: los certificados SSL/TLS se utilizan ampliamente para proteger el acceso a instancias de SQL Server. La administración de certificados ahora está integrada ahora en el Administrador de configuración de SQL Server, lo que simplifica tareas comunes como las siguientes:

  - Ver y validar los certificados instalados en una instancia de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 
  - Ver certificados a punto de expirar
  - Implementar certificados en máquinas que participan en grupos de disponibilidad Always On (desde el nodo que contiene la réplica principal).
  - Implementar certificados en máquinas que participan en una instancia de clúster de conmutación por error (desde el nodo activo).

  > [!NOTE]
  > El usuario debe tener permisos de administrador en todos los nodos de clúster.

## <a id="tools"></a>Herramientas

- [**Azure Data Studio**](../azure-data-studio/what-is.md): publicado anteriormente con el nombre en versión preliminar de SQL Operations Studio, Azure Data Studio es una herramienta de escritorio ligera, moderna, de código abierto y multiplataforma con la que se pueden llevar a cabo las tareas más comunes de administración y desarrollo de datos. Con Azure Data Studio puede conectarse a SQL Server local y en la nube en Windows, macOS y Linux. Azure Data Studio permite realizar lo siguiente:

  - Editar y ejecutar consultas en un entorno de desarrollo moderno con la posibilidad de usar IntelliSense de forma sumamente rápida, con fragmentos de código y con integración del control de código fuente  
  - Visualizar rápidamente datos con gráficos integrados de los conjuntos de resultados  
  - Crear paneles personalizados de los servidores y las bases de datos mediante widgets personalizables  
  - Administrar fácilmente su entorno más amplio con el terminal integrado  
  - Analizar datos en una experiencia de cuadernos integrada basada en Jupyter  
  - Mejorar la experiencia con las extensiones y los temas personalizados  
  - Explorar los recursos de Azure con un explorador de recursos y una suscripción integrados.
  - Admite escenarios que usen el clúster de macrodatos de SQL Server.


- [**SQL Server Management Studio (SSMS) 18.0 (versión preliminar)**](../ssms/sql-server-management-studio-ssms.md)

  - Compatibilidad con [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]
  - Compatibilidad con Always Encrypted con enclaves seguros
  - Tamaño de descarga más pequeño
  - Se basa ahora en el shell aislado de Visual Studio 2017
  - Para ver una lista completa, consulte el [registro de cambios de SSMS](../ssms/sql-server-management-studio-changelog-ssms.md).

## <a name="other-services"></a>Otros servicios

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP 2.0 no presenta nuevas características para los siguientes servicios:

- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Analysis Services (SSAS)
- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (SSIS)
- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (SSRS)

## <a name="next-steps"></a>Pasos siguientes

- [Notas de la versión de SQL Server 2019](sql-server-ver15-release-notes.md)

- [Microsoft SQL Server 2019: Artículo técnico](https://info.microsoft.com/rs/157-GQE-382/images/EN-US-CNTNT-white-paper-DBMod-Microsoft-SQL-Server-2019-Technical-white-paper.pdf)<br />Publicado en septiembre de 2018. Se aplica a Microsoft SQL Server 2019 CTP 2.0 para Windows, Linux y contenedores de Docker.


[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
