---
title: Conjunto de filas DISCOVER_SESSIONS | Documentos de Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DISCOVER_SESSIONS rowset
ms.assetid: 47a79542-3142-4e62-a66f-6c4dbfe0f5c0
caps.latest.revision: "18"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5f8fef815cbb4a648bacb6ab90a40bfc41d57d3e
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2017
---
# <a name="discoversessions-rowset"></a>DISCOVER_SESSIONS, conjunto de filas
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Proporciona información de actividad y el uso de recursos acerca de las sesiones abiertas actualmente en el servidor.  
  
## <a name="rowset-columns"></a>Columnas del conjunto de filas  
 El conjunto de filas **DISCOVER_SESSIONS** contiene las siguientes columnas.  
  
|Nombre de columna|Indicador de tipo|Longitud|Description|  
|-----------------|--------------------|------------|-----------------|  
|**SESSION_COMMAND_COUNT**|**DBTYPE_I4**||Número de comandos que comenzaron a ejecutarse desde el principio de la sesión.|  
|**SESSION_CONNECTION_ID**|**DBTYPE_I4**||Identificador de conexión de la sesión.|  
|**SESSION_CPU_TIME_MS**|**DBTYPE_UI8**||Tiempo de CPU, en milisegundos, consumido por todas las solicitudes desde el principio de la sesión.|  
|**SESSION_CURRENT_DATABASE**|**DBTYPE_WSTR**||Nombre de la base de datos que utiliza la ejecución del comando actual o de la base de datos que utilizó el último comando ejecutado.|  
|**SESSION_ELAPSED_TIME_MS**|**DBTYPE_UI8**||Tiempo transcurrido, en milisegundos, desde el inicio de la sesión.|  
|**SESSION_ID**|**DBTYPE_WSTR**||Identificador único de la sesión, como un GUID.|  
|**SESSION_IDLE_TIME_MS**|**DBTYPE_UI8**||Tiempo de inactividad, en milisegundos, desde el inicio de la sesión.|  
|**SESSION_LAST_COMMAND**|**DBTYPE_WSTR**||Texto del comando que se está ejecutando actualmente o del último comando ejecutado.|  
|**SESSION_LAST_COMMAND_CPU_TIME_MS**|**DBTYPE_UI8**||Tiempo de CPU, en milisegundos, consumido por **SESSION_LAST_COMMAND**.|  
|**SESSION_LAST_COMMAND_ELAPSED_TIME_MS**|**DBTYPE_UI8**||Tiempo transcurrido, en milisegundos, desde el inicio de **SESSION_LAST_COMMAND**.|  
|**SESSION_LAST_COMMAND_END_TIME**|**DBTYPE_DBTIMESTAMP**||Hora UTC del servidor en el momento en que terminó de ejecutarse el último comando.|  
|**SESSION_LAST_COMMAND_START_TIME**|**DBTYPE_DBTIMESTAMP**||Hora UTC del servidor en el momento en que comenzó a ejecutarse el último comando.|  
|**SESSION_PROPERTIES**|**DBTYPE_WSTR**||Reservado para uso futuro.|  
|**SESSION_READ_KB**|**DBTYPE_UI8**||Valor acumulado de los datos leídos del disco desde el inicio de la sesión, en kilobytes.|  
|**SESSION_READS**|**DBTYPE_UI8**||Número acumulado de lecturas de disco desde el inicio de la sesión.|  
|**SESSION_SPID**|**DBTYPE_I4**||Identificador de la sesión.|  
|**SESSION_START_TIME**|**DBTYPE_DBTIMESTAMP**||Fecha y hora en que se inició la sesión como hora UTC para el servidor.|  
|**SESSION_STATUS**|**DBTYPE_I4**||Estado de actividad de la sesión.<br /><br /> 0 significa "Inactivo": No hay ninguna actividad actual en curso.<br /><br /> 1 significa "Activo": La sesión está ejecutando alguna tarea solicitada.<br /><br /> 2 significa "Bloqueado": La sesión está esperando que algún recurso continúe ejecutando la tarea suspendida.<br /><br /> 3 significa "Cancelado": La sesión se ha etiquetado como cancelada.|  
|**SESSION_USED_MEMORY**|**DBTYPE_I4**||Tamaño actual de la memoria utilizada por la sesión, en kilobytes. El valor notificado es el uso de RAM por SPID, sin distinción entre la memoria reducible y la no reducible. A diferencia de otras DMV que notifican el uso de memoria, DISCOVER_SESSIONS no divide el uso de memoria por categorías.<br /><br /> Tenga en cuenta que SESSION_USED_MEMORY tiende a notificar valores de uso de memoria inferiores a los reales, porque excluye los objetos compartidos entre varias sesiones.  Solo se representan en el cálculo de memoria aquellos objetos que son únicos en la sesión.|  
|**SESSION_USER_NAME**|**DBTYPE_WSTR**||Nombre de usuario de la sesión.|  
|**SESSION_WRITE_KB**|**DBTYPE_UI8**||Valor acumulado de los datos escritos en el disco desde el inicio de la sesión, en kilobytes.|  
|**SESSION_WRITES**|**DBTYPE_UI8**||Número acumulado de escrituras en disco desde el inicio de la sesión.|  
  
 Este conjunto de filas de esquema no está ordenado.  
  
## <a name="restriction-columns"></a>Columnas de restricción  
 El conjunto de filas **DISCOVER_SESSIONS** puede tener restricciones en las columnas que se muestran en la tabla siguiente.  
  
|Nombre de columna|Indicador de tipo|Estado de restricción|  
|-----------------|--------------------|-----------------------|  
|SESSION_ID|DBTYPE_WSTR|Opcional.|  
|SESSION_SPID|DBTYPE_I4|Opcional.|  
|SESSION_CONNECTION_ID|DBTYPE_I4|Opcional.|  
|SESSION_USER_NAME|DBTYPE_WSTR|Opcional.|  
|SESSION_CURRENT_DATABASE|DBTYPE_WSTR|Opcional.|  
|SESSION_ELAPSED_TIME_MS|DBTYPE_UI8|Opcional.|  
|SESSION_CPU_TIME_MS|DBTYPE_UI8|Opcional.|  
|SESSION_IDLE_TIME_MS|DBTYPE_UI8|Opcional.|  
|SESSION_STATUS|DBTYPE_I4|Opcional.|  
  
## <a name="see-also"></a>Vea también  
 [Conjuntos de filas de esquema de XML for Analysis](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
