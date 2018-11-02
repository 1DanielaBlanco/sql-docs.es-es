---
title: Agente de lectura de cola de replicación | Microsoft Docs
ms.custom: ''
ms.date: 10/29/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], Queue Reader Agent
- command prompt [SQL Server replication]
- Queue Reader Agent, parameter reference
- Queue Reader Agent, executables
ms.assetid: 8e227793-11f6-47c6-99dc-ffc282f5d4bf
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f63676830d79bc8ec9c3ffd462e9d836364df159
ms.sourcegitcommit: 3e1efbe460723f9ca0a8f1d5a0e4a66f031875aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2018
ms.locfileid: "50236972"
---
# <a name="replication-queue-reader-agent"></a>Agente de lectura de cola de replicación
  El Agente de lectura de cola de replicación es una aplicación ejecutable que lee los mensajes almacenados en una cola de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] o [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Message Queue y, a continuación, aplica esos mensajes al Publicador. El Agente de lectura de cola se utiliza con la instantánea y las publicaciones transaccionales que permiten la actualización en cola.  
  
> [!NOTE]  
>  Los parámetros se pueden especificar en cualquier orden. Cuando no se especifican parámetros opcionales, se utilizan valores predefinidos basados en el perfil de agente predeterminado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      qrdrsvc [-?]  
[-Continuous]  
[-DefinitionFiledefinition_file]  
[-Distributorserver_name[\instance_name]]  
[-DistributionDBdistribution_database]  
[-DistributorLogindistributor_login]  
[-DistributorPassworddistributor_password]  
[-DistributorSecurityMode [0|1]]  
[-EncryptionLevel [0|1|2]]  
[-HistoryVerboseLevel [0|1|2|3]]  
[-LoginTimeOutlogin_time_out_seconds]  
[-Outputoutput_path_and_file_name]  
[-OutputVerboseLevel [0|1|2]]  
[-PollingIntervalpolling_interval]  
[-PublisherFailoverPartnerserver_name[\instance_name] ]  
[-ProfileNameagent_profile_name]  
[-QueryTimeOutquery_time_out_seconds]  
[-ResolverState [1|2|3]]  
```  
  
## <a name="arguments"></a>Argumentos  
 **-?**  
 Muestra información de uso.  
  
 **-Continuous**  
 Especifica si el agente intenta procesar continuamente las transacciones en cola. Si se especifica, el agente continúa la ejecución incluso si no hay transacciones en cola pendientes de cualquiera de los suscriptores.  
  
 **-DefinitionFile** *def_path_and_file_name*  
 Es la ruta de acceso del archivo de definición de agente. Un archivo de definición de agente contiene los argumentos de línea de comandos para el agente. El contenido del archivo se analiza como un archivo ejecutable. Utilice las comillas tipográficas (") para especificar valores de argumento que contienen caracteres arbitrarios.  
  
 **-Distributor** *nombre_de_servidor*[**\\***nombre_de_instancia*]  
 Es el nombre del distribuidor. Especifique *server_name* para la instancia predeterminada de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en ese servidor. Especifique *server_name*\\*instance_name* para una instancia con nombre de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en ese servidor. Si no se especifica, el nombre tiene como valor predeterminado el nombre de la instancia predeterminada de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en el equipo local.  
  
 **-DistributionDB** *distribution_database*  
 Es la base de datos de distribución.  
  
 **-DistributorLogin** *distributor_login*  
 Es el nombre de inicio de sesión del distribuidor.  
  
 **-DistributorPassword** *distributor_password*  
 Es la contraseña del distribuidor.  
  
 **-DistributorSecurityMode** [ **0**| **1**]  
 Especifica el modo de seguridad del distribuidor. Un valor de **0** hace referencia a la autenticación de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (valor predeterminado) y un valor de **1** hace referencia al modo de autenticación de Windows.  
  
 **-EncryptionLevel** [ **0** | **1** | **2** ]  
 Es el nivel de cifrado de Capa de sockets seguros (SSL) utilizado por el Agente de lectura de cola cuando realiza conexiones.  
  
|Valor de EncryptionLevel|Descripción|  
|---------------------------|-----------------|  
|**0**|Especifica que no se utiliza SSL.|  
|**1**|Especifica que se utiliza SSL, pero el agente no comprueba que un emisor confiable haya firmado el certificado del servidor SSL.|  
|**2**|Especifica que se usa SSL y que se ha comprobado el certificado.|  

 > [!NOTE]  
 >  Un certificado SSL válido se define con un nombre de dominio completo de SQL Server. Para el agente pueda conectarse correctamente al establecer EncryptionLevel - 2, crear un alias en el servidor SQL local. El parámetro 'Nombre de Alias' debe ser el nombre del servidor y el parámetro 'Server' debe establecerse en el nombre completo de SQL Server.
  
 Para obtener más información, vea [Información general sobre seguridad &#40;replicación&#41;](../security/security-overview-replication.md).  
  
 **-HistoryVerboseLevel** [ **0**| **1**| **2**| **3**]  
 Especifica la cantidad de historial registrado durante una operación del lector de cola. Puede minimizar el efecto sobre el rendimiento del registro del historial seleccionando **1**.  
  
|Valor HistoryVerboseLevel|Descripción|  
|-------------------------------|-----------------|  
|**0**|Ningún registro del historial (no se recomienda).|  
|**1**|Predeterminado: Siempre actualiza un mensaje del historial anterior del mismo estado (inicio, progreso, éxito, etc.). Si no existe ningún registro anterior con el mismo estado, inserta un nuevo registro.|  
|**2**|Inserte nuevos registros del historial, incluso mensajes inactivos o mensajes del trabajo de ejecución prolongada.|  
|**3**|Inserte nuevos registros de historial que incluyen detalles adicionales que pueden ser útiles para solucionar problemas.|  
  
 **-LoginTimeOut** *login_time_out_seconds*  
 Es el número de segundos antes de que el inicio de sesión exceda el tiempo de espera. El valor predeterminado es 15 segundos.  
  
 **-Output** *output_path_and_file_name*  
 Es la ruta de acceso del archivo de salida del agente. Si no se proporciona un nombre de archivo, el resultado se envía a la consola. Si el nombre de archivo especificado existe, el resultado se anexa al archivo.  
  
 **-OutputVerboseLevel** [ **0**| **1**| **2**]  
 Especifica si el resultado debería ser detallado. Si el nivel detallado es **0**, solo se imprimen los mensajes de error. Si el nivel detallado es **1**, se imprimen todos los mensajes del informe de progreso. Si el nivel detallado es **2** (valor predeterminado), se imprimen todos los mensajes de error y mensajes del informe de progreso, lo que es útil para la depuración.  
  
 **-PollingInterval** *polling_interval*  
 Solo es pertinente para actualizar las suscripciones que utilizan colas basadas en [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Especifica la frecuencia, en segundos, con la que se sondea la cola [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] las transacciones en cola pendientes. El valor puede estar comprendido entre 0 y 240 segundos. El valor predeterminado es 5 segundos.  
  
 **-PublisherFailoverPartner** *nombre_de_servidor*[**\\***nombre_de_instancia*]  
 Especifica la instancia del asociado de conmutación por error de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que participa en una sesión de creación de reflejo de la base de datos con la base de datos de publicación. Para obtener más información, vea [Database Mirroring and Replication &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).  
  
 **-ProfileName** *agent_profile_name*  
 Es el nombre de un perfil de agente utilizado para proporcionar un conjunto de valores predeterminados al agente. Para obtener información, vea [Replication Agent Profiles](replication-agent-profiles.md) (Perfiles del Agente de replicación).  
  
 **-QueryTimeOut** *query_time_out_seconds*  
 Es el número de segundos antes de que la consulta exceda el tiempo de espera. El valor predeterminado es 1800 segundos.  
  
 **-ResolverState** [ **1**| **2**| **3**]  
 Especifica cómo se resuelven los conflictos de actualización en cola. Un valor de **1** indica que el Publicador gana el conflicto, y la transacción en cola actual que está en conflicto se revertirá en el Publicador y el Suscriptor que originó la actualización; el procesamiento de las transacciones en cola posteriores continuará. Un valor de **2** indica que el Suscriptor gana el conflicto, y la transacción en cola invalidará los valores en el Publicador. Un valor de **3** indica que cualquier conflicto provocará la reinicialización del Suscriptor; el Publicador gana el conflicto, se finalizará el proceso de las transacciones en cola subsiguientes y se reinicializará la suscripción. La configuración predeterminada es **1** para las publicaciones transaccionales y **3** para las publicaciones de instantáneas.  
  
## <a name="remarks"></a>Comentarios  
 Para iniciar el Agente de lectura de cola, ejecute **qrdrsvc.exe** en el símbolo del sistema. Para obtener información, vea [Aplicaciones ejecutables del Agente de replicación](../concepts/replication-agent-executables-concepts.md).  
  
## <a name="see-also"></a>Vea también  
 [Administración del Agente de replicación](replication-agent-administration.md)  
  
  
