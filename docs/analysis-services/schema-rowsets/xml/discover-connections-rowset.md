---
title: Conjunto de filas DISCOVER_CONNECTIONS | Documentos de Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: de0346d7412f55e597db4b7b44cd533114a297a5
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="discoverconnections-rowset"></a>DISCOVER_CONNECTIONS, conjunto de filas
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Proporciona información sobre el uso de los recursos y la actividad en las conexiones abiertas actualmente en el servidor.  
  
 **Se aplica a:** modelos tabulares, modelos multidimensionales  
  
## <a name="rowset-columns"></a>Columnas del conjunto de filas  
 El conjunto de filas **DISCOVER_CONNECTIONS** contiene las siguientes columnas.  
  
|Nombre de columna|Indicador de tipo|Restricciones|Description|  
|-----------------|--------------------|------------------|-----------------|  
|**CONNECTION_ID**|**DBTYPE_I4**|Sí|Número único que identifica la conexión.|  
|**CONNECTION_USER_NAME**|**DBTYPE_WSTR**|Sí|Nombre de usuario de conexión.|  
|**CONNECTION_IMPERSONATED_USER_NAME**|**DBTYPE_WSTR**|Sí|Reservado para uso futuro. Analysis Services devuelve siempre NULL para el valor de CONNECTION_IMPERSONATED_USER_NAME.|  
|**CONNECTION_HOST_NAME**|**DBTYPE_WSTR**|Sí|Nombre del equipo que inició la conexión.|  
|**CONNECTION_HOST_APPLICATION**|**DBTYPE_WSTR**||Nombre de la aplicación que inició la conexión.|  
|**CONNECTION_START_TIME**|**DBTYPE_DBTIMESTAMP**||Fecha y hora UTC del servidor cuando se inició la conexión.|  
|**CONNECTION_ELAPSED_TIME_MS**|**DBTYPE_I8**|Sí|Tiempo transcurrido, en milisegundos, desde el inicio de la conexión.|  
|**CONNECTION_LAST_COMMAND_START_TIME**|**DBTYPE_DBTIMESTAMP**||Fecha y hora UTC del servidor cuando se inició la ejecución del último comando.|  
|**CONNECTION_LAST_COMMAND_END_TIME**|**DBTYPE_DBTIMESTAMP**||Fecha y hora UTC del servidor al finalizar la ejecución del último comando.|  
|**CONNECTION_LAST_COMMAND_ELAPSED_TIME_MS**|**DBTYPE_I8**|Sí|Tiempo transcurrido, en milisegundos, desde el fin del último comando ejecutado.|  
|**CONNECTION_IDLE_TIME_MS**|**DBTYPE_I8**|Sí|Tiempo de inactividad, en milisegundos, desde el inicio de la conexión.|  
|**CONNECTION_BYTES_SENT**|**DBTYPE_I8**||Número acumulado de bytes enviados por la conexión desde el inicio de la conexión.|  
|**CONNECTION_DATA_BYTES_SENT**|**DBTYPE_I8**||Número acumulado de bytes de datos enviados por la conexión desde el inicio de la conexión.<br /><br /> Los datos viajan comprimidos dentro de la conexión; este valor representa los datos expandidos enviados.|  
|**CONNECTION_BYTES_RECEIVED**|**DBTYPE_I8**||Número acumulado de bytes recibidos por la conexión desde el inicio de la conexión.|  
|**CONNECTION_DATA_BYTES_RECEIVED**|**DBTYPE_I8**||Número acumulado de bytes de datos recibidos por la conexión desde el inicio de la conexión.<br /><br /> Los datos viajan comprimido dentro de la conexión; este valor representa los datos expandidos recibidos.|  
  
 Este conjunto de filas de esquema no está ordenado.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Usar ADOMD.NET para devolver el conjunto de filas  
 Cuando se utilizan ADOMD.NET y el conjunto de filas de esquema para recuperar metadatos, puede utilizar el GUID o una cadena para hacer referencia a un objeto de conjunto de filas de esquema del método GetSchemaDataSet. Para obtener más información, vea [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 La tabla siguiente proporciona el GUID y los valores de cadena que identifican este conjunto de filas.  
  
|Argumento|Valor|  
|--------------|-----------|  
|GUID|a07ccd25-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|Conexiones|  
  
## <a name="see-also"></a>Vea también  
 [XML para conjuntos de filas de esquema de análisis](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
