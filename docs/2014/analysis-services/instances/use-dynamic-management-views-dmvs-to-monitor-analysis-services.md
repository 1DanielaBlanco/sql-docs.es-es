---
title: Usar vistas de administración dinámica (DMV) para supervisar Analysis Services | Documentos de Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 22b82b2d-867f-4ebf-9288-79d1cdd62f18
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 3ef037d3d2745a5cfce8949ca7ac14e0d5743326
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36203071"
---
# <a name="use-dynamic-management-views-dmvs-to-monitor-analysis-services"></a>Usar vistas de administración dinámica (DMV) para supervisar Analysis Services
  Las vistas de administración dinámica (DMV) de Analysis Services son estructuras de consulta que exponen información sobre las operaciones del servidor local y el estado del servidor. La estructura de consulta es una interfaz para los conjuntos de filas de esquema que devuelven metadatos y la información de supervisión acerca de una instancia de Analysis Services.  
  
 Para la mayoría de las consultas DMV, use un `SELECT` instrucción y `$System` esquema con un conjunto de filas de esquema XML/A.  
  
```  
SELECT * FROM $System.<schemaRowset>  
```  
  
 Las consultas DMV devuelven información sobre el estado del servidor actual en el momento en que se ejecutó la consulta. Para supervisar las operaciones en tiempo real, utilice el seguimiento en su lugar. Para más información, consulte [Use SQL Server Profiler to Monitor Analysis Services](use-sql-server-profiler-to-monitor-analysis-services.md).  
  
 En este tema se incluyen las secciones siguientes:  
  
 [Ventajas del uso de las consultas DMV](#bkmk_ben)  
  
 [Ejemplos y escenarios](#bkmk_ex)  
  
 [Sintaxis de las consultas](#bkmk_syn)  
  
 [Herramientas y permisos](#bkmk_tools)  
  
 [Referencia de DMV](#bkmk_ref)  
  
##  <a name="bkmk_ben"></a> Ventajas del uso de las consultas DMV  
 Las consultas DMV devuelven información acerca de las operaciones y el consumo de recursos que no están directamente disponibles a través de otros medios.  
  
 Las consultas DMV son una alternativa a la ejecución de comandos de detección XML/A. Para la mayoría de los administradores, escribir una consulta DMV es más sencillo porque la sintaxis de la consulta se basa en SQL. Además, el conjunto de resultados se devuelve en formato tabular que es más fácil de leer y de copiar.  
  
##  <a name="bkmk_ex"></a> Ejemplos y escenarios  
 Una consulta DMV puede ayudarle a responder preguntas sobre las sesiones activas y las conexiones, y qué objetos están utilizando la mayoría de la CPU o de la memoria en un momento concreto. En esta sección se proporcionan ejemplos de escenarios en los que las consultas DMV se usan con más frecuencia. También puede revisar la [Guía de operaciones de SQL Server 2008 R2 Analysis Services](http://go.microsoft.com/fwlink/?LinkID=225539&clcid=0x409) para consultar las características adicionales sobre cómo usar las consultas DMV para supervisar una instancia de servidor.  
  
 `Select * from $System.discover_object_activity` /** Esta consulta informa de la actividad de los objetos desde que el servicio se ha iniciado por última vez. Para ver consultas de ejemplo basadas en esta DMV, vea [Nuevo System.Discover_Object_Activity](http://go.microsoft.com/fwlink/?linkid=221322)(Nuevo System.Discover_Object_Activity).  
  
 `Select * from $System.discover_object_memory_usage` /** Esta consulta informa del consumo de memoria de cada objeto.  
  
 `Select * from $System.discover_sessions` /** Esta consulta informa de las sesiones activas, incluido el usuario de la sesión y la duración.  
  
 `Select * from $System.discover_locks` /** Esta consulta devuelve una instantánea de los bloqueos usados en un momento específico.  
  
##  <a name="bkmk_syn"></a> Sintaxis de las consultas  
 El motor de consultas para las DMV es el analizador de minería de datos. La sintaxis de consulta DMV se basa en la instrucción [SELECT &#40;DMX&#41;](/sql/dmx/select-dmx).  
  
 Aunque la sintaxis de las consultas DMV se basan en una instrucción SQL SELECT, no admite la sintaxis completa de una instrucción SELECT. Fundamentalmente, no se admiten JOIN, GROUP BY, LIKE, CAST ni CONVERT.  
  
```  
SELECT [DISTINCT] [TOP <n>] <select list>  
FROM $System.<schemaRowset>  
[WHERE <condition expression>]  
[ORDER BY <expression>[DESC|ASC]]  
```  
  
 El siguiente ejemplo de DISCOVER_CALC_DEPENDENCY muestra el uso de la cláusula WHERE para proporcionar un parámetro a la consulta:  
  
```  
SELECT * FROM $System.DISCOVER_CALC_DEPENDENCY  
WHERE OBJECT_TYPE = 'ACTIVE_RELATIONSHIP'  
```  
  
 O bien, para los conjuntos de filas de esquema que tienen restricciones, la consulta debe incluir la función SYSTEMRESTRICTSCHEMA. El ejemplo siguiente devuelve los metadatos CSDL sobre los modelos tabulares que se ejecutan en un servidor en modo tabular. Observe que CATALOG_NAME distingue entre mayúsculas y minúsculas:  
  
```  
Select * from SYSTEMRESTRICTSCHEMA ($System.Discover_csdl_metadata, [CATALOG_NAME] = 'Adventure Works DW')  
```  
  
##  <a name="bkmk_tools"></a> Herramientas y permisos  
 Debe tener permisos de administrador del sistema en la instancia de Analysis Services para consultar una DMV.  
  
 Puede usar cualquier aplicación cliente que admita consultas DMX o MDX, incluidos SQL Server Management Studio, un informe de Reporting Services o un panel de PerformancePoint.  
  
 Para ejecutar una consulta de DMV Management Studio, conéctese a la instancia que desea consultar y haga clic en **Nueva consulta**. Puede ejecutar una consulta desde una ventana de consulta DMX o MDX.  
  
##  <a name="bkmk_ref"></a> Referencia de DMV  
 No todos los conjuntos de filas de esquema tienen una interfaz DMV. Para obtener una lista de todos los conjuntos de filas de esquema que se pueden consultar mediante DMV, ejecute la consulta siguiente.  
  
```  
SELECT * FROM $System.DBSchema_Tables   
WHERE TABLE_TYPE = 'SCHEMA'   
ORDER BY TABLE_NAME ASC  
```  
  
> [!NOTE]  
>  Si no hay una DMV para un conjunto de filas determinado, el servidor devuelve el siguiente error: "el \<schemarowset > el servidor no reconoció el tipo de solicitud". El resto de los errores indica problemas con la sintaxis.  
  
|Conjunto de filas|Descripción|  
|------------|-----------------|  
|[Conjunto de filas DBSCHEMA_CATALOGS](../schema-rowsets/ole-db/dbschema-catalogs-rowset.md)|Devuelve una lista de bases de datos de Analysis Services en la conexión actual.|  
|[Conjunto de filas DBSCHEMA_COLUMNS](../schema-rowsets/ole-db/dbschema-columns-rowset.md)|Devuelve una lista de todas las columnas en la base de datos actual. Puede usar esta lista para generar una consulta DMV.|  
|[Conjunto de filas DBSCHEMA_PROVIDER_TYPES](../schema-rowsets/ole-db/dbschema-provider-types-rowset.md)|Devuelve las propiedades de los tipos de datos base admitidos por el proveedor de datos OLE DB.|  
|[Conjunto de filas DBSCHEMA_TABLES](../schema-rowsets/ole-db/dbschema-tables-rowset.md)|Devuelve una lista de todas las tablas en la base de datos actual. Puede usar esta lista para generar una consulta DMV.|  
|[Conjunto de filas DISCOVER_CALC_DEPENDENCY](../schema-rowsets/xml/discover-calc-dependency-rowset.md)|Devuelve una lista de las columnas y las tablas usadas en un modelo que tienen dependencias en otras columnas y tablas.|  
|[Conjunto de filas DISCOVER_COMMAND_OBJECTS](../schema-rowsets/xml/discover-command-objects-rowset.md)|Proporciona información sobre el uso de los recursos y la actividad en los objetos que utiliza el comando al que se hace referencia.|  
|[Conjunto de filas DISCOVER_COMMANDS](../schema-rowsets/xml/discover-commands-rowset.md)|Proporciona información de la actividad y el uso de los recursos acerca del comando que se ejecuta actualmente.|  
|[Conjunto de filas DISCOVER_CONNECTIONS](../schema-rowsets/xml/discover-connections-rowset.md)|Proporciona información de la actividad y el uso de los recursos acerca de las conexiones abiertas para Analysis Services.|  
|[Conjunto de filas DISCOVER_CSDL_METADATA](../schema-rowsets/xml/discover-csdl-metadata-rowset.md)|Devuelve información sobre un modelo tabular.<br /><br /> Requiere la adición de SYSTEMRESTRICTSCHEMA y parámetros adicionales.|  
|[Conjunto de filas DISCOVER_DB_CONNECTIONS](../schema-rowsets/xml/discover-db-connections-rowset.md)|Proporciona información de la actividad y el uso de los recursos acerca de las conexiones abiertas desde Analysis Services a orígenes de datos externos, por ejemplo, durante el procesamiento o la importación.|  
|[Conjunto de filas DISCOVER_DIMENSION_STAT](../schema-rowsets/xml/discover-dimension-stat-rowset.md)|Devuelve los atributos de una dimensión o las columnas de una tabla, según el tipo de modelo.|  
|[Conjunto de filas DISCOVER_ENUMERATORS](../schema-rowsets/xml/discover-enumerators-rowset.md)|Devuelve los metadatos sobre los enumeradores admitidos para un origen de datos concreto.|  
|[Conjunto de filas DISCOVER_INSTANCES](../schema-rowsets/ole-db-olap/discover-instances-rowset.md)|Devuelve información relacionada con la instancia especificada.<br /><br /> Requiere la adición de SYSTEMRESTRICTSCHEMA y parámetros adicionales.|  
|[Conjunto de filas DISCOVER_JOBS](../schema-rowsets/xml/discover-jobs-rowset.md)|Devuelve información acerca de los trabajos actuales.|  
|[Conjunto de filas DISCOVER_KEYWORDS &#40;XMLA&#41;](../schema-rowsets/xml/discover-keywords-rowset-xmla.md)|Devuelve la lista de palabras clave reservadas.|  
|[Conjunto de filas DISCOVER_LITERALS](../schema-rowsets/xml/discover-literals-rowset.md)|Devuelve la lista de literales, incluidos los tipos de datos y valores, admitidos por el proveedor de XMLA.|  
|[Conjunto de filas DISCOVER_LOCKS](../schema-rowsets/xml/discover-locks-rowset.md)|Devuelve una instantánea de los bloqueos utilizados en un momento concreto.|  
|[Conjunto de filas DISCOVER_MEMORYGRANT](../schema-rowsets/xml/discover-memorygrant-rowset.md)|Devuelve información acerca de la memoria asignada por Analysis Services en el inicio.|  
|[Conjunto de filas DISCOVER_MEMORYUSAGE](../schema-rowsets/xml/discover-memoryusage-rowset.md)|Muestra el uso de memoria de objetos específicos.|  
|[Conjunto de filas DISCOVER_OBJECT_ACTIVITY](../schema-rowsets/xml/discover-object-activity-rowset.md)|Informa de la actividad de los objetos desde que el servicio se inició por última vez.|  
|[Conjunto de filas DISCOVER_OBJECT_MEMORY_USAGE](../schema-rowsets/xml/discover-object-memory-usage-rowset.md)|Informes del consumo de memoria del objeto.|  
|[Conjunto de filas DISCOVER_PARTITION_DIMENSION_STAT](../schema-rowsets/xml/discover-partition-dimension-stat-rowset.md)|Proporciona información sobre los atributos de una dimensión.<br /><br /> Requiere la adición de SYSTEMRESTRICTSCHEMA y parámetros adicionales.|  
|[Conjunto de filas DISCOVER_PARTITION_STAT](../schema-rowsets/xml/discover-partition-stat-rowset.md)|Proporciona información sobre las particiones de una dimensión, una tabla o un grupo de medida.<br /><br /> Requiere la adición de SYSTEMRESTRICTSCHEMA y parámetros adicionales.|  
|[Conjunto de filas DISCOVER_PERFORMANCE_COUNTERS](../schema-rowsets/xml/discover-performance-counters-rowset.md)|Muestra las columnas usadas en un contador de rendimiento.<br /><br /> Requiere la adición de SYSTEMRESTRICTSCHEMA y parámetros adicionales.|  
|[Conjunto de filas DISCOVER_PROPERTIES](../schema-rowsets/xml/discover-properties-rowset.md)|Devuelve información sobre las propiedades admitidas por XMLA para el origen de datos especificado.|  
|[Conjunto de filas DISCOVER_SCHEMA_ROWSETS](../schema-rowsets/xml/discover-schema-rowsets-rowset.md)|Devuelve nombres, restricciones, la descripción y otra información para todos los valores de enumeración admitidos por XMLA.|  
|[Conjunto de filas DISCOVER_SESSIONS](../schema-rowsets/xml/discover-sessions-rowset.md)|Informa de las sesiones activas, incluido el usuario de la sesión y la duración.|  
|[Conjunto de filas DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS](../schema-rowsets/xml/discover-storage-table-column-segments-rowset.md)|Proporciona información en el nivel de columna y segmento acerca de las tablas de almacenamiento que usa una base de datos de Analysis Services que se ejecuta en modo Tabular o de SharePoint.|  
|[Conjunto de filas DISCOVER_STORAGE_TABLE_COLUMNS](../schema-rowsets/xml/discover-storage-table-columns-rowset.md)|Permite al cliente determinar la asignación de columnas a las tablas de almacenamiento que usa una base de datos de Analysis Services que se ejecuta en modo Tabular o de SharePoint.|  
|[Conjunto de filas DISCOVER_STORAGE_TABLES](../schema-rowsets/xml/discover-storage-tables-rowset.md)|Devuelve información sobre las tablas usadas para el almacenamiento de modelos en una base de datos del modelo Tabular.|  
|[Conjunto de filas DISCOVER_TRACE_COLUMNS](../schema-rowsets/xml/discover-trace-columns-rowset.md)|Devuelve una descripción XML de las columnas disponibles en un seguimiento.|  
|[Conjunto de filas DISCOVER_TRACE_DEFINITION_PROVIDERINFO](../schema-rowsets/xml/discover-trace-definition-providerinfo-rowset.md)|Devuelve el nombre y la información de versión del proveedor.|  
|[Conjunto de filas DISCOVER_TRACE_EVENT_CATEGORIES](../schema-rowsets/xml/discover-trace-event-categories-rowset.md)|Devuelve una lista de las categorías disponibles.|  
|[Conjunto de filas DISCOVER_TRACES](../schema-rowsets/xml/discover-traces-rowset.md)|Devuelve una lista de los seguimientos que se ejecutan activamente en la conexión actual.|  
|[Conjunto de filas DISCOVER_TRANSACTIONS](../schema-rowsets/xml/discover-transactions-rowset.md)|Devuelve una lista de las transacciones que se ejecutan activamente en la conexión actual.|  
|[Conjunto de filas DISCOVER_XEVENT_TRACE_DEFINITION](../dev-guide/discover-xevent-trace-definition-rowset.md)|Devuelve una lista de los seguimientos xevent que se ejecutan activamente en la conexión actual.|  
|[Conjunto de filas DMSCHEMA_MINING_COLUMNS](../schema-rowsets/data-mining/dmschema-mining-columns-rowset.md)|Muestra las columnas individuales de todos los modelos de minería de datos disponibles en la conexión actual.|  
|[Conjunto de filas DMSCHEMA_MINING_FUNCTIONS](../schema-rowsets/data-mining/dmschema-mining-functions-rowset.md)|Devuelve una lista de las funciones admitidas por los algoritmos de minería de datos del servidor.|  
|[Conjunto de filas DMSCHEMA_MINING_MODEL_CONTENT](../schema-rowsets/data-mining/dmschema-mining-model-content-rowset.md)|Devuelve un conjunto de filas que consta de las columnas que describen el modelo actual.|  
|[Conjunto de filas DMSCHEMA_MINING_MODEL_CONTENT_PMML](../schema-rowsets/data-mining/dmschema-mining-model-content-pmml-rowset.md)|Devuelve un conjunto de filas que consta de las columnas que describen el modelo actual en el formato PMML.|  
|[Conjunto de filas DMSCHEMA_MINING_MODEL_XML](../schema-rowsets/data-mining/dmschema-mining-model-xml-rowset.md)|Devuelve un conjunto de filas que consta de las columnas que describen el modelo actual en el formato PMML.|  
|[Conjunto de filas DMSCHEMA_MINING_MODELS](../schema-rowsets/data-mining/dmschema-mining-models-rowset.md)|Devuelve una lista de modelos de minería de datos en la base de datos actual.|  
|[Conjunto de filas DMSCHEMA_MINING_SERVICE_PARAMETERS](../schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset.md)|Devuelve una lista de los parámetros de los algoritmos en el servidor.|  
|[Conjunto de filas DMSCHEMA_MINING_SERVICES](../schema-rowsets/data-mining/dmschema-mining-services-rowset.md)|Proporciona una lista de los algoritmos de minería de datos disponibles en el servidor.|  
|[Conjunto de filas DMSCHEMA_MINING_STRUCTURE_COLUMNS](../schema-rowsets/data-mining/dmschema-mining-structure-columns-rowset.md)|Devuelve una lista de todas las columnas de todos los modelos de minería de datos disponibles en la conexión actual.|  
|[Conjunto de filas DMSCHEMA_MINING_STRUCTURES](../schema-rowsets/data-mining/dmschema-mining-structures-rowset.md)|Enumera las estructuras de minería de datos disponibles en la conexión actual.|  
|[Conjunto de filas MDSCHEMA_CUBES](../schema-rowsets/ole-db-olap/mdschema-cubes-rowset.md)|Devuelve información sobre los cubos que están definidos en la base de datos actual.|  
|[Conjunto de filas MDSCHEMA_DIMENSIONS](../schema-rowsets/ole-db-olap/mdschema-dimensions-rowset.md)|Devuelve información sobre las dimensiones que están definidas en la base de datos actual.|  
|[Conjunto de filas MDSCHEMA_FUNCTIONS](../schema-rowsets/ole-db-olap/mdschema-functions-rowset.md)|Devuelve una lista de las funciones que están disponibles para las aplicaciones cliente conectadas a la base de datos.|  
|[Conjunto de filas MDSCHEMA_HIERARCHIES](../schema-rowsets/ole-db-olap/mdschema-hierarchies-rowset.md)|Devuelve información sobre las jerarquías que están definidas en la base de datos actual.|  
|[Conjunto de filas MDSCHEMA_INPUT_DATASOURCES](../schema-rowsets/ole-db-olap/mdschema-input-datasources-rowset.md)|Devuelve información sobre los objetos de origen de datos que están definidos en la base de datos actual.|  
|[Conjunto de filas MDSCHEMA_KPIS](../schema-rowsets/ole-db-olap/mdschema-kpis-rowset.md)|Devuelve información sobre las KPI que están definidas en la base de datos actual.|  
|[Conjunto de filas MDSCHEMA_LEVELS](../schema-rowsets/ole-db-olap/mdschema-levels-rowset.md)|Devuelve información acerca de los niveles de las jerarquías que están definidos en la base de datos actual.|  
|[Conjunto de filas MDSCHEMA_MEASUREGROUP_DIMENSIONS](../schema-rowsets/ole-db-olap/mdschema-measuregroup-dimensions-rowset.md)|Muestra la dimensión de los grupos de medida.|  
|[Conjunto de filas MDSCHEMA_MEASUREGROUPS](../schema-rowsets/ole-db-olap/mdschema-measuregroups-rowset.md)|Devuelve una lista de los grupos de medida de la conexión actual.|  
|[Conjunto de filas MDSCHEMA_MEASURES](../schema-rowsets/ole-db-olap/mdschema-measures-rowset.md)|Devuelve una lista de las medidas en la conexión actual.|  
|[Conjunto de filas MDSCHEMA_MEMBERS](../schema-rowsets/ole-db-olap/mdschema-members-rowset.md)|Devuelve una lista de todos los miembros en la conexión actual, ordenada según la base de datos, el cubo y la dimensión.|  
|[Conjunto de filas MDSCHEMA_PROPERTIES](../schema-rowsets/ole-db-olap/mdschema-properties-rowset.md)|Devuelve el nombre completo de cada propiedad, junto con el tipo de propiedad, el tipo de datos y otros metadatos.|  
|[Conjunto de filas MDSCHEMA_SETS](../schema-rowsets/ole-db-olap/mdschema-sets-rowset.md)|Devuelve una lista de los conjuntos definidos en la conexión actual.|  
  
## <a name="see-also"></a>Vea también  
 [Guía de operaciones de SQL Server 2008 R2 Analysis Services](http://go.microsoft.com/fwlink/?LinkID=225539&clcid=0x409)   
 [Nuevo System.Discover_Object_Activity](http://go.microsoft.com/fwlink/?linkid=221322)   
 [Nueva función SYSTEMRESTRICTEDSCHEMA para conjuntos de filas restringidas y DMV](http://go.microsoft.com/fwlink/?LinkId=231885)  
  
  
