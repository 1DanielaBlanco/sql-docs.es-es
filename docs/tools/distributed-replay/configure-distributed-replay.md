---
title: Configurar Distributed Replay | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aee11dde-daad-439b-b594-9f4aeac94335
caps.latest.revision: 43
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7d48bd22d10dfd3b33a61382ad3581123524924f
ms.contentlocale: es-es
ms.lasthandoff: 08/02/2017

---
# <a name="configure-distributed-replay"></a>Configurar Distributed Replay
  Los detalles de configuración de Distributed Replay de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se especifican en archivos XML en Distributed Replay Controller, en los clientes y donde se encuentra instalada la herramienta de administración. Entre los archivos figuran los siguientes:  
  
-   [Archivo de configuración del controlador](#DReplayController)  
  
-   [Archivo de configuración del cliente](#DReplayClient)  
  
-   [Archivo de configuración de preproceso](#PreprocessConfig)  
  
-   [Archivo de configuración de reproducción](#ReplayConfig)  
  
##  <a name="DReplayController"></a> Archivo de configuración del controlador: DReplayController.config  
 Cuando el servicio de Distributed Replay Controller de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se inicia, carga el nivel de registro del archivo de configuración del controlador, `DReplayController.config`. Este archivo se encuentra en la carpeta donde instaló el servicio de Distributed Replay Controller:  
  
 **\<ruta de instalación de controladora > \DReplayController.config**  
  
 El nivel de registro especificado por el archivo de configuración del controlador incluye lo siguiente:  
  
|Configuración|Elemento XML|Descripción|Valores permitidos|Necesario|  
|-------------|-----------------|-----------------|--------------------|--------------|  
|Nivel de registro|`<LoggingLevel>`|Especifica el nivel de registro para el servicio del controlador.|`INFORMATION` &#124; `WARNING` &#124; `CRITICAL`|No. El valor es `CRITICAL`de forma predeterminada.|  
  
### <a name="example"></a>Ejemplo  
 En este ejemplo se muestra un archivo de configuración del controlador modificado para suprimir las entradas de registro `INFORMATION` y `WARNING` .  
  
```  
<?xml version='1.0'?>  
<Options>  
<LoggingLevel>CRITICAL</LoggingLevel>  
</Options>  
```  
  
##  <a name="DReplayClient"></a> Archivo de configuración del cliente: DReplayClient.config  
 Cuando el servicio de Distributed Replay Client de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se inicia, carga los valores de configuración del archivo de configuración del cliente, `DReplayClient.config`. Este archivo se encuentra en cada cliente, en la carpeta donde instaló el servicio de Distributed Replay Client:  
  
 **\<ruta de acceso de instalación de cliente > \DReplayClient.config**  
  
 La configuración especificada por el archivo de configuración del cliente incluye lo siguiente:  
  
|Configuración|Elemento XML|Descripción|Valores permitidos|Necesario|  
|-------------|-----------------|-----------------|--------------------|--------------|  
|Controlador|`<Controller>`|Especifica el nombre del equipo que se va a controlar. El cliente intentará registrarse con el entorno de Distributed Replay poniéndose en contacto con el controlador.|Puede utilizar "`localhost`" o "`.`" para hacer referencia al equipo local.|No. De forma predeterminada, el cliente intenta registrarse con la instancia del controlador que se está ejecutando localmente ("`.`"), si existe.|  
|Directorio de trabajo del cliente|`<WorkingDirectory>`|Es la ruta de acceso local del cliente donde se guardan los archivos de distribución.<br /><br /> Los archivos de este directorio se sobrescriben en la siguiente reproducción.|Un nombre de directorio completo, empezando con la letra de unidad.|No. Si no se especifica ningún valor, los archivos de distribución se guardarán en la misma ubicación que el archivo de configuración del cliente predeterminado. Si se especifica un valor y esa carpeta no existe en el cliente, el servicio del cliente no se iniciará.|  
|Directorio de resultados del cliente|`<ResultDirectory>`|Es la ruta de acceso local en el cliente donde se guarda el archivo de seguimiento del resultado de la actividad de reproducción (para el cliente).<br /><br /> Los archivos de este directorio se sobrescriben en la siguiente reproducción.|Un nombre de directorio completo, empezando con la letra de unidad.|No. Si no se especifica ningún valor, el archivo de seguimiento del resultado se guardará en la misma ubicación que el archivo de configuración del cliente predeterminado. Si se especifica un valor y esa carpeta no existe en el cliente, el servicio del cliente no se iniciará.|  
|Nivel de registro|`<LoggingLevel>`|Es el nivel de registro para el servicio del cliente.|`INFORMATION` &#124; `WARNING` &#124; `CRITICAL`|No. El valor es `CRITICAL`de forma predeterminada.|  
  
### <a name="example"></a>Ejemplo  
 Este ejemplo muestra un archivo de configuración del cliente modificado para especificar que el servicio del controlador se está ejecutando en un equipo diferente, denominado `Controller1`. Los elementos `WorkingDirectory` y `ResultDirectory` se han configurado de modo que utilicen las carpetas `c:\ClientWorkingDir` y `c:\ResultTraceDir`, respectivamente. El nivel de registro se ha cambiado de su valor predeterminado para suprimir las entradas de registro `INFORMATION` y `WARNING` .  
  
```  
<?xml version='1.0'?>  
<Options>  
    <Controller>Controller1</Controller>  
    <WorkingDirectory>c:\ClientWorkingDir</WorkingDirectory>  
    <ResultDirectory>c:\ResultTraceDir</ResultDirectory>  
    <LoggingLevel>CRITICAL</LoggingLevel>  
</Options>  
```  
  
##  <a name="PreprocessConfig"></a> Archivo de configuración de preproceso: DReplay.exe.preprocess.config  
 Al utilizar la herramienta de administración para iniciar la fase de preproceso, la herramienta de administración carga los valores de configuración de preproceso desde el archivo de configuración de preproceso, `DReplay.exe.preprocess.config`.  
  
 Use el archivo de configuración predeterminado o el parámetro **-c** de la herramienta de administración para especificar la ubicación de un archivo de configuración de preproceso modificado. Para obtener más información sobre el uso de la opción de preprocesamiento de la herramienta de administración, consulte [opción de preprocesamiento &#40; herramienta de administración de Distributed Replay &#41;](../../tools/distributed-replay/preprocess-option-distributed-replay-administration-tool.md).  
  
 El archivo de configuración de preproceso predeterminado se encuentra en la carpeta donde instaló la herramienta de administración:  
  
 **\<ruta de instalación de herramienta de administración > \DReplayAdmin\DReplay.exe.preprocess.config**  
  
 Los valores de configuración de preproceso se especifican en elementos XML secundarios del elemento `<PreprocessModifiers>` en el archivo de configuración de preproceso. Entre estas opciones de configuración, se incluyen las siguientes:  
  
|Configuración|Elemento XML|Descripción|Valores permitidos|Necesario|  
|-------------|-----------------|-----------------|--------------------|--------------|  
|Incluir las actividades de sesión de sistema|`<IncSystemSession>`|Indica si las actividades de sesión de sistema en la captura se incluirán durante la reproducción.|`Yes` &#124; `No`|No. El valor es `No`de forma predeterminada.|  
|Tiempo de inactividad máximo|`<MaxIdleTime>`|Limita el tiempo de inactividad a un número absoluto (en segundos).|Un valor entero >= -1.<br /><br /> `-1` indica que no ha habido ningún cambio respecto del valor original en el archivo de seguimiento original.<br /><br /> `0` indica que existe alguna actividad en algún momento.|No. El valor es `-1`de forma predeterminada.|  
  
### <a name="example"></a>Ejemplo  
 El archivo de configuración de preproceso predeterminado:  
  
```  
<?xml version='1.0'?>  
<Options>  
    <PreprocessModifiers>  
        <IncSystemSession>No</IncSystemSession>  
        <MaxIdleTime>-1</MaxIdleTime>  
    </PreprocessModifiers>  
</Options>  
```  
  
##  <a name="ReplayConfig"></a> Archivo de configuración de reproducción: DReplay.exe.replay.config  
 Al utilizar la herramienta de administración para iniciar la fase de reproducción de eventos, la herramienta de administración carga los valores de configuración de reproducción desde el archivo de configuración de reproducción, `DReplay.exe.replay.config`.  
  
 Use el archivo de configuración predeterminado o el parámetro **-c** de la herramienta de administración para especificar la ubicación de un archivo de configuración de reproducción modificado. Para obtener más información sobre el uso de la opción de reproducción de la herramienta de administración, consulte [opción Replay &#40; herramienta de Distributed Replay administración &#41;](../../tools/distributed-replay/replay-option-distributed-replay-administration-tool.md).  
  
 El archivo de configuración de reproducción predeterminado se encuentra en la carpeta donde instaló la herramienta de administración:  
  
 **\<ruta de instalación de herramienta de administración > \DReplayAdmin\DReplay.exe.Replay.config**  
  
 Los valores de configuración de reproducción se especifican en elementos XML secundarios de los elementos `<ReplayOptions>` y `<OutputOptions>` del archivo de configuración de reproducción.  
  
### <a name="replayoptions-element"></a>\<ReplayOptions > elemento  
 Los valores especificados por el archivo de configuración de reproducción en el elemento `<ReplayOptions>` incluyen lo siguiente:  
  
|Configuración|Elemento XML|Descripción|Valores permitidos|Necesario|  
|-------------|-----------------|-----------------|--------------------|--------------|  
|Instancia de destino de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (el servidor de prueba)|`<Server>`|Especifica el nombre del servidor y la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para la conexión.|*server_name*[\\*instance_name*]<br /><br /> No puede usar "`localhost`" o "`.`" para representar el host local.|No, si el nombre del servidor ya se especifica con el parámetro **-s***target server* con la opción **replay** de la herramienta de administración.|  
|Modo de secuenciación|`<SequencingMode>`|Especifica el modo que se usa para la programación de eventos.|`synchronization` &#124; `stress`|No. El valor es `stress`de forma predeterminada.|  
|Granularidad de escala de esfuerzo|`<StressScaleGranularity>`|Especifica si todas las conexiones en el Identificador de perfil de servicio (SPID) deben escalarse juntas (SPID) o independientemente (Conexión) en el modo de esfuerzo.|SPID &#124; Conexión|Sí. El valor es `SPID`de forma predeterminada.|  
|Escala del tiempo de conexión|`<ConnectTimeScale>`|Se usa para escalar el tiempo de conexión en el modo de esfuerzo.|Un entero entre `1` y `100`.|No. El valor es `100`de forma predeterminada.|  
|Escala del tiempo de reflexión|`<ThinkTimeScale>`|Se usa para escalar el tiempo de reflexión en el modo de esfuerzo.|Un entero entre `0` y `100`.|No. El valor es `100`de forma predeterminada.|  
|Use agrupar conexiones|`<UseConnectionPooling>`|Especifica si la agrupación de conexiones se habilitará en cada Distributed Replay client.|Sí &#124; No|Sí. El valor es `Yes`de forma predeterminada.|  
|Intervalo del monitor de mantenimiento|`<HealthmonInterval>`|Indica con qué periodicidad se debe ejecutar el monitor de mantenimiento (en segundos).<br /><br /> Este valor solo se utiliza en modo de sincronización.|Entero >= 1<br /><br /> (`-1` para deshabilitar)|No. El valor es `60`de forma predeterminada.|  
|Tiempo de espera de la consulta|`<QueryTimeout>`|Especifica el valor del tiempo de espera máximo de una consulta, en segundos. Este valor solo es efectivo hasta que se haya devuelto la primera fila.|Entero >= 1<br /><br /> (`-1` para deshabilitar)|No. El valor es `3600`de forma predeterminada.|  
|Subprocesos por cliente|`<ThreadsPerClient>`|Especifica el número de subprocesos de reproducción para cada cliente de reproducción.|Un entero entre `1` y `512`.|No. Si no se especifica, Distributed Replay usará el valor `255`.|  
  
### <a name="outputoptions-element"></a>\<OutputOptions > elemento  
 Los valores especificados por el archivo de configuración de reproducción en el elemento `<OutputOptions>` incluyen lo siguiente:  
  
|Configuración|Elemento XML|Descripción|Valores permitidos|Necesario|  
|-------------|-----------------|-----------------|--------------------|--------------|  
|Registrar el recuento de filas|`<RecordRowCount>`|Indica si se debe registrar el recuento de filas para cada conjunto de resultados.|`Yes` &#124; `No`|No. El valor es `Yes`de forma predeterminada.|  
|Registrar el conjunto de resultados|`<RecordResultSet>`|Indica si se debe registrar el contenido de todos los conjuntos de resultados.|`Yes` &#124; `No`|No. El valor es `No`de forma predeterminada.|  
  
### <a name="example"></a>Ejemplo  
 El archivo de configuración de reproducción predeterminado:  
  
```  
<?xml version='1.0'?>  
<Options>  
    <ReplayOptions>  
        <Server></Server>  
        <SequencingMode>stress</SequencingMode>  
        <ConnectTimeScale></ConnectTimeScale>  
        <ThinkTimeScale></ThinkTimeScale>  
        <HealthmonInterval>60</HealthmonInterval>  
        <QueryTimeout>3600</QueryTimeout>  
        <ThreadsPerClient></ThreadsPerClient>  
    </ReplayOptions>  
    <OutputOptions>  
        <ResultTrace>  
            <RecordRowCount>Yes</RecordRowCount>  
            <RecordResultSet>No</RecordResultSet>  
        </ResultTrace>  
    </OutputOptions>  
</Options>  
```  
  
## <a name="see-also"></a>Vea también  
 [Opciones de línea de comandos de la herramienta de administración &#40;utilidad Distributed Replay&#41;](../../tools/distributed-replay/administration-tool-command-line-options-distributed-replay-utility.md)   
 [Reproducción distribuida de SQL Server](../../tools/distributed-replay/sql-server-distributed-replay.md)   
 [Foro de SQL Server Distributed Replay](http://social.technet.microsoft.com/Forums/sl/sqldru/)   
 [Usar Distributed Replay para la prueba de carga de SQL Server, parte 2](http://blogs.msdn.com/b/mspfe/archive/2012/11/14/using-distributed-replay-to-load-test-your-sql-server-part-2.aspx)   
 [Usar Distributed Replay para la prueba de carga de SQL Server, parte 1](http://blogs.msdn.com/b/mspfe/archive/2012/11/08/using-distributed-replay-to-load-test-your-sql-server-part-1.aspx)  
  
  

