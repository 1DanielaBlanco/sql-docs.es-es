---
title: Ejecutar la consola SSMA (DB2ToSQL) | Documentos de Microsoft
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: ce63f633-067d-4f04-b8e9-e1abd7ec740b
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: abfd3a12482d71f808887b1f3f987d0bd1582c76
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2018
ms.locfileid: "34774811"
---
# <a name="executing-the-ssma-console-db2tosql"></a>Ejecutar la consola SSMA (DB2ToSQL)
Microsoft proporciona un conjunto robusto de script de comandos del archivo para ejecutar y controlar las actividades SSMA. Las secciones posteriores detallan los mismos. La aplicación de consola utiliza ciertos comandos del archivo de secuencia de comandos estándar como enumerados en esta sección.  
  
## <a name="project-script-file-commands"></a>Comandos del archivo de Script de proyecto  
Los comandos de proyectos controlan la creación de proyectos, abrir, guardar y salir de proyectos.  
  
**Command**  
  
Crear nueva-proyectos  
  
Crea un nuevo proyecto SSMA.  
  
**Script**  
  
-   `project-folder` indica la carpeta del proyecto obtener creado.  
  
-   `project-name` indica el nombre del proyecto. {cadena}  
  
-   `overwrite-if-exists`Atributo opcional indica si se debe sobrescribir un proyecto existente. {valor} booleano  
  
-   `project-type:`Atributo opcional. Indica si el tipo de proyecto, es decir, "sql-server-2005" proyecto o proyecto "sql-server-2008" o "sql-server-2012" proyecto o proyecto de "sql-server-2014" o "sql azure". Valor predeterminado es "sql-server-2014".  
  
**Ejemplo:**  
  
```xml  
<create-new-project  
  
   project-folder="<project-folder>"  
  
   project-name="<project-name>"  
  
   overwrite-if-exists="<true/false>"   (optional)  
  
   project-type="<sql-server-2008 | sql-server-2005 | sql-server-2012 | sql-server-2014>"   (optional)  
  
/>  
```  
Es el atributo 'sobrescribir-if-exists' **false** de forma predeterminada.  
  
El atributo 'tipo de proyecto' es **sql-server-2008** de forma predeterminada.  
  
**Command**  
  
Abrir proyecto  
  
Abre un proyecto existente.  
  
**Script**  
  
-   `project-folder` indica la carpeta del proyecto obtener creado. El comando produce un error si la carpeta especificada no existe.  {cadena}  
  
-   `project-name` indica el nombre del proyecto. El comando produce un error si el proyecto especificado no existe.  {cadena}  
  
**Ejemplo de sintaxis:**  
  
```xml  
<open-project  
  
   project-folder="<project-folder>"  
  
   project-name="<project-name>"  
  
/>  
```  
SSMA para la aplicación de consola de DB2 admite compatibilidad con versiones anteriores. Podrá abrir proyectos creados con una versión anterior de SSMA.  
  
**Command**  
  
Guardar proyecto  
  
Guarda el proyecto de migración.  
  
**Script**  
  
**Ejemplo de sintaxis:**  
  
```xml  
<save-project/>  
```  
**Command**  
  
Cerrar proyecto  
  
Cierra el proyecto de migración.  
  
**Script**  
  
**Ejemplo de sintaxis:**  
  
```xml  
<close-project  
  
   if-modified="<save/error/ignore>"   (optional)  
  
/>  
```  
  
## <a name="database-connection-script-file-commands"></a>Comandos del archivo de Script de conexión de base de datos  
Los comandos de conexión de base de datos ayudan a conectar a la base de datos.  
  
-   El **examinar** no se admite la característica de la interfaz de usuario en la consola.  
  
-   Para obtener más información sobre 'Crear archivos de Script', vea [crear archivos de Script &#40;OracleToSQL&#41;](../../ssma/oracle/creating-script-files-oracletosql.md).  
  
**Command**  
  
datos de origen conectarse  
  
-   Realiza la conexión a la base de datos de origen y carga los metadatos de nivel alto de la base de datos de origen, pero no todos los metadatos.  
  
-   Si no se puede establecer la conexión con el origen, se genera un error y la aplicación de consola detiene la ejecución  
  
**Script**  
  
Definición de servidor se recupera desde el atributo de nombre definido para cada conexión en la sección servidor del archivo de conexión de servidor o el archivo de script.  
  
**Ejemplo de sintaxis:**  
  
```xml  
<connect-source-database  server="<server-unique-name>"/>  
```  
**Command**  
  
forzar carga-origen/destino-bases de datos  
  
-   Carga los metadatos de origen.  
  
-   Resulta útil para trabajar en el proyecto de migración sin conexión.  
  
-   Si no se puede establecer la conexión con el origen o destino, se genera un error y la aplicación de consola detiene la ejecución  
  
**Script**  
  
Requiere uno o varios nodos de la metabase como parámetro de línea de comandos.  
  
**Ejemplo de sintaxis:**  
  
```xml  
<force-load object-name="<object-name>"  
  
  metabase="<source/target>"/>  
```  
o Administrador de configuración de  
  
```xml  
<force-load>  
  
   <metabase-object object-name="<object-name>"/>  
  
</force-load>  
```  
**Command**  
  
datos de origen volver a conectar  
  
-   Vuelve a conectarse a la base de datos de origen pero no carga los metadatos a diferencia del comando de datos de origen de conexión.  
  
-   Si no se puede establecer el volver a conectar con el origen, se genera un error y la aplicación de consola detiene la ejecución.  
  
**Script**  
  
**Ejemplo de sintaxis:**  
  
```xml  
<reconnect-source-database  server="<server-unique-name>"/>  
```  
**Command**  
  
datos de destino conectarse  
  
-   Se conecta a la base de datos de SQL Server de destino y carga los metadatos de nivel alto de la base de datos de destino pero no los metadatos por completo.  
  
-   Si no se puede establecer la conexión con el destino, se genera un error y la aplicación de consola detiene la ejecución.  
  
**Script**  
  
Definición de servidor se recupera desde el atributo de nombre definido para cada conexión en la sección servidor del archivo de conexión de servidor o el archivo de script  
  
**Ejemplo de sintaxis:**  
  
```xml  
<connect-target-database  server="<server-unique-name>"/>  
```  
**Command**  
  
datos de destino volver a conectar  
  
-   Vuelve a conectarse a la base de datos de destino pero no carga los metadatos, a diferencia del comando de conexión de datos de destino.  
  
-   Si la (conexión con el destino re) no se puede establecer, se genera un error y la aplicación de consola detiene la ejecución.  
  
**Script**  
  
**Ejemplo de sintaxis:**  
  
```xml  
<reconnect-target-database  server="<server-unique-name>"/>  
```  
  
## <a name="report-script-file-commands"></a>Comandos del archivo de Script de informe  
Los comandos de informes generan informes sobre el rendimiento de diversas actividades de consola SSMA.  
  
**Command**  
  
informe de evaluación generar  
  
-   Genera informes de evaluación de la base de datos de origen.  
  
-   Si no se realiza la conexión de base de datos de origen antes de ejecutar este comando, se genera un error y se cierra la aplicación de consola.  
  
-   No se pudo conectar al servidor de base de datos de origen durante la ejecución del comando, también se produce en terminar la aplicación de consola.  
  
**Script**  
  
-   `conversion-report-folder:` Especifica la carpeta donde el informe de evaluación puede almacenarse. (opcional) (atributo)  
  
-   `object-name:` Especifica los objetos que tienen en cuenta para la generación de informes de evaluación (puede tener nombres de objeto de indivdual o un nombre de objeto de grupo).  
  
-   `object-type:` Especifica el tipo del objeto especificado en el atributo de nombre de objeto (si se especifica la categoría de objeto de tipo de objeto será "categoría").  
  
-   `conversion-report-overwrite:` Especifica si se debe sobrescribir la carpeta de informes de evaluación si ya existe.  
  
    **Valor predeterminado:** false. (opcional) (atributo)  
  
-   `write-summary-report-to:` Especifica la ruta de acceso donde se generará el informe de resumen.  
  
    Si solo se menciona la ruta de acceso de carpeta, archivo, a continuación, por nombre **AssessmentReport&lt;n&gt;. XML** se crea. (opcional) (atributo)  
  
    Creación de informes tiene dos categorías secundarias adicionales:  
  
    -   `report-errors` (= "true/false", no tiene valor predeterminado como "false" (atributos opcionales))  
  
    -   `verbose` (= "true/false", no tiene valor predeterminado como "false" (atributos opcionales))  
  
**Ejemplo de sintaxis:**  
  
```xml  
<generate-assessment-report  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"  
  
   write-summary-report-to="<file>"   (optional)  
  
   verbose="<true/false>"   (optional)  
  
   report-errors="<true/false>"   (optional)  
  
   assessment-report-folder="<folder-name>"   (optional)  
  
   conversion-report-overwrite="<true/false>"   (optional)  
  
/>  
```  
o Administrador de configuración de  
  
```xml  
<generate-assessment-report  
  
   conversion-report-folder="<folder-name>"   (optional)  
  
   conversion-report-overwrite="<true/false>"   (optional)  
  
>  
  
      <metabase-object object-name="<object-name>"  
  
         object-type="<object-category>"/>  
  
</generate-assessment-report>  
```  
  
## <a name="migration-script-file-commands"></a>Comandos del archivo de Script de migración  
Los comandos de migración convertir el esquema de base de datos de destino en el esquema de origen y migra los datos al servidor de destino. La salida de consola predeterminada para los comandos de migración es informe de salida 'Total' con ningún informe de error detallado: resumen sólo en el nodo de raíz del árbol de objeto de origen.  
  
**Command**  
  
convertir esquema  
  
-   Realiza la conversión de esquema de origen al esquema de destino.  
  
-   Si no se realiza la conexión de base de datos de origen o de destino antes de ejecutar este comando o se produce un error en la conexión con el servidor de base de datos de origen o de destino durante la ejecución del comando, se genera un error y se cierra la aplicación de consola.  
  
**Script**  
  
-   `conversion-report-folder:` Especifica la carpeta donde el informe de evaluación puede almacenarse. (opcional) (atributo)  
  
-   `object-name:` Especifica los objetos de origen que se consideran para la conversión de esquema (puede tener nombres de objeto de indivdual o un nombre de objeto de grupo).  
  
-   `object-type:` Especifica el tipo del objeto especificado en el atributo de nombre de objeto (si se especifica la categoría de objeto de tipo de objeto será "categoría").  
  
-   `conversion-report-overwrite:` Especifica si se debe sobrescribir la carpeta de informes de evaluación si ya existe.  
  
    **Valor predeterminado:** false. (opcional) (atributo)  
  
-   `write-summary-report-to:` Especifica la ruta de acceso donde se generará el informe de resumen.  
  
    Si solo se menciona la ruta de acceso de carpeta, archivo, a continuación, por nombre **SchemaConversionReport&lt;n&gt;. XML** se crea. (opcional) (atributo)  
  
    Creación de informes tiene dos categorías secundarias adicionales:  
  
    -   `report-errors` (= "true/false", no tiene valor predeterminado como "false" (atributos opcionales))  
  
    -   `verbose` (= "true/false", no tiene valor predeterminado como "false" (atributos opcionales))  
  
**Ejemplo de sintaxis:**  
  
```xml  
<convert-schema  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"  
  
   write-summary-report-to="<file-name/folder-name>"   (optional)  
  
   verbose="<true/false>"   (optional)  
  
   report-errors="<true/false>"   (optional)  
  
   conversion-report-folder="<folder-name>"   (optional)  
  
   conversion-report-overwrite="<true/false>"   (optional)  
  
/>  
```  
o Administrador de configuración de  
  
```xml  
<convert-schema  
  
   conversion-report-folder="<folder-name>"   (optional)  
  
   conversion-report-overwrite="<true/false>"   (optional)  
  
      <metabase-object object-name="<object-name>"  
  
         object-type="<object-category>"/>  
  
</convert-schema>  
```  
**Command**  
  
migrar datos: migra los datos de origen al destino.  
  
**Script**  
  
-   `conversion-report-folder:` Especifica la carpeta donde el informe de evaluación puede almacenarse. (opcional) (atributo)  
  
-   `object-name:` Especifica los objetos de origen que se tienen en cuenta para migrar datos (puede tener nombres de objeto de indivdual o un nombre de objeto de grupo).  
  
-   `object-type:` Especifica el tipo del objeto especificado en el atributo de nombre de objeto (si se especifica la categoría de objeto de tipo de objeto será "categoría").  
  
-   `conversion-report-overwrite:` Especifica si se debe sobrescribir la carpeta de informes de evaluación si ya existe.  
  
    **Valor predeterminado:** false. (opcional) (atributo)  
  
-   `write-summary-report-to:` Especifica la ruta de acceso donde se generará el informe de resumen.  
  
    Si solo se menciona la ruta de acceso de carpeta, archivo, a continuación, por nombre **DataMigrationReport&lt;n&gt;. XML** se crea. (opcional) (atributo)  
  
    Creación de informes tiene dos categorías secundarias adicionales:  
  
    -   `report-errors` (= "true/false", no tiene valor predeterminado como "false" (atributos opcionales))  
  
    -   `verbose` (= "true/false", no tiene valor predeterminado como "false" (atributos opcionales))  
  
**Ejemplo de sintaxis:**  
  
```xml  
<migrate-data  
  
   write-summary-report-to="<file-name/folder-name>"  
  
   report-errors="<true/false>"  
  
   verbose="<true/false>">  
  
      <metabase-object object-name="<object-name>"/>  
  
      <metabase-object object-name="<object-name>"/>  
  
      <metabase-object object-name="<object-name>"/>  
  
      <data-migration-connection  
  
         source-use-last-used="true"/source-server="<server-unique-name>"  
  
         target-use-last-used="true"/target-server="<server-unique-name>"/>  
  
</migrate-data>  
```  
o Administrador de configuración de  
  
```xml  
<migrate-data  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"  
  
   write-summary-report-to="<file-name/folder-name>"  
  
   report-errors="<true/false>"  
  
   verbose="<true/false>"/>  
```  
  
## <a name="migration-preparation-script-file-commands"></a>Comandos del archivo de secuencia de comandos de preparación de migración  
El comando de preparación de la migración inicia la asignación de esquema entre las bases de datos de origen y de destino.  
  
**Command**  
  
esquema de asignación  
  
Asignación de esquema de base de datos de origen al esquema de destino.  
  
**Script**  
  
-   `source-schema` Especifica el esquema de origen que se va a migrar.  
  
-   `sql-server-schema` Especifica el esquema de destino donde los deseamos que desea migrar.  
  
**Ejemplo de sintaxis:**  
  
```xml  
<map-schema  
  
   source-schema="<source-schema>"  
  
   sql-server-schema="<target-schema>"/>  
```  
**Command**  
  
esquema de asignación  
  
Asignación de esquema de base de datos de origen al esquema de destino.  
  
**Script**  
  
`source-schema` Especifica el esquema de origen que se va a migrar.  
  
`sql-server-schema` Especifica el esquema de destino donde los deseamos que desea migrar.  
  
**Ejemplo de sintaxis:**  
  
```xml  
<map-schema  
  
   source-schema="<source-schema>"  
  
   sql-server-schema="<target-schema>"/>  
```  
  
## <a name="manageability-script-file-commands"></a>Comandos del archivo de Script de facilidad de uso  
Los comandos de facilidad de uso ayudan a sincronizar los objetos de base de datos de destino con la base de datos de origen.  
  
La salida de consola predeterminada para los comandos de migración es informe de salida 'Total' con ningún informe de error detallado: resumen sólo en el nodo de raíz del árbol de objeto de origen.  
  
**Command**  
  
destino sincronizar  
  
-   Los objetos de destino se sincroniza con la base de datos de destino.  
  
-   Si este comando se ejecuta en la base de datos de origen, se produce un error.  
  
-   Si no se realiza la conexión de base de datos de destino antes de ejecutar este comando o se produce un error en la conexión con el servidor de base de datos de destino durante la ejecución del comando, se genera un error y se cierra la aplicación de consola.  
  
**Script**  
  
-   `object-name:` Especifica los objetos de destino que se consideran para la sincronización con la base de datos de destino (puede tener nombres de objeto de indivdual o un nombre de objeto de grupo).  
  
-   `object-type:` Especifica el tipo del objeto especificado en el atributo de nombre de objeto (si se especifica la categoría de objeto de tipo de objeto será "categoría").  
  
-   `on-error:` Especifica si se debe especificar los errores de sincronización como advertencias o errores. Opciones disponibles en el error:  
  
    -   total de informes como advertencia  
  
    -   informes-each-como-advertencia  
  
    -   Error-script  
  
-   `report-errors-to:` Especifica la ubicación del informe de errores para la operación de sincronización (atributo opcional) si solo se proporciona la ruta de acceso de carpeta, a continuación, de archivos por nombre **TargetSynchronizationReport.XML** se crea.  
  
**Ejemplo de sintaxis:**  
  
```xml  
<synchronize-target  
  
   object-name="<object-name>"  
  
   on-error="<report-total-as-warning/  
  
               report-each-as-warning/  
  
               fail-script>"   (optional)  
  
   report-errors-to="<file-name/folder-name>"   (optional)  
  
/>  
```  
o Administrador de configuración de  
  
```xml  
<synchronize-target  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"/>  
```  
o Administrador de configuración de  
  
```xml  
<synchronize-target>  
  
   <metabase-object object-name="<object-name>"/>  
  
   <metabase-object object-name="<object-name>"/>  
  
   <metabase-object object-name="<object-name>"/>  
  
</synchronize-target>  
```  
**Command**  
  
actualización de base de datos  
  
-   Actualiza los objetos de origen de base de datos.  
  
-   Si este comando se ejecuta en la base de datos de destino, se genera un error.  
  
**Script**  
  
Requiere uno o varios nodos de la metabase como parámetro de línea de comandos.  
  
-   `object-name:` Especifica los objetos de origen que se consideran para actualizar desde la base de datos de origen (puede tener nombres de objeto de indivdual o un nombre de objeto de grupo).  
  
-   `object-type:` Especifica el tipo del objeto especificado en el atributo de nombre de objeto (si se especifica la categoría de objeto de tipo de objeto será "categoría").  
  
-   `on-error:` Especifica si se debe especificar la actualización de errores como advertencias o errores. Opciones disponibles en el error:  
  
    -   total de informes como advertencia  
  
    -   informes-each-como-advertencia  
  
    -   Error-script  
  
-   `report-errors-to:` Especifica la ubicación del informe de errores para la operación de actualización (atributo opcional) si solo se proporciona la ruta de acceso de carpeta, a continuación, de archivos por nombre **SourceDBRefreshReport.XML** se crea.  
  
**Ejemplo de sintaxis:**  
  
```xml  
<refresh-from-database  
  
   object-name="<object-name>"  
  
   on-error="<report-total-as-warning/  
  
               report-each-as-warning/  
  
               fail-script>"   (optional)  
  
   report-errors-to="<file-name/folder-name>"   (optional)  
  
/>  
```  
o Administrador de configuración de  
  
```xml  
<refresh-from-database  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"/>  
```  
o Administrador de configuración de  
  
```xml  
<refresh-from-database>  
  
   <metabase-object object-name="<object-name>"/>  
  
</refresh-from-database>  
```  
  
## <a name="script-generation-script-file-commands"></a>Comandos del archivo de Script de generación de script  
Los comandos de generación de Script realizan dos tareas: ayudan a guardar la salida en un archivo de script, en la consola y registre la salida de T-SQL en la consola o un archivo basado en el parámetro especificado.  
  
**Command**  
  
Guardar como secuencia de comandos  
  
Usado para guardar las secuencias de comandos de los objetos en un archivo que se ha mencionado cuando metabase = destino, ésta es una alternativa al comando de sincronización que se obtendrá las secuencias de comandos y ejecutar la misma base de datos de destino.  
  
**Script**  
  
Requiere uno o varios nodos de la metabase como parámetro de línea de comandos.  
  
-   `object-name:` Especifica los objetos cuyos scripts son se guarden. (Puede tener nombres de objeto individuales o un nombre de objeto de grupo)  
  
-   `object-type:` Especifica el tipo del objeto especificado en el atributo de nombre de objeto (si se especifica la categoría de objeto de tipo de objeto será "categoría").  
  
-   `metabase:` Especifica si es el origen o destino de la metabase.  
  
-   `destination:` Especifica la ruta de acceso o la carpeta donde la secuencia de comandos debe guardarse, si el nombre de archivo no se proporciona, a continuación, un nombre de archivo en el formato (valor del atributo object_name) .out  
  
-   `overwrite:` Si es true, a continuación, sobrescribe si existe el mismo nombre de archivo. Puede tener los valores (verdadero/falso).  
  
**Ejemplo de sintaxis:**  
  
```xml  
<save-as-script  
  
   metabase="<source/target>"  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"  
  
   destination="<file/folder>"  
  
   overwrite="<true/false>"   (optional)  
  
/>  
```  
o Administrador de configuración de  
  
```xml  
<save-as-script  
  
   metabase="<source/target>"  
  
   destination="<file/folder>"  
  
      <metabase-object object-name="<object-name>"  
  
         object-type="<object-category>"/>  
  
</save-as-script>  
```  
**Command**  
  
instrucción de sql Convert  
  
-   `context` Especifica el nombre del esquema.  
  
-   `destination` Especifica si la salida debe almacenarse en un archivo.  
  
    Si no se especifica este atributo, la instrucción de T-SQL convertida se muestra en la consola. (opcional) (atributo)  
  
-   `conversion-report-folder` Especifica la carpeta donde el informe de evaluación puede almacenarse. (opcional) (atributo)  
  
-   `conversion-report-overwrite` Especifica si se debe sobrescribir la carpeta de informes de evaluación si ya existe.  
  
    **Valor predeterminado:** false. (opcional) (atributo)  
  
-   `write-converted-sql-to` Especifica la ruta de acceso de carpeta donde se almacenará el T-SQL convertido de archivo (o). Cuando se especifica una ruta de acceso de carpeta junto con el `sql-files` atributo, cada archivo de código fuente tendrá un archivo de código T-SQL creado en la carpeta especificada de destino correspondiente. Cuando se especifica una ruta de acceso de carpeta junto con la `sql` atributo, el T-SQL convertido se escribe en un archivo denominado **Result.out** en la carpeta especificada.  
  
-   `sql` Especifica las instrucciones de sql de DB2 se convierta, una o varias instrucciones pueden estar separadas por un ";"  
  
-   `sql-files` Especifica la ruta de acceso de los archivos de sql que se tiene que convertir a código de T-SQL.  
  
-   `write-summary-report-to` Especifica la ruta de acceso donde se generará el informe. Si solo se menciona la ruta de acceso de carpeta, archivo, a continuación, por nombre **ConvertSQLReport.XML** se crea. (opcional) (atributo)  
  
    Informe de creación tiene 2 más subcategorías, especialmente..,:  
  
    -   informe de errores (= "true/false", no tiene valor predeterminado como "false" (atributos opcionales)).  
  
    -   verbose (= "true/false", no tiene valor predeterminado como "false" (atributos opcionales)).  
  
**Script**  
  
Requiere uno o varios nodos de la metabase como parámetro de línea de comandos.  
  
**Ejemplo de sintaxis:**  
  
```  
<convert-sql-statement  
  
   context="<schema-name>"  
  
   conversion-report-folder="<folder-name>"  
  
   conversion-report-overwrite="<true/false>"  
  
   write-summary-report-to="<file-name/folder-name>"   (optional)  
  
   verbose="<true/false>"   (optional)  
  
   report-errors="<true/false>"   (optional)  
  
   destination="<stdout/file>"   (optional)  
  
   file-name="<file-name>"  
  
   sql="SELECT 1 FROM DUAL;">  
  
   <output-window suppress-messages="<true/false>" />  
  
</convert-sql-statement>  
```  
o Administrador de configuración de  
  
```  
<convert-sql-statement  
  
   context="<schema-name>"  
  
   conversion-report-folder="<folder-name>"  
  
   conversion-report-overwrite="<true/false>"  
  
   write-summary-report-to="<file-name/folder-name>" (optional)  
  
   verbose="<true/false>" (optional)  
  
   report-errors="<true/false>"  
  
   destination="<stdout/file>"   (optional)  
  
   write-converted-sql-to="<file-name/folder-name>"  
  
   sql-files="<folder-name>\*.sql" />  
```  
o Administrador de configuración de  
  
```  
<convert-sql-statement  
  
   context="<schema-name>"  
  
   conversion-report-folder="<folder-name>"  
  
   conversion-report-overwrite="<true/false>"  
  
   sql-files="<folder-name>\*.sql" />  
```  
  
## <a name="next-step"></a>Paso siguiente  
Para obtener información sobre las opciones de línea de comandos, consulte [opciones de línea de comandos en la consola de SSMA &#40;DB2ToSQL&#41; ](../../ssma/db2/command-line-options-in-ssma-console-db2tosql.md) .  
  
Para obtener información sobre los archivos de secuencia de comandos de consola de ejemplo, vea [trabajar con los archivos de comandos de consola de ejemplo &#40;DB2ToSQL&#41;](../../ssma/db2/working-with-the-sample-console-script-files-db2tosql.md)  
  
El paso siguiente depende de los requisitos del proyecto:  
  
-   Para especificar una contraseña o la exportación / importación de contraseñas, vea [administrar contraseñas &#40;DB2ToSQL&#41;](../../ssma/db2/managing-passwords-db2tosql.md).  
  
-   Para generar informes, consulte [generar informes &#40;DB2ToSQL&#41;](../../ssma/db2/generating-reports-db2tosql.md).  
  
-   Para solucionar problemas en la consola, consulte [solución de problemas &#40;DB2ToSQL&#41;](../../ssma/db2/troubleshooting-db2tosql.md).  
  
