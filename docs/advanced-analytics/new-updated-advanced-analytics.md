---
title: 'Actualizado: Advanced Analytics para documentos de SQL Server | Documentos de Microsoft'
description: Mostrar fragmentos de contenido actualizado para recientemente modificadas en documentación, Advanced Analytics para Microsoft SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 058278df1ee54a6440f8225ea15f727857df76f2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="new-and-recently-updated-advanced-analytics-for-sql-server"></a>Nuevos y actualizados recientemente: análisis avanzados para SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Casi todos los días, Microsoft actualiza algunos de los artículos existentes en su [Docs.Microsoft.com](http://docs.microsoft.com/) sitio Web de documentación. Este artículo muestra extractos de los artículos actualizados recientemente. También pueden aparecer vínculos a artículos nuevos.

En este artículo es generado por un programa que se vuelve a ejecutar periódicamente. En ocasiones, un extracto puede aparecer con formato imperfecto, o como marcado del artículo de origen. Nunca las imágenes se muestran aquí.

Actualizaciones recientes se notifican para el siguiente intervalo de fechas y el asunto:



- *Intervalo de fechas de las actualizaciones:* &nbsp; del **03-12-2017** &nbsp; al &nbsp; **03-02-2018**
- *Área de asunto:* &nbsp; **Advanced Analytics para SQL Server**.

<!-- Repo = 'MicrosoftDocs/sql-docs'.   Branch = 'live'. -->



&nbsp;

## <a name="new-articles-created-recently"></a>Nuevos artículos creados recientemente

Los siguientes vínculos llevan a nuevos artículos que se han agregado recientemente.


1. [Instalación de paquetes de Python adicionales en SQL Server](python/install-additional-python-packages-on-sql-server.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Artículos actualizados con extractos

En esta sección se muestran extractos de actualizaciones recopiladas de artículos que han sufrido una actualización importante recientemente.

Los extractos que se muestran aquí aparecen separados de su contexto semántica correcta. Además, en ocasiones, un extracto se separa de la sintaxis de markdown importante que rodea en el artículo real. Por lo tanto, estos extractos son para obtener instrucciones generales solo. Los extractos de sólo le permiten saber si sus intereses garantizan dedicar tiempo a haga clic en y visite el artículo real.

Por estas y otras razones, no se copie el código de estos fragmentos y no toma como verdaderos exacta cualquier fragmento de texto. En su lugar, visite el artículo real.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Compact lista de artículos que se actualizó recientemente

En esta lista compacta se proporcionan vínculos a todos los artículos actualizados que aparecen en la sección de extractos.

1. [Problemas conocidos en servicios de aprendizaje de máquina](#TitleNum_1)
2. [Convertir código de R para ejecución en bases de datos](#TitleNum_2)
3. [Determinar qué paquetes de R están instalados en SQL Server](#TitleNum_3)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-known-issues-in-machine-learning-servicesknown-issues-for-sql-server-machine-learning-servicesmd"></a>1. &nbsp; [Problemas conocidos en servicios de aprendizaje de máquina](known-issues-for-sql-server-machine-learning-services.md)

*Actualizado: 2018-02-02* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([siguiente](#TitleNum_2))

<!-- Source markdown line 163.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 c6f46adcf795c43f818120b88407a3a89304cb27 c781562605f5cd77f6c43bfe5e89810cb72ceae0  (PR=4789  ,  Filename=known-issues-for-sql-server-machine-learning-services.md  ,  Dirpath=docs\advanced-analytics\  ,  MergeCommitSha40=386bfb688843bac7fa4d83dc1cfef94dd19db110) -->



Para otros problemas conocidos que podrían afectar a las soluciones de R, consulte el [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/resources-known-issues) sitio.

**Acceso denegado advertencia al ejecutar scripts de R en SQL Server en una ubicación no predeterminada**


Si la instancia de SQL Server se ha instalado en una ubicación no predeterminados, como fuera de la `Program Files` carpeta, la advertencia ACCESS_DENIED se produce al intentar ejecutar scripts que instalan un paquete. Por ejemplo:

> *En normalizePath(path.expand(path), winslash, mustWork): ruta de acceso [2] = "~ExternalLibraries/R/8/1": se denegó el acceso*

La razón es que una función de R intenta leer la ruta de acceso y se produce un error si el grupo de usuarios integrado **SQLRUserGroup**, no tiene acceso de lectura. La advertencia que se inicia no bloquea la ejecución del script de R actual, pero la advertencia puede repetirse varias veces siempre que el usuario ejecuta cualquier otro script de R.

Si ha instalado SQL Server en la ubicación predeterminada, este error no se produce, porque todos los usuarios de Windows tener permisos de lectura en el `Program Files` carpeta.

Este problema se corregirá en una versión de próximos servicios. Como alternativa, proporcione el grupo, **SQLRUserGroup**, con acceso de lectura para todas las carpetas primarias de `ExternalLibraries`.

**Error de serialización entre las versiones anteriores y nuevas de RevoScaleR**


Al pasar un modelo con un formato serializado a una instancia de SQL Server remota, podría aparecer el error:

> *Error en memDecompress (datos, tipo = descomprimir) error interno -3 en memDecompress(2).*

Este error se produce si ha guardado el modelo utilizando una versión reciente de la función de serialización, [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel), pero la instancia de SQL Server donde se deserializa el modelo tiene una versión antigua de las APIs de RevoScaleR, de SQL Servidor de 2017 CU2 o una versión anterior.



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-converting-r-code-for-execution-in-databaserconverting-r-code-for-use-in-sql-servermd"></a>2. &nbsp; [Convertir código de R para ejecución en bases de datos](r/converting-r-code-for-use-in-sql-server.md)

*Actualizado: 2018-01-08* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([anterior](#TitleNum_1) | [siguiente](#TitleNum_3))

<!-- Source markdown line 136.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 a1d156fac1af5813ef75965071686b177e2aede7 fc8beff0aa0d7ea298e493b90984875e81e9143e  (PR=4493  ,  Filename=converting-r-code-for-use-in-sql-server.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=f486d12078a45c87b0fcf52270b904ca7b0c7fc8) -->



**Empaquetar el código de R en un procedimiento almacenado**

+ Si el código es relativamente simple, puede incrustar en una función definida por el usuario de T-SQL sin modificaciones, como se describe en estos ejemplos:

    + [Crear una función de R que se ejecuta en rxExec](r/../tutorials/deepdive-create-a-simple-simulation.md)
    + [Ingeniería de característica con T-SQL y R](r/../tutorials/sqldev-create-data-features-using-t-sql.md)

+ Si el código es más complejo, use el paquete de R **sqlrutils** para convertir el código. Este paquete está diseñado para ayudar a los usuarios experimentados de R a escribir código de procedimiento almacenado buena.

    El primer paso es escribir el código de R como una sola función con claramente definidas entradas y salidas.

    A continuación, utilice la **sqlrutils** paquete para generar la entrada y las salidas en el formato correcto. El **sqlrutils** paquete genera el código de todo el procedimiento almacenado para usted y también se puede registrar el procedimiento almacenado en la base de datos.

    Para obtener más información y ejemplos, vea [SqlRUtils](r/../r/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md).

**Integrar con otros flujos de trabajo**

+ Aprovechar las herramientas de T-SQL y procesos ETL. Realizar ingeniería de característica, extracción de características y la limpieza de datos de antemano como parte de los flujos de trabajo de datos.

    Cuando está trabajando en un entorno de desarrollo de R dedicado como R Tools para Visual Studio o RStudio, puede extraer los datos en el equipo, analizar los datos de forma iterativa y, a continuación, escribir o mostrar los resultados.

    Sin embargo, cuando se migra código independiente para SQL Server, gran parte de este proceso puede simplificado o delegar a otras herramientas de SQL Server.

+ Use las estrategias de visualización segura, asincrónica.

    Los usuarios de SQL Server a menudo no pueden tener acceso a archivos en el servidor y herramientas de cliente SQL normalmente no admiten el dispositivo de gráficos de R. Si los gráficos u otros gráficos se generan como parte de la solución, considere la posibilidad de exportar los gráficos como datos binarios y guardar en una tabla o escribir.



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-determine-which-r-packages-are-installed-on-sql-serverrdetermine-which-packages-are-installed-on-sql-servermd"></a>3. &nbsp; [Determinar qué paquetes de R están instalados en SQL Server](r/determine-which-packages-are-installed-on-sql-server.md)

*Actualizado: 2018-01-24* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([anterior](#TitleNum_2))

<!-- Source markdown line 78.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 9a065066398843a4bed318fa46d4982d712915a9 7a1df11f57e7bbf0abc37d3aa240dedd2b88c45f  (PR=4715  ,  Filename=determine-which-packages-are-installed-on-sql-server.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=9e6a029456f4a8daddb396bc45d7874a43a47b45) -->




**Obtener la versión y la ubicación de biblioteca**


En el ejemplo siguiente se obtiene la ubicación de la biblioteca de RevoScaleR en el contexto de proceso local y la versión del paquete.

```
rxFindPackage(RevoScaleR, "local")
packageVersion("RevoScaleR")
```

**Determinar la ruta de acceso de biblioteca utilizado por SQL Server**


Si ha actualizado los componentes mediante el enlace de aprendizaje automático, puede cambiar la ruta de acceso a la biblioteca de R. Cuando esto sucede, anteriores accesos directos a herramientas de R podrían hacer referencia a una versión anterior. Para asegurarse de la versión de paquete y la ruta de acceso utilizada por SQL Server, puede ejecutar un comando como el siguiente:

```
EXEC sp_execute_external_script
    @language =N'R',
    @script=N'
    sql_r_path <- rxSqlLibPaths("local")
      print(sql_r_path)
    version_info <-packageVersion("RevoScaleR")
      print(version_info)'
```

**Resultado**

```
STDOUT message(s) from external script:
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER1000/R_SERVICES/library"
[1] '9.2.1'
```







## <a name="similar-articles-about-new-or-updated-articles"></a>Artículos similares sobre artículos nuevos o actualizados

En esta sección se enumeran artículos muy similares a los artículos actualizados recientemente en otras áreas temáticas, dentro de nuestro repositorio público de GitHub.com: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).


#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Áreas temáticas *con* artículos nuevos o actualizados recientemente


- [Nuevos + actualizados (1+3): &nbsp;documentos de **Análisis avanzado para SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuevos + actualizados (0+1): &nbsp;documentos de **Analytics Platform System para SQL**](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nuevos + actualizados (0+1): &nbsp;documentos de **Conexión a SQL**](../connect/new-updated-connect.md)
- [Nuevos + actualizados (0+1): &nbsp;documentos del **Motor de base de datos de SQL**](../database-engine/new-updated-database-engine.md)
- [Nuevos + actualizados (12+1): **documentos de** Integration Services para SQL](../integration-services/new-updated-integration-services.md)
- [Nuevos + actualizados (6+2): &nbsp;documentos de **Linux para SQL**](../linux/new-updated-linux.md)
- [Nuevos + actualizados (15+0): **documentos de** PowerShell para SQL](../powershell/new-updated-powershell.md)
- [Nuevos + actualizados (2+9): &nbsp;documentos de **Bases de datos relacionales para SQL**](../relational-databases/new-updated-relational-databases.md)
- [Nuevos + actualizados (1+0): &nbsp;documentos de **Reporting Services para SQL**](../reporting-services/new-updated-reporting-services.md)
- [Nuevos + actualizados (1+1): &nbsp;documentos de **SQL Operations Studio**](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nuevos + actualizados (1+1): &nbsp;documentos de **Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Nuevos + actualizados (0+1): &nbsp;documentos de **SQL Server Data Tools (SSDT)**](../ssdt/new-updated-ssdt.md)
- [Nuevos + actualizados (1+2): &nbsp;documentos de **SQL Server Management Studio (SSMS)**](../ssms/new-updated-ssms.md)
- [Nuevos + actualizados (0+2): &nbsp;documentos de **Transact-SQL**](../t-sql/new-updated-t-sql.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Áreas temáticas que *no* tienen artículos nuevos o actualizados recientemente


- [Nuevos + Actualizados (0+0): documentos de **Data Migration Assistant (DMA) para SQL**](../dma/new-updated-dma.md)
- [Nuevos y actualizados (0 + 0): **ActiveX Data Objects (ADO) para SQL** documentos](../ado/new-updated-ado.md)
- [Nuevos + actualizados (0+0): documentos de **Analysis Services para SQL**](../analysis-services/new-updated-analysis-services.md)
- [Nuevos y actualizados (0 + 0): **Data Quality Services para SQL** documentos](../data-quality-services/new-updated-data-quality-services.md)
- [Nuevos y actualizados (0 + 0): **extensiones de minería de datos (DMX) para SQL** documentos](../dmx/new-updated-dmx.md)
- [Nuevos + actualizados (0+0): documentos de **Master Data Services (MDS) para SQL**](../master-data-services/new-updated-master-data-services.md)
- [Nuevos y actualizados (0 + 0): **expresiones multidimensionales (MDX) para SQL** documentos](../mdx/new-updated-mdx.md)
- [Nuevos y actualizados (0 + 0): **ODBC (conectividad abierta de base de datos) para SQL** documentos](../odbc/new-updated-odbc.md)
- [Nuevos y actualizados (0 + 0): **ejemplos para SQL** documentos](../samples/new-updated-samples.md)
- [Nuevos y actualizados (0 + 0): **SQL Server Migration Assistant (SSMA)** documentos](../ssma/new-updated-ssma.md)
- [Nuevos + actualizados (0+0): documentos de **Herramientas para SQL**](../tools/new-updated-tools.md)
- [Nuevos y actualizados (0 + 0): **XQuery para SQL** documentos](../xquery/new-updated-xquery.md)


