---
title: Novedades de SQL Server 2017 | Microsoft Docs
ms.custom: 
ms.date: 07/12/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- server-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b57f375-9242-4bb2-9d4b-c560d5a93524
caps.latest.revision: 71
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 71203bfa7cb4dcd06cc14ad8e49e5bc1113f8605
ms.openlocfilehash: 731d53110d9dc47de5a44dd7f65190e029e120dc
ms.contentlocale: es-es
ms.lasthandoff: 07/19/2017

---
# <a name="whats-new-in-sql-server-2017"></a>Novedades de SQL Server 2017
SQL Server 2017 representa un paso importante hacia convertir SQL Server en una plataforma que proporciona opciones de lenguajes de desarrollo, tipos de datos, ya sean locales o en la nube, y sistemas operativos con la eficacia de SQL Server en Linux, contenedores de Docker basados en Linux y Windows. En este tema se resumen las novedades de las áreas de características específicas de las versiones más recientes de SQL Server 2017 Release Candidate (RC1, julio de 2017) y Community Technical Preview (CTP).

**Pruébelo:** [descargue SQL Server 2017 Release Candidate (RC)](http://go.microsoft.com/fwlink/?LinkID=829477)

>[!TIP]
>**Descargue SQL Server en Linux.** Para más información, consulte [Documentación de SQL Server en Linux](https://docs.microsoft.com/sql/linux/) y [Novedades de SQL Server 2017 en Linux](https://docs.microsoft.com/sql/linux/sql-server-linux-whats-new).

## <a name="latest-release-sql-server-2017-release-candidate-rc1-july-2017"></a>Última versión: SQL Server 2017 Release Candidate (RC1, julio de 2017)

### <a name="sql-server-database-engine"></a>Motor de base de datos de SQL Server    
- Los ensamblados CLR ahora se pueden agregar a una lista blanca, como solución alternativa para la característica `clr strict security` que se describe en CTP 2.0. [sp_add_trusted_assembly](../relational-databases/system-stored-procedures/sys-sp-add-trusted-assembly-transact-sql.md), [sp_drop_trusted_assembly](../relational-databases/system-stored-procedures/sys-sp-drop-trusted-assembly-transact-sql.md) y [sys.trusted_asssemblies](../relational-databases/system-catalog-views/sys-trusted-assemblies-transact-sql.md) se agregan para admitir la lista blanca de ensamblados de confianza.  

### <a name="sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS)
- La nueva característica **Escalabilidad horizontal** de SSIS tiene las siguientes características nuevas y modificadas en RC1. Para más información, consulte [Novedades de Integration Services en SQL Server 2017](~/integration-services/what-s-new-in-integration-services-in-sql-server-2017.md).
    -   Patrón de escalabilidad horizontal ahora admite alta disponibilidad.
    -   Se mejoró el control de conmutación por error de los registros de ejecución de Trabajadores de escalabilidad horizontal.
    -   Se cambió el nombre del parámetro *runincluster* del procedimiento almacenado **[catálogo].[create_execution]** a *runinscaleout* para mejorar la coherencia y la legibilidad.
    -   El catálogo de SSIS tiene una nueva propiedad global para especificar el modo predeterminado de ejecución de los paquetes de SSIS.

## <a name="sql-server-database-engine"></a>Motor de base de datos de SQL Server  
SQL Server 2017 incluye muchas mejoras de rendimiento, perfeccionamiento y características de Motor de base de datos. 
- La **recompilación de índices en línea reanudable** reanuda una operación de recompilación de índices en línea desde donde se detuvo después de un error (como una conmutación por error en una réplica o espacio en disco insuficiente), o bien pausa y reanuda más adelante una operación de recompilación de índices en línea. Vea [ALTER INDEX](../t-sql/statements/alter-index-transact-sql.md) y [directrices para operaciones de índice en línea](../relational-databases/indexes/guidelines-for-online-index-operations.md). (CTP 2.0)
- La opción **IDENTITY_CACHE** de ALTER DATABASE SCOPED CONFIGURATION permite evitar lagunas en los valores de columnas e identidad si un servidor se reinicia inesperadamente o realiza conmutación por error en un servidor secundario. Vea [configuración de ALTER DATABASE en el ámbito](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md). (CTP 2.0)
- El **ajuste automático de bases de datos** proporciona información de los posibles problemas de rendimiento de las consultas, recomienda soluciones y puede corregir automáticamente los problemas identificados. Consulte [Ajuste automático](../relational-databases/automatic-tuning/automatic-tuning.md). (CTP 2.0)
- Las nuevas **funcionalidades de base de datos de gráficos** para modelar relaciones varios a varios incluyen una nueva sintaxis de [CREATE TABLE](../t-sql/statements/create-table-sql-graph.md) para crear tablas de nodos y perimetrales, y la palabra clave [MATCH](../t-sql/queries/match-sql-graph.md) para consultas. Consulte [Procesamiento de gráficos con SQL Server 2017](../relational-databases/graphs/sql-graph-overview.md). (CTP 2.0)
- Una opción de sp_configure llamada `clr strict security` se habilita de manera predeterminada para mejorar la seguridad de los ensamblados CLR. Consulte [Seguridad estricta de CLR](../database-engine/configure-windows/clr-strict-security.md). (CTP 2.0)
- El programa de instalación ahora permite especificar el tamaño de archivo tempdb inicial hasta **256 GB** (262 144 MB) por archivo, con una advertencia si el tamaño del archivo es mayor que 1 GB y si IFI no está habilitado. (CTP 2.0)
- La columna **modified_extent_page_count** en [sys.dm_db_file_space_usage](../relational-databases/system-dynamic-management-views/sys-dm-db-file-space-usage-transact-sql.md) hace seguimiento de los cambios diferenciales en cada archivo de base de datos, lo que habilita soluciones de copia de seguridad inteligentes que realizan copia de seguridad diferencial o copia de seguridad completa según el porcentaje de páginas modificadas en la base de datos. (CTP 2.0)
- La sintaxis [SELECT INTO](../t-sql/queries/select-into-clause-transact-sql.md) T-SQL ahora admite la carga de una tabla en un grupo de archivos distinto del grupo de archivos predeterminado d el usuario mediante la palabra clave **ON**. (CTP 2.0)
- Ahora se admiten las transacciones entre bases de datos entre todas las bases de datos que forman parte de un **grupo de disponibilidad AlwaysOn**, incluidas las bases de datos que son parte de la misma instancia. Consulte [Transactions - Always On Availability Groups and Database Mirroring](../database-engine/availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md) (Transacciones: grupos de disponibilidad AlwaysOn y creación de reflejo de la base de datos) (CTP 2.0)
- La nueva funcionalidad de **grupos de funcionalidad** incluye compatibilidad sin clúster, configuración de grupos de compatibilidad de confirmación de réplica mínima y migraciones y pruebas entre distintos sistemas operativos Windows y Linux. (CTP 1.3)
- Nuevas vistas de administración dinámica:
    - [sys.dm_db_log_stats](../relational-databases/system-dynamic-management-views/sys-dm-db-log-stats-transact-sql.md) expone atributos a nivel de resumen e información sobre los archivos de registro de transacciones, lo que resulta útil para supervisar el estado de los registros de transacciones. (CTP 2.1)
    - [sys.dm_tran_version_store_space_usage](../relational-databases/system-dynamic-management-views/sys-dm-tran-version-store-space-usage.md) hace seguimiento del uso del almacén de versiones por base de datos, lo que resulta útil para planear de manera proactiva el dimensionamiento de tempdb según el uso del almacén de versiones por base de datos. (CTP 2.0)
    - [sys.dm_db_log_info](../relational-databases/system-dynamic-management-views/sys-dm-db-log-info-transact-sql.md) expone información de VLF para supervisar, alertar y evitar posibles problemas con los registros de transacciones. (CTP 2.0)
    - [sys.dm_db_stats_histogram](../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md) es una nueva vista de administración dinámica para examinar estadísticas. (CTP 1.3)
    - **sys.dm_os_host_info** proporciona información de sistema operativo para Windows y Linux. (CTP 1.0)
- El **Asesor de optimización de base de datos (DTA)** tiene opciones adicionales y mejor rendimiento. (CTP 1.2)
- Las **mejoras en memoria** incluyen compatibilidad con columnas calculadas en tablas optimizadas para memoria, compatibilidad total con funciones JSON en módulos de compilación nativa y el operador CROSS APPLY en módulos de compilación nativa. (CTP 1.1)
- Las nuevas **funciones de cadena** son CONCAT_WS, TRANSLATE y TRIM, y WITHIN GROUP ahora es compatible con la función STRING_AGG. (CTP 1.1)
- Hay nuevas **opciones de acceso masivo** (BULK INSERT y OPENROWSET(BULK...) ) para archivos CSV y de Azure Blob. (CTP 1.1)
- Las **mejoras de objetos con optimización para memoria** incluyen sp_spaceused y la eliminación de la limitación de ocho índices en las tablas optimizadas para memoria, sp_rename para tablas optimizadas para memoria y módulos T-SQL de compilación nativa y CASE y TOP (N) WITH TIES para módulos T-SQL de compilación nativa. Los archivos de grupos de archivos con optimización para memoria ahora se pueden almacenar, se puede crear una copia de seguridad de ellos y se pueden restaurar en Azure Storage. (CTP 1.0)
- **DATABASE SCOPED CREDENTIAL** es una nueva clase de protegible, que admite los permisos CONTROL, ALTER, REFERENCES, TAKE OWNERSHIP y VIEW DEFINITION. ADMINISTER DATABASE BULK OPERATIONS ahora es visible en sys.fn_builtin_permissions. (CTP 1.0)
- Se agregó **COMPATIBILITY_LEVEL 140** de base de datos. (CTP 1.0)  

Para más información, consulte [Novedades de Motor de base de datos de SQL Server 2017](~/database-engine/configure-windows/what-s-new-in-sql-server-2017-database-engine.md).

## <a name="sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS)
- La nueva característica **Escalabilidad horizontal** de SSIS tiene las siguientes características nuevas y modificadas. Para más información, consulte [Novedades de Integration Services en SQL Server 2017](~/integration-services/what-s-new-in-integration-services-in-sql-server-2017.md). (RC1)
    -   Patrón de escalabilidad horizontal ahora admite alta disponibilidad.
    -   Se mejoró el control de conmutación por error de los registros de ejecución de Trabajadores de escalabilidad horizontal.
    -   Se cambió el nombre del parámetro *runincluster* del procedimiento almacenado **[catálogo].[create_execution]** a *runinscaleout* para mejorar la coherencia y la legibilidad.
    -   El catálogo de SSIS tiene una nueva propiedad global para especificar el modo predeterminado de ejecución de los paquetes de SSIS.
- En la nueva característica **Escalabilidad horizontal de SSIS**, ahora puede usar el parámetro **Use32BitRuntime** cuando desencadena la ejecución. (CTP 2.1)
- SQL Server 2017 Integration Services (SSIS) ahora admite **SQL Server en Linux** y un paquete nuevo le permite ejecutar paquetes de SSIS en Linux desde la línea de comandos. Para más información, consulte la [entrada de blog que anuncia la compatibilidad de SSIS con Linux](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/). (CTP 2.1)
- La nueva característica **Escalabilidad horizontal de SSIS** facilita en gran medida la ejecución de SSIS en varias máquinas. Consulte [Escalabilidad horizontal de Integration Services](~/integration-services/integration-services-ssis-scale-out.md). (CTP 1.0)
- Origen OData y Administrador de conexiones OData ahora admiten la conexión a fuentes de OData de Microsoft Dynamics AX Online y Microsoft Dynamics CRM Online. (CTP 1.0)

Para más información, consulte [Novedades de Integration Services en SQL Server 2017](~/integration-services/what-s-new-in-integration-services-in-sql-server-2017.md).

## <a name="sql-server-analysis-services-ssas"></a>SQL Server Analysis Services (SSAS) 
SQL Server Analysis Services 2017 presenta muchas mejoras para los modelos tabulares. Estos incluyen:
- Modo tabular como opción de instalación predeterminada para Analysis Services. (CTP 2.0)
- Seguridad de nivel de objeto para proteger los metadatos de los modelos tabulares. (CTP 2.0)
- Relaciones de fecha para crear fácilmente relaciones basadas en los campos de fecha. (CTP 2.0)
- Compatibilidad de los nuevos orígenes de datos **Get Data** (Power Query) y los orígenes de datos DirectQuery existentes con consultas M. (CTP 2.0) 
- Editor DAX para SSDT. (CTP 2.0)
- Sugerencias de codificación, una característica avanzada para optimizar la actualización de datos de modelos tabulares en memoria de gran tamaño. (CTP 1.3)
- Compatibilidad con el **nivel de compatibilidad 1400** para modelos tabulares. Para crear proyectos de modelos tabulares con el nivel de compatibilidad 1400 o actualizar proyectos existentes a dicho nivel, descargue e instale [SQL Server Data Tools (SSDT) 17.0 RC2](https://go.microsoft.com/fwlink?LinkId=837939). (CTP 1.1)
- Una experiencia **Get Data** moderna para los modelos tabulares en el nivel de compatibilidad 1400. Consulte el [blog del equipo de Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/2016/12/16/introducing-a-modern-get-data-experience-for-sql-server-2017-on-windows-ctp-1-1-for-analysis-services/). (CTP 1.1)
- Propiedad **Ocultar miembros** para ocultar los miembros en blanco de jerarquías desiguales. (CTP 1.1)
- Nueva acción **Filas de detalles** del usuario final para **mostrar detalles** de la información agregada. Funciones [SELECTCOLUMNS](https://msdn.microsoft.com/library/mt761759.aspx) y **DETAILROWS** para crear expresiones de Filas de detalles. (CTP 1.1)
- Operador DAX **IN** para especificar varios valores. (CTP 1.1)

Para más información, consulte [Novedades de SQL Server Analysis Services 2017](~/analysis-services/what-s-new-in-sql-server-analysis-services-2017.md).

## <a name="sql-server-reporting-services-ssrs"></a>SQL Server Reporting Services (SSRS)
A partir de CTP 2.1, SSRS ya no está disponible para instalarse mediante el programa de instalación de SQL Server. Vaya al Centro de descarga de Microsoft para [descargar la versión preliminar de mayo de 2017 de Servidor de informes de Power BI y Power BI Desktop optimizado para Servidor de informes de Power BI](https://www.microsoft.com/download/details.aspx?id=55253). Para obtener información sobre el servidor de informes de Power BI, consulte [empezar a trabajar con el servidor de informes de Power BI](https://powerbi.microsoft.com/documentation/reportserver-get-started/).
- Ahora hay comentarios disponibles para los informes a fin de agregar perspectivas y colaborar con otros usuarios. También puede incluir archivos adjuntos con los comentarios. (CTP 2.1)
- En las versiones más recientes del Generador de informes y SQL Server Data Tools, puede crear consultas DAX nativas sobre los modelos de datos tabulares de SQL Server Analysis Services si arrastra y coloca los campos deseados en los diseñadores de consultas. Consulte el [blog de Reporting Services](https://blogs.msdn.microsoft.com/sqlrsteamblog/2017/03/09/query-designer-support-for-dax-now-available-in-report-builder-and-sql-server-data-tools/).

Para más información, consulte [Novedades de SQL Server Reporting Services (SSRS)](~/reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md).

## <a name="sql-server-machine-learning-services"></a>Servicios de aprendizaje de máquina SQL Server
SQL Server R Services ahora se llama **SQL Server Machine Learning Services** para reflejar la nueva compatibilidad con Python además de los lenguajes R. Puede usar Machine Learning Services (en base de datos) para ejecutar scripts de R o Python en SQL Server, o bien instalar Microsoft Machine Learning Server (independiente) para implementar y usar modelos de R y Python que no requieren SQL Server. Ambas plataformas incluyen nuevos algoritmos de MicrosoftML de aprendizaje automático de distribuida y la versión más reciente de Microsoft R (versión 9.1.0). (CTP 2.0)
- El aprendizaje automático con Python incluye el módulo **revoscalepy**, que admite un subconjunto de los algoritmos distribuidos y los contextos de cálculo proporcionados en RevoScaleR. 
- Puede crear fácilmente varios modelos en paralelo desde R con la nueva función **rxExecBy**. Los contextos de cálculo admitidos incluyen RxSpark y RxInSQLServer. (CTP 2.0)

Para más información, consulte [Novedades de SQL Server Machine Learning Services](~/advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md).

## <a name="next-steps"></a>Pasos siguientes
- Consulte las [notas de la versión de SQL Server 2017](sql-server-2017-release-notes.md).
- Averigüe las [novedades de SQL Server 2016](what-s-new-in-sql-server-2016.md).

