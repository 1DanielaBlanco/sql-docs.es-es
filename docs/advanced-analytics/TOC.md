# Información general

## [¿Qué es SQL Server Machine Learning Services?](what-is-sql-server-machine-learning.md)
### [Análisis en base de datos](r/sql-server-r-services.md)
### [Servidor independiente](r/r-server-standalone.md)
## [Nuevas características](what-s-new-in-sql-server-machine-learning-services.md)
## [Características por edición](r/differences-in-r-features-between-editions-of-sql-server.md)

# [Arquitectura](architecture-overview-machine-learning.md)
## [R](r/architecture-overview-sql-server-r.md)
### [Interoperabilidad de R](r/r-interoperability-in-sql-server.md)
### [Componentes que admiten la integración de R](r/new-components-in-sql-server-to-support-r.md)
### [Seguridad para R](r/security-overview-sql-server-r.md)
## [Python](python/architecture-overview-sql-server-python.md)
### [Python en Machine Learning Services](python/sql-server-python-services.md)
### [Interoperabilidad de Python](python/python-interoperability.md)
### [Componentes para admitir Python](python/new-components-in-sql-server-to-support-python-integration.md)
### [Seguridad de Python](python/security-overview-sql-server-python-services.md)
<!-- ### [How To Create a Resource Pool for Python](python/how-to-create-a-resource-pool-for-python.md)-->
<!-- ### [Extended Events for Python](python/extended-events-for-python.md)-->
<!-- ### [DMVs for Python](python/dmvs-for-python.md)-->
<!-- ### [Resource Governance for Python](python/resource-governance-for-python.md)-->

# Install 

## [Análisis en base de datos](install/sql-machine-learning-services-windows-install.md)
## [Servidor independiente](install/sql-machine-learning-standalone-windows-install.md)
## [Modelos entrenados previamente](r/install-pretrained-models-sql-server.md)
## SQL Server 2016
### [R Services (en bases de datos)](install/sql-r-services-windows-install.md)
### [R Server (Standalone)](install/sql-r-standalone-windows-install.md)
## [Instalación del símbolo del sistema](install/sql-ml-component-commandline-install.md)
## [Instalación sin conexión (sin Internet)](install/sql-ml-component-install-without-internet-access.md)
## [Actualización R y Python](r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)
## [Configuración de las herramientas de R](r/set-up-a-data-science-client.md)
## [Configuración de las herramientas de Python](python/setup-python-client-tools-sql.md)

# [Tutoriales, muestras y soluciones](tutorials/machine-learning-services-tutorials.md)

## [R](tutorials/sql-server-r-tutorials.md)
### [R: Usar el código de R en Transact-SQL](tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
#### [Trabajar con entradas y salidas](tutorials/rtsql-working-with-inputs-and-outputs.md)
#### [Tipos de datos y objetos de datos de R y SQL](tutorials/rtsql-r-and-sql-data-types-and-data-objects.md)
#### [Uso de funciones de R con datos de SQL Server](tutorials/rtsql-using-r-functions-with-sql-server-data.md)
#### [Crear un modelo predictivo](tutorials/rtsql-create-a-predictive-model-r.md)
#### [Predecir y trazar a partir del modelo](tutorials/rtsql-predict-and-plot-from-model.md)
### [R: Tutorial integral de ciencia de datos](tutorials/walkthrough-data-science-end-to-end-walkthrough.md)
#### [Requisitos previos del tutorial de ciencia de datos](tutorials/walkthrough-prerequisites-for-data-science-walkthroughs.md)
#### [Preparar los datos](tutorials/walkthrough-prepare-the-data.md)
#### [Explorar los datos con SQL](tutorials/walkthrough-view-and-explore-the-data.md)
#### [Resumir los datos con R](tutorials/walkthrough-view-and-summarize-data-using-r.md)
#### [Crear gráficos y trazados con R](tutorials/walkthrough-create-graphs-and-plots-using-r.md)
#### [Crear características de datos mediante SQL y R](tutorials/walkthrough-create-data-features.md)
#### [Generar y guardar el modelo](tutorials/walkthrough-build-and-save-the-model.md)
#### [Implementar y usar el modelo](tutorials/walkthrough-deploy-and-use-the-model.md)
### [R: Análisis detallado de ciencia de datos con RevoScaleR](tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
#### [Trabajar con datos de SQL Server](tutorials/deepdive-work-with-sql-server-data-using-r.md)
#### [Crear objetos de datos de SQL Server mediante RxSqlServerData](tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)
#### [Consultar y modificar los datos de SQL Server](tutorials/deepdive-query-and-modify-the-sql-server-data.md)
#### [Definir y usar contextos de cálculo](tutorials/deepdive-define-and-use-compute-contexts.md)
#### [Crear y ejecutar scripts de R](tutorials/deepdive-create-and-run-r-scripts.md)
#### [Visualizar datos de SQL Server con R](tutorials/deepdive-visualize-sql-server-data-using-r.md)
#### [Crear modelos](tutorials/deepdive-create-models.md)
#### [Puntuación de nuevos datos](tutorials/deepdive-score-new-data.md)
#### [Transformar datos mediante R](tutorials/deepdive-transform-data-using-r.md)
#### [Cargar datos en memoria mediante rxImport](tutorials/deepdive-load-data-into-memory-using-rximport.md)
#### [Crear una nueva tabla de SQL Server mediante rxDataStep](tutorials/deepdive-create-new-sql-server-table-using-rxdatastep.md)
#### [Realizar análisis de fragmentación mediante rxDataStep](tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)
#### [Analizar datos en el contexto del proceso local](tutorials/deepdive-analyze-data-in-local-compute-context.md)
#### [Mover datos entre SQL Server y el archivo XDF](tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)
#### [Crear una simulación sencilla](tutorials/deepdive-create-a-simple-simulation.md)
### [R: Análisis en base de datos para desarrolladores de SQL](tutorials/sqldev-in-database-r-for-sql-developers.md)
#### [Paso 1: Descargar los datos de ejemplo](tutorials/sqldev-download-the-sample-data.md)
#### [Paso 2: Importar datos a SQL Server mediante PowerShell](r/sqldev-import-data-to-sql-server-using-powershell.md)
#### [Paso 3: Explorar y visualizar los datos](tutorials/sqldev-explore-and-visualize-the-data.md)
#### [Paso 4: Crear características de datos mediante T-SQL](tutorials/sqldev-create-data-features-using-t-sql.md)
#### [Paso 5: Entrenar y guardar un modelo con T-SQL](r/sqldev-train-and-save-a-model-using-t-sql.md)
#### [Paso 6: Hacer operativo el modelo](tutorials/sqldev-operationalize-the-model.md)

## [Python](tutorials/sql-server-python-tutorials.md)
### [Python: Ejecutar Python mediante T-SQL](tutorials/run-python-using-t-sql.md)
#### [Encapsulamiento de Python en un procedimiento almacenado](tutorials/wrap-python-in-tsql-stored-procedure.md)
#### [Entrenamiento y puntuación de un modelo de Python en SQL Server](tutorials/train-score-using-python-in-tsql.md)
#### [Creación de un modelo usando revoscalepy en un contexto de proceso de SQL Server](tutorials/use-python-revoscalepy-to-create-model.md)
### [Python: Análisis en base de datos para desarrolladores de SQL](tutorials/sqldev-in-database-python-for-sql-developers.md)
#### [Descargar datos de ejemplo](tutorials/sqldev-py1-download-the-sample-data.md)
#### [Importar datos a SQL Server](tutorials/sqldev-py2-import-data-to-sql-server-using-powershell.md)
#### [Explorar y visualizar datos](tutorials/sqldev-py3-explore-and-visualize-the-data.md)
#### [Crear características de datos mediante T-SQL](tutorials/sqldev-py4-create-data-features-using-t-sql.md)
#### [Entrenar y guardar el modelo](tutorials/sqldev-py5-train-and-save-a-model-using-t-sql.md)
#### [Hacer operativo el modelo](tutorials/sqldev-py6-operationalize-the-model.md)
## [Ejemplos](https://github.com/Microsoft/sql-server-samples)
## [Soluciones](tutorials/data-science-scenarios-and-solution-templates.md)

# [Procedimiento](r/sql-server-machine-learning-tasks.md)

## [Administración de paquetes](r/r-package-management-for-sql-server-r-services.md)
### [Paquetes predeterminados](r/installing-and-managing-r-packages.md)
### [Obtención de información del paquete](r/determine-which-packages-are-installed-on-sql-server.md)
### [Instalación de paquetes de R adicionales](r/install-additional-r-packages-on-sql-server.md)
### [Instalación de paquetes de Python adicionales](python/install-additional-python-packages-on-sql-server.md)
### Solo R
#### [Habilitación de la administración de paquetes de R remota](r/r-package-how-to-enable-or-disable.md)
#### [Funciones de RevoScaleR para administración de paquetes de R](r/use-revoscaler-to-manage-r-packages.md)
#### [Sincronización de paquetes de R](r/package-install-uninstall-and-sync.md)
#### [miniCRAN para el repositorio local de paquetes de R](r/create-a-local-package-repository-using-minicran.md)
#### [Soluciones alternativas para "bibliotecas de usuario" de R](r/packages-installed-in-user-libraries.md)

## Modelado y exploración de datos
### [Bibliotecas de R y tipos de datos](r/r-libraries-and-data-types.md)
### [Bibliotecas de Python y tipos de datos](python/python-libraries-and-data-types.md)
### [Puntuación nativa](sql-native-scoring.md)
### [Puntuación en tiempo real](real-time-scoring.md)
### [Modelado de predicción con R](r/data-exploration-and-predictive-modeling-with-r.md)
### [Cómo efectuar una puntuación nativa o en tiempo real](r/how-to-do-realtime-scoring.md)
### [Cargar objetos de R mediante ODBC](r/save-and-load-r-objects-from-sql-server-using-odbc.md)
### [Convertir el código de R para usarlo en Machine Learning Services](r/converting-r-code-for-use-in-sql-server.md)
### [Crear varios modelos mediante rxExecBy](r/creating-multiple-models-using-rxexecby.md)
### [Usar datos de cubos OLAP en R](r/using-data-from-olap-cubes-in-r.md)
### [Crear un procedimiento almacenado mediante sqlrutils](r/how-to-create-a-stored-procedure-using-sqlrutils.md)

## Rendimiento
### [Optimización del rendimiento de R: Información general](r/sql-server-r-services-performance-tuning.md)
### [Optimización del rendimiento de R: Configuración de SQL Server](r/sql-server-configuration-r-services.md)
### [Optimización del rendimiento de R: R y optimización de datos](r/r-and-data-optimization-r-services.md)
### [Optimización del rendimiento de R: Resultados](r/performance-case-study-r-services.md)
### [Usar las funciones de generación de perfiles de código de R](r/using-r-code-profiling-functions.md)

## Administración
### [Configurar y administrar R](r/configuration-sql-server-r-services.md)
### [Opciones de configuración avanzada de Machine Learning Services](r/configure-and-manage-advanced-analytics-extensions.md)
### [Consideraciones de seguridad para el tiempo de ejecución de R en SQL Server](r/security-considerations-for-the-r-runtime-in-sql-server.md)
### [Modificar el grupo de cuentas de usuario de SQL Server Machine Learning Services](r/modify-the-user-account-pool-for-sql-server-r-services.md)
### [Agregar SQLRUserGroup como usuario de base de datos](r/add-sqlrusergroup-to-database.md)
### [Implementar y usar modelos mediante servicios web](operationalization-with-mrsdeploy.md)
### [Administrar y supervisar soluciones](r/managing-and-monitoring-r-solutions.md
### [Regulación de recursos para Machine Learning Services](r/resource-governance-for-r-services.md)
### [Creación de grupos de recursos para el aprendizaje automático](r/how-to-create-a-resource-pool-for-r.md)
### [Eventos extendidos de Machine Learning Services](r/extended-events-for-sql-server-r-services.md)
### [Eventos extendidos para la supervisión de instrucciones PREDICT](xe-event-predict-tsql.md)
### [DMV de Machine Learning Services](r/dmvs-for-sql-server-r-services.md)
### [Uso de funciones de generación de perfiles de código de R](r/using-r-code-profiling-functions.md)
### [Supervisar Machine Learning Services con informes personalizados en Management Studio](r/monitor-r-services-using-custom-reports-in-management-studio.md)

# [Referencia](r/machine-learning-services-r-reference.md)

## [MicrosoftML](using-the-microsoftml-package.md)
## [RevoScaleR](r/revoscaler-overview.md)
### [Funciones de RevoScaleR para los datos de SQL Server](r/scaler-functions-for-working-with-sql-server-data.md)
## [SqlRUtils](r/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)
## [OlapR](r/how-to-create-mdx-queries-using-olapr.md)
## [revoscalepy](python/what-is-revoscalepy.md)

# Recursos

## [Problemas conocidos](known-issues-for-sql-server-machine-learning-services.md)
## [Notas de la versión](https://docs.microsoft.com/sql/sql-server/sql-server-2017-release-notes)
## [Artículos nuevos y actualizados](new-updated-advanced-analytics.md)

## [Sugerencias de instalación y solución de problemas](machine-learning-troubleshooting-faq.md)
### [Configurar una máquina virtual](r/installing-sql-server-r-services-on-an-azure-virtual-machine.md)
### [Recopilación de datos para la solución de problemas](data-collection-ml-troubleshooting-process.md)
### [Preguntas más frecuentes sobre actualización e instalación](r/upgrade-and-installation-faq-sql-server-r-services.md)
### [Problemas comunes para la ejecución de scripts externos](common-issues-external-script-execution.md)

## Blogs
### [SQL Server](https://blogs.technet.microsoft.com/dataplatforminsider/)
### [R Server](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/)
### [Aprendizaje automático](https://blogs.technet.microsoft.com/machinelearning/)

## Foros de comentarios
### [SQL Server](https://social.msdn.microsoft.com/Forums/sqlserver/home?category=sqlserver)
### [Microsoft R Server](https://social.msdn.microsoft.com/Forums/home?forum=MicrosoftR)
