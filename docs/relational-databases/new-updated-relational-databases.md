---
title: 'Actualizado: los documentos de bases de datos relacionales | Documentos de Microsoft'
description: "Mostrar fragmentos de contenido actualizado para recientemente modificadas en documentación, bases de datos relacionales."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: BYHAM
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: relational-databases
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 06/30/2017
ms.author: genemi
ms.translationtype: Human Translation
ms.sourcegitcommit: dcf26be9dc2e502b2d01f5d05bcb005fd7938017
ms.openlocfilehash: 19b664245f45ad45a4c7d1eba249858030fad718
ms.contentlocale: es-es
ms.lasthandoff: 07/03/2017

---
<a id="new-and-recently-updated-relational-databases-docs" class="xliff"></a>

# Las nuevas y recientemente actualizado: los documentos de bases de datos relacionales



Casi todos los días, Microsoft actualiza algunos de los artículos existentes en su [Docs.Microsoft.com](http://docs.microsoft.com/) sitio Web de documentación. Este artículo muestra extractos de los artículos actualizados recientemente. También pueden aparecer vínculos a artículos nuevos.

En este artículo es generado por un programa que se vuelve a ejecutar periódicamente. En ocasiones, un extracto puede aparecer con formato imperfecto, o como marcado del artículo de origen. Nunca las imágenes se muestran aquí.

Actualizaciones recientes se notifican para el siguiente intervalo de fechas y el asunto:



- *Intervalo de fechas de las actualizaciones:* &nbsp; **17-05-2017** &nbsp; a &nbsp; **30-06-2017**
- *Área de asunto:* &nbsp; **bases de datos relacionales**.




&nbsp;

<a id="new-articles-created-recently" class="xliff"></a>

## Nuevos artículos creados recientemente

Los siguientes vínculos llevan a nuevos artículos que se han agregado recientemente.


1. [Parámetros internos de OLTP en memoria de SQL Server para SQL Server 2016](in-memory-oltp/sql-server-in-memory-oltp-internals-for-sql-server-2016.md)
2. [Procesamiento de consultas adaptable en bases de datos SQL](performance/adaptive-query-processing.md)
3. [Guide to enhancing privacy and addressing GDPR requirements with the Microsoft SQL platform (Guía para la mejora de la privacidad y direccionamiento de requisitos GDPR con la plataforma de Microsoft SQL)](security/microsoft-sql-and-the-gdpr-requirements.md)
4. [sys.dm_db_log_stats (Transact-SQL)](system-dynamic-management-views/sys-dm-db-log-stats-transact-sql.md)
5. [sys.dm_exec_query_parallel_workers (Transact-SQL)](system-dynamic-management-views/sys-dm-exec-query-parallel-workers-transact-sql.md)



&nbsp;

<a id="updated-articles-with-excerpts" class="xliff"></a>

## Artículos actualizados con extractos

Esta sección muestra los extractos de las actualizaciones que se recopilan de los artículos que han presentado recientemente una actualización a gran escala.

Los extractos que se muestran aquí aparecen separados de su contexto semántica correcta. Además, en ocasiones, un extracto se separa de la sintaxis de markdown importante que rodea en el artículo real. Por lo tanto, estos extractos son para obtener instrucciones generales solo. Los extractos de sólo le permiten saber si sus intereses garantizan dedicar tiempo a haga clic en y visite el artículo real.

Por estas y otras razones, no se copie el código de estos fragmentos y no toma como verdaderos exacta cualquier fragmento de texto. En su lugar, visite el artículo real.



&nbsp;

&nbsp;

<a name="TitleNum_1"/>

<a id="1-nbsp-altering-memory-optimized-tablesin-memory-oltpaltering-memory-optimized-tablesmd" class="xliff"></a>

### 1. &nbsp; [Modificar tablas con optimización para memoria](in-memory-oltp/altering-memory-optimized-tables.md)

*Actualizado: 23-06-2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Siguiente](#TitleNum_2))

<!-- Source markdown line 82.  ms.author= "genemi".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 8359700b5db24838f1bb273526794c2865bbbe11 41d77cf0bbcf53a1b64d6524a24e5736c5a073da  (PR=2171  ,  Filename=altering-memory-optimized-tables.md  ,  Dirpath=docs\relational-databases\in-memory-oltp\  ,  MergeCommitSha40=7d2dbe0bdc4cbd05f11eacf938b35a9c35ace2e7) -->



**Registro de ALTER TABLE en tablas con optimización para memoria**

En una tabla con optimización para memoria, la mayoría de los escenarios ALTER TABLE ahora se ejecutan en paralelo y generan una optimización de las escrituras en el registro de transacciones. La optimización se consigue únicamente al registrar los cambios de metadatos en el registro de transacciones. Sin embargo, las siguientes operaciones de ALTER TABLE se ejecutan en un solo subproceso y no tienen optimización para registro.

En este caso, la operación de un solo subproceso registraría todo el contenido de la tabla modificada en el registro de transacciones. La siguiente es una lista de las operaciones de un solo subproceso:

- Modificar o agregar una columna para usar un objeto de gran tamaño (LOB): nvarchar(max), varchar(max) o varbinary(max).

- Agregar o quitar un índice COLUMNSTORE.

- Casi todo lo que afecta a una [columna no consecutiva--../../relational-databases/in-memory-oltp/supported-data-types-for-in-memory-oltp.md).

    - Hacer que una columna consecutiva pase a ser no consecutiva.

    - Hacer que una columna no consecutiva pase a ser consecutiva.

    - Crear una columna no consecutiva nueva.

    - *Excepción:* el alargamiento de una columna que ya no es consecutiva se registra de la forma optimizada. 
  




&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

<a id="2-nbsp-table-and-row-size-in-memory-optimized-tablesin-memory-oltptable-and-row-size-in-memory-optimized-tablesmd" class="xliff"></a>

### 2. &nbsp; [Tamaño de tabla y fila de las tablas con optimización para memoria](in-memory-oltp/table-and-row-size-in-memory-optimized-tables.md)

*Actualizado: 22-06-2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Anterior](#TitleNum_1) | [Siguiente](#TitleNum_3))

<!-- Source markdown line 114.  ms.author= "genemi".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 27ce0fa2e7bb464f9c3d6e32dd195de3b79abfcd 0a3cacd86024e2b734704ffd37e55ca0b17a0c94  (PR=2163  ,  Filename=table-and-row-size-in-memory-optimized-tables.md  ,  Dirpath=docs\relational-databases\in-memory-oltp\  ,  MergeCommitSha40=fe6de2b16b9792a5399b1c014af72a2a5ee52377) -->



 
  
 El recálculo de [tamaño del cuerpo de la fila] se describe en la siguiente tabla.  
  
 Hay dos cálculos diferentes para el tamaño del cuerpo de la fila: el tamaño calculado y el tamaño real:  
  
-   El tamaño calculado, indicado mediante el [tamaño del cuerpo calculado de la fila], se utiliza para determinar si la limitación de tamaño de fila de 8.060 bytes se supera.  
  
-   El tamaño real se indica con [tamaño del texto real de la fila], es el tamaño de almacenamiento real del cuerpo de la fila en memoria y en los archivos de puntos de comprobación.  
  
 Ambos [tamaño del cuerpo calculado de la fila] y [tamaño del texto real de la fila] se calculan de igual forma. La única diferencia es el cálculo de tamaño de las columnas (n)varchar(i) y varbinary(i), como se refleja en la parte inferior de la tabla siguiente. El tamaño del cuerpo calculado de la fila utiliza el tamaño *i* declarado como tamaño de columna, mientras que el tamaño del cuerpo real de la fila utiliza el tamaño real de los datos.  
  
 En la tabla siguiente se describe el cálculo del tamaño del cuerpo de fila, indicado como [tamaño real del cuerpo de fila] = SUM([tamaño de tipos superficiales]) + 2 + 2 * [número de columnas de tipo profundo].  
  
|Sección|Tamaño|Comentarios|  
|-------------|----------|--------------|  
|Columnas de tipo superficial|SUM([tamaño de tipos superficiales]) El tamaño en bytes de los tipos individuales es el siguiente:<br /><br /> **Bit**: 1<br /><br /> **Tinyint**: 1<br /><br /> **Smallint**: 2<br /><br /> **Int**: 4<br /><br /> **Real**: 4<br /><br /> **Smalldatetime**: 4<br /><br /> **Smallmoney**: 4<br /><br /> **Bigint**: 8<br /><br /> **Datetime**: 8<br /><br /> **Datetime2**: 8<br /><br /> **Float**: 8<br /><br /> **Money**: 8<br /><br /> **Numeric** (precisión <=18): 8<br /><br /> **Time**: 8<br /><br /> **Numeric** (precisión >18): 16<br /><br /> **Uniqueidentifier**: 16||  
|Relleno superficial de la columna|Los valores posibles son:<br /><br /> 1, si hay columnas de tipo profundo y el tamaño total de datos de las columnas superficiales es un número impar.<br /><br /> De lo contrario, es 0|Los tipos profundos son (var)binary y (n)(var)char.|  




&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

<a id="3-nbsp-post-migration-validation-and-optimization-guidepost-migration-validation-and-optimization-guidemd" class="xliff"></a>

### 3. &nbsp; [Guía de optimización y validación posterior a la migración](post-migration-validation-and-optimization-guide.md)

*Actualizado: 21-06-2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Anterior](#TitleNum_2) | [Siguiente](#TitleNum_4))

<!-- Source markdown line 27.  ms.author= "harinid".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 faa2e3dd8be3aeb475bf8c7f71617ebf17969892 f2760dfecda10baeb121929b72a4d8164e81185b  (PR=2126  ,  Filename=post-migration-validation-and-optimization-guide.md  ,  Dirpath=docs\relational-databases\  ,  MergeCommitSha40=dcbeda6b8372b358b6497f78d6139cad91c8097c) -->



A continuación se muestran algunos de los escenarios comunes de rendimiento detectados después de migrar a la plataforma [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)] y cómo resolverlos. Se incluyen escenarios específicos de la migración de [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)] a [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)] (versiones más antiguas a más recientes), así como de plataformas ajenas (como Oracle, DB2, MySQL y Sybase) a [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)].

**<a name="CEUpgrade"></a> Consultar las regresiones debidas a un cambio en la versión CE**


**Se aplica a:** migración de [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)] a [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)].

Al migrar desde una versión anterior de [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)] a [!INCLUDE[ssSQL14--../includes/sssql14-md.md)] o más reciente, y al actualizar el [nivel de compatibilidad de la base de datos--../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md) al más reciente, una carga de trabajo puede verse expuesta al riesgo de regresión de rendimiento.

Esto es debido a que, a partir de [!INCLUDE[ssSQL14--../includes/sssql14-md.md)], todos los cambios del optimizador de consultas están vinculados al [nivel de compatibilidad--../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md) más reciente, por lo que los planes no se cambian en el momento de la actualización, sino cuando un usuario cambia la opción de base de datos `COMPATIBILITY_LEVEL` a la versión más reciente. Esta función, junto con el Almacén de consultas, confiere al usuario un enorme control sobre el rendimiento de las consultas en el proceso de actualización. 

Para obtener más información sobre los cambios del optimizador de consultas introducidas en [!INCLUDE[ssSQL14](../includes/sssql14-md.md)], consulte [Optimizing Your Query Plans with the SQL Server 2014 Cardinality Estimator (Optimizar los planes de consulta con el programa de estimación de cardinalidad de SQL Server 2014)](http://msdn.microsoft.com/library/dn673537.aspx).




&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

<a id="4-nbsp-sysquerystoreplan-transact-sqlsystem-catalog-viewssys-query-store-plan-transact-sqlmd" class="xliff"></a>

### 4. &nbsp; [sys.query_store_plan (Transact-SQL)](system-catalog-views/sys-query-store-plan-transact-sql.md)

*Actualizado: 05-06-2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Anterior](#TitleNum_3) | [Siguiente](#TitleNum_5))

<!-- Source markdown line 58.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 1b77e34309ba7033578b3c82ed83c8c2fbc93e24 ce4ade9ab906c35cb87068a1fb91c4e1d7549aac  (PR=1940  ,  Filename=sys-query-store-plan-transact-sql.md  ,  Dirpath=docs\relational-databases\system-catalog-views\  ,  MergeCommitSha40=1d363db8e8bd0e1460cdea3c3a7add68e48714c9) -->



**Limitaciones de forzar un plan**

El Almacén de consultas dispone de un mecanismo para obligar al optimizador de consultas a usar un determinado plan de ejecución. Pero existen algunas limitaciones que pueden evitar la aplicación de un plan. 

En primer lugar, si el plan contiene las siguientes construcciones:
* Instrucción insert bulk.
* Instrucción insert bulk.
* Referencia a una tabla externa
* Consulta distribuida u operaciones de texto completo
* Uso de consultas globales 
* Cursores
* Especificación de combinación en estrella no válida 

En segundo lugar, si los objetos en los que se basa el plan ya no están disponibles:
* Base de datos (si la base de datos donde se originó el plan ya no existe)
* Índice (ya no existe o está deshabilitado)

Por último, problemas con el propio plan:
* No válido para la consulta
* El optimizador de consultas ha superado el número de operaciones permitidas
* XML de plan formado incorrectamente




&nbsp;

&nbsp;

---

<a name="TitleNum_5"/>

<a id="5-nbsp-manage-retention-of-historical-data-in-system-versioned-temporal-tablestablesmanage-retention-of-historical-data-in-system-versioned-temporal-tablesmd" class="xliff"></a>

### 5. &nbsp;[Administrar la retención de datos históricos en las tablas temporales con versión del sistema](tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)

*Updated: 2017-05-19* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Previous](#TitleNum_4))

<!-- Source markdown line 425.  ms.author= "carlrab".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 ee69beb6a46913934d4a322f5d95343cc86f2ec4 94da98fec4ab16636a4581c16eb4456e2d1ff66b  (PR=1777  ,  Filename=manage-retention-of-historical-data-in-system-versioned-temporal-tables.md  ,  Dirpath=docs\relational-databases\tables\  ,  MergeCommitSha40=5bd0e1d3955d898824d285d28979089e2de6f322) -->



**Usando el enfoque de directiva de retención de historial Temporal**

> **Nota:** mediante la directiva de retención de historial Temporal método se aplica a [! INCLUDE [sqldbesa--.. /.. /includes/sqldbesa-MD.MD]) y SQL Server 2017 desde CTP 1.3.  

Tiempo de retención de historial temporal puede ser configurado en el nivel de tabla individual, lo que permite a los usuarios crear antigüedad flexible directivas. Aplicar la retención temporal es simple: requiere un solo parámetro establecerse durante el cambio de esquema o de creación de tabla.

Después de definir la directiva de retención, la base de datos de SQL Azure inicia comprobar periódicamente si hay filas históricos que son aptas para la limpieza automática de los datos. Identificación de las filas coincidentes y su eliminación de la tabla de historial se producen de forma transparente, en la tarea en segundo plano programada y ejecutada por el sistema. Se comprueba la condición de edad para las filas de la tabla de historial en función de la columna que representa el final del período de SYSTEM_TIME. Si el período de retención, por ejemplo, se establece en seis meses, filas aptas para la limpieza de la tabla cumplen la condición siguiente:
```
ValidTo < DATEADD (MONTH, -6, SYSUTCDATETIME())
```
En el ejemplo anterior, se supone que ValidTo columna corresponde al final del período de SYSTEM_TIME.
**¿Cómo configurar la directiva de retención?**

Antes de configurar la directiva de retención para una tabla temporal, compruebe primero si la retención de historial temporal está habilitada en el nivel de base de datos:
```
SELECT is_temporal_history_retention_enabled, name
FROM sys.databases
```
Marca la base de datos **is_temporal_history_retention_enabled** se establece en ON de forma predeterminada, pero los usuarios pueden cambiar con la instrucción ALTER DATABASE. Automáticamente se establece en OFF después de punto en la operación de restauración de tiempo. Para habilitar la limpieza de la retención de historial temporal para la base de datos, ejecute la instrucción siguiente:





&nbsp;

<a name="compactupdatedlist"/>

<a id="compact-list-of-articles-updated-recently" class="xliff"></a>

## Compact lista de artículos que se actualizó recientemente

Esta lista compact proporciona vínculos a todos los artículos actualizados que se enumeran en la sección anterior.

1. [Modificar tablas con optimización para memoria](#TitleNum_1)
2. [Tamaño de tabla y fila de las tablas con optimización para memoria](#TitleNum_2)
3. [Guía de optimización y validación posterior a la migración](#TitleNum_3)
4. [sys.query_store_plan (Transact-SQL)](#TitleNum_4)
5. [Administración de la retención de datos históricos en las tablas temporales con control de versiones del sistema](#TitleNum_5)




<a name="sisters2"/>

&nbsp;

<a id="sister-articles" class="xliff"></a>

## Hermana artículos

En esta sección se enumeran artículos muy similares a los artículos actualizados recientemente en otras áreas temáticas, dentro del mismo repositorio de GitHub.com: [MicrosoftDocs/**sql-docs-pr**](https://github.com/microsoftdocs/sql-docs-pr/).

<!--  20170630-1150  -->

<a id="subject-areas-which-do-have-new-or-recently-updated-articles" class="xliff"></a>

#### Áreas temáticas con artículos nuevos o actualizados recientemente

- [Nuevos + Actualizados (12+2): documentos de **Análisis avanzado para SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuevos + Actualizados (1+0): documentos de **Analysis Services para SQL**](../analysis-services/new-updated-analysis-services.md)
- [Nuevos + Actualizados (0+2): documentos de **Conectar con SQL**](../connect/new-updated-connect.md)
- [Nuevos + Actualizados (3+0): documentos de **Motor de base de datos para SQL**](../database-engine/new-updated-database-engine.md)
- [Nuevos + Actualizados (1+2): documentos de **Integration Services para SQL**](../integration-services/new-updated-integration-services.md)
- [Nuevos + Actualizados (2+8): documentos de **Linux para SQL**](../linux/new-updated-linux.md)
- [Nuevos + Actualizados (1+0): documentos de **Master Data Services (MDS) para SQL**](../master-data-services/new-updated-master-data-services.md)
- [Nuevos + Actualizados (5+5): documentos de **Bases de datos relacionales para SQL**](../relational-databases/new-updated-relational-databases.md)
- [Nuevos + Actualizados (2+0): documentos de **Reporting Services para SQL**](../reporting-services/new-updated-reporting-services.md)
- [Nuevos + Actualizados (0+4): documentos de **Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Nuevos + Actualizados (0+1): documentos de **SQL Server Data Tools (SSDT)**](../ssdt/new-updated-ssdt.md)
- [Nuevos + Actualizados (0+1): documentos de **SQL Server Management Studio (SSMS)**](../ssms/new-updated-ssms.md)
- [Nuevos + Actualizados (1+0): documentos de **Herramientas para SQL**](../tools/new-updated-tools.md)


<a id="subject-areas-which-have-no-new-or-recently-updated-articles" class="xliff"></a>

#### Áreas temáticas sin artículos nuevos ni actualizados recientemente

- [Nuevos + Actualizados (0+0): documentos de **Objetos de datos ActiveX (ADO) para SQL**](../ado/new-updated-ado.md)
- [Nuevos + Actualizados (0+0): documentos de **Data Quality Services para SQL**](../data-quality-services/new-updated-data-quality-services.md)
- [Nuevos + Actualizados (0+0): documentos de **Extensiones de minería de datos (DMX) para SQL**](../dmx/new-updated-dmx.md)
- [Nuevos + Actualizados (0+0): documentos de **Expresiones multidimensionales (MDX) para SQL**](../mdx/new-updated-mdx.md)
- [Nuevos + Actualizados (0+0): documentos de **ODBC (conectividad abierta de bases de datos) para SQL**](../odbc/new-updated-odbc.md)
- [Nuevos + Actualizados (0+0): documentos de **PowerShell para SQL**](../powershell/new-updated-powershell.md)
- [Nuevos + Actualizados (0+0): documentos de **Ejemplos para SQL**](../sample/new-updated-sample.md)
- [Nuevos + Actualizados (0+0): documentos de **SQL Server Migration Assistant (SSMA)**](../ssma/new-updated-ssma.md)
- [Nuevos + Actualizados (0+0): documentos de **Transact-SQL**](../t-sql/new-updated-t-sql.md)
- [Nuevos + Actualizados (0+0): documentos de **XQuery para SQL**](../xquery/new-updated-xquery.md)


&nbsp;


