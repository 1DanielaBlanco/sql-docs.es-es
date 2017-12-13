---
title: "Columnas de datos de eventos de estado del servidor de detección | Documentos de Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: Discover Server State event category
ms.assetid: fbacb187-a4d1-4aa4-be3b-3ddd175f9e19
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7111aaee1121c12a00d372138bc299d9e80cc695
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2017
---
# <a name="discover-server-state-events-data-columns"></a>Columnas de datos de eventos de detección de estado del servidor
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]La categoría de eventos de detección de estado de servidor tiene las siguientes clases de evento:  
  
|**Identificador del evento**|**Nombre del evento**|**Descripción del evento**|  
|------------------|--------------------|---------------------------|  
|33|Server State Discover Begin|Inicio de la detección del estado del servidor.|  
|34|Server State Discover Data|Contenido de la respuesta de detección del estado del servidor.|  
|35|Server State Discover End|Fin de la detección del estado del servidor.|  
  
 En las siguientes tablas se muestran las columnas de datos de cada una de estas clases de eventos.  
  
## <a name="server-state-discover-begin-classdata-columns"></a>Columnas de datos de la clase Server State Discover Begin  
  
|||||  
|-|-|-|-|  
|**Nombre de la columna**|**Identificador de la columna**|**Tipo de columna**|**Descripción de la columna**|  
|EventClass|0|1|EventClass se usa para clasificar los eventos.|  
|EventSubclass|1|1|EventSubclass proporciona información adicional sobre cada clase de eventos.<br /><br /> 1: **DISCOVER_CONNECTIONS**<br /><br /> 2: **DISCOVER_SESSIONS**<br /><br /> 3: **DISCOVER_TRANSACTIONS**<br /><br /> 6: **DISCOVER_DB_CONNECTIONS**<br /><br /> 7: **DISCOVER_JOBS**<br /><br /> 8: **DISCOVER_LOCKS**<br /><br /> 12: **DISCOVER_PERFORMANCE_COUNTERS**<br /><br /> 13: **DISCOVER_MEMORYUSAGE**<br /><br /> 14: **DISCOVER_JOB_PROGRESS**<br /><br /> 15: **DISCOVER_MEMORYGRANT**|  
|CurrentTime|2|5|Contiene la hora actual del evento de detección de estado del servidor, si está disponible. Para filtrar, los formatos esperados son "AAAA-MM-DD" y "AAAA-MM-DD HH:MM:SS".|  
|StartTime|3|5|Contiene la hora a la que se inició el evento, si está disponible. Para filtrar, los formatos esperados son "AAAA-MM-DD" y "AAAA-MM-DD HH:MM:SS".|  
|ConnectionID|25|1|Contiene el identificador único de conexión asociado al evento de detección de estado del servidor.|  
|NTUserName|32|8|Contiene la cuenta de usuario de Windows asociada al evento de detección de estado del servidor.|  
|NTDomainName|33|8|Contiene la cuenta de usuario de dominio de Windows asociada al evento de detección de estado del servidor.|  
|ClientProcessID|36|1|Contiene el identificador de proceso de la aplicación cliente que ha creado la conexión con el servidor.|  
|ApplicationName|37|8|Contiene el nombre de la aplicación cliente que ha creado la conexión con el servidor. Esta columna se rellena con los valores que pasa la aplicación, en lugar de con el nombre que se muestra para el programa.|  
|SessionID|39|8|Contiene el identificador de sesión asociado al evento de detección de estado del servidor.|  
|NTCanonicalUserName|40|8|Contiene el nombre de usuario de Windows asociado al evento de detección de estado del servidor. El nombre de usuario está en formato canónico. Por ejemplo, engineering.microsoft.com/software/user.|  
|SPID|41|1|Contiene el identificador de proceso de servidor (SPID) que identifica de forma única la sesión de usuario asociada al evento de detección de estado del servidor. El SPID se corresponde directamente con el GUID de sesión utilizado por XMLA.|  
|TextData|42|9|Contiene los datos de texto asociados al evento.|  
|ServerName|43|8|Contiene el nombre de la instancia de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en la que se ha producido el evento de detección de estado del servidor.|  
|RequestProperties|45|9|Contiene las propiedades de la solicitud de XMLA actual.|  
  
## <a name="server-state-discover-data-classdata-columns"></a>Columnas de datos de la clase Server State Discover Data  
  
|||||  
|-|-|-|-|  
|**Nombre de la columna**|**Identificador de la columna**|**Tipo de columna**|**Descripción de la columna**|  
|EventClass|0|1|EventClass se usa para clasificar los eventos.|  
|EventSubclass|1|1|EventSubclass proporciona información adicional sobre cada clase de eventos.<br /><br /> 1: **DISCOVER_CONNECTIONS**<br /><br /> 2: **DISCOVER_SESSIONS**<br /><br /> 3: **DISCOVER_TRANSACTIONS**<br /><br /> 6: **DISCOVER_DB_CONNECTIONS**<br /><br /> 7: **DISCOVER_JOBS**<br /><br /> 8: **DISCOVER_LOCKS**<br /><br /> 12: **DISCOVER_PERFORMANCE_COUNTERS**<br /><br /> 13: **DISCOVER_MEMORYUSAGE**<br /><br /> 14: **DISCOVER_JOB_PROGRESS**<br /><br /> 15: **DISCOVER_MEMORYGRANT**|  
|CurrentTime|2|5|Contiene la hora actual del evento de detección de estado del servidor, si está disponible. Para filtrar, los formatos esperados son "AAAA-MM-DD" y "AAAA-MM-DD HH:MM:SS".|  
|StartTime|3|5|Contiene la hora a la que se inició el evento, si está disponible. Para filtrar, los formatos esperados son "AAAA-MM-DD" y "AAAA-MM-DD HH:MM:SS".|  
|ConnectionID|25|1|Contiene el identificador único de conexión asociado al evento de detección de estado del servidor.|  
|SessionID|39|8|Contiene el identificador de sesión asociado al evento de detección de estado del servidor.|  
|SPID|41|1|Contiene el identificador de proceso de servidor (SPID) que identifica de forma única la sesión de usuario asociada al evento de detección de estado del servidor. El SPID se corresponde directamente con el GUID de sesión utilizado por XMLA.|  
|TextData|42|9|Contiene los datos de texto asociados a la respuesta del servidor con respecto a la solicitud de detección.|  
|ServerName|43|8|Contiene el nombre de la instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en la que se ha producido el evento de detección de estado del servidor.|  
  
## <a name="server-state-discover-end-classdata-columns"></a>Columnas de datos de la clase Server State Discover End  
  
|||||  
|-|-|-|-|  
|**Nombre de la columna**|**Identificador de la columna**|**Tipo de columna**|**Descripción de la columna**|  
|EventClass|0|1|EventClass se usa para clasificar los eventos.|  
|EventSubclass|1|1|EventSubclass proporciona información adicional sobre cada clase de eventos.<br /><br /> 1: **DISCOVER_CONNECTIONS**<br /><br /> 2: **DISCOVER_SESSIONS**<br /><br /> 3: **DISCOVER_TRANSACTIONS**<br /><br /> 6: **DISCOVER_DB_CONNECTIONS**<br /><br /> 7: **DISCOVER_JOBS**<br /><br /> 8: **DISCOVER_LOCKS**<br /><br /> 12: **DISCOVER_PERFORMANCE_COUNTERS**<br /><br /> 13: **DISCOVER_MEMORYUSAGE**<br /><br /> 14: **DISCOVER_JOB_PROGRESS**<br /><br /> 15: **DISCOVER_MEMORYGRANT**|  
|CurrentTime|2|5|Contiene la hora actual del evento de detección de estado del servidor, si está disponible. Para filtrar, los formatos esperados son "AAAA-MM-DD" y "AAAA-MM-DD HH:MM:SS".|  
|StartTime|3|5|Contiene la hora a la que se inició el evento, si está disponible. Para filtrar, los formatos esperados son "AAAA-MM-DD" y "AAAA-MM-DD HH:MM:SS".|  
|EndTime|4|5|Contiene la hora a la que finalizó el evento. Esta columna no se llena para las clases de eventos de inicio, como SQL:BatchStarting o SP:Starting. Para filtrar, los formatos esperados son "AAAA-MM-DD" y "AAAA-MM-DD HH:MM:SS".|  
|Duración|5|2|Contiene el tiempo (en milisegundos) que duró el evento.|  
|CPUTime|6|2|Contiene el intervalo de tiempo de CPU (en milisegundos) utilizado por el evento de detección de estado del servidor.|  
|ConnectionID|25|1|Contiene el identificador único de conexión asociado al evento de detección de estado del servidor.|  
|NTUserName|32|8|Contiene la cuenta de usuario de Windows asociada al evento de detección de estado del servidor.|  
|NTDomainName|33|8|Contiene la cuenta de usuario de dominio de Windows asociada al evento de detección de estado del servidor.|  
|ClientProcessID|36|1|Contiene el identificador de proceso de la aplicación cliente que inició la solicitud de XMLA.|  
|ApplicationName|37|8|Contiene el nombre de la aplicación cliente que ha creado la conexión con el servidor. Esta columna se rellena con los valores que pasa la aplicación, en lugar de con el nombre que se muestra para el programa.|  
|SessionID|39|8|Contiene la cuenta de usuario de dominio de Windows asociada al evento de detección de estado del servidor.|  
|NTCanonicalUserName|40|8|Contiene el nombre de usuario de Windows asociado al evento de detección de estado del servidor. El nombre de usuario está en formato canónico. Por ejemplo, engineering.microsoft.com/software/user.|  
|SPID|41|1|Contiene el identificador de proceso de servidor (SPID) que identifica de forma única la sesión de usuario asociada al evento de detección de estado del servidor. El SPID se corresponde directamente con el GUID de sesión utilizado por XMLA.|  
|TextData|42|9|Contiene los datos de texto asociados a la respuesta del servidor con respecto a la solicitud de detección.|  
|ServerName|43|8|Contiene el nombre de la instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en la que se ha producido el evento de detección de estado del servidor.|  
  
## <a name="see-also"></a>Vea también  
 [Discover Server State Event Category](../../analysis-services/trace-events/discover-server-state-event-category.md)  
  
  
