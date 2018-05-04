---
title: Conjunto de filas DISCOVER_COMMANDS | Documentos de Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_COMMANDS rowset
ms.assetid: d228f265-05d9-4d2c-a622-44c73eab7a71
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: dd2f0de8cec9c9155595a0da7219ce966ef54fdb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="discovercommands-rowset"></a>DISCOVER_COMMANDS, conjunto de filas
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Proporciona información de la actividad y el uso de recursos sobre los comandos que se están ejecutando actualmente o los que se ejecutaron los últimos en las conexiones abiertas en el servidor.  
  
 **Se aplica a:** modelos tabulares, modelos multidimensionales  
  
## <a name="rowset-columns"></a>Columnas del conjunto de filas  
 El conjunto de filas **DISCOVER_COMMANDS** contiene las siguientes columnas.  
  
|Nombre de columna|Indicador de tipo|Restricción|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**SESSION_SPID**|**DBTYPE_I4**|Sí|Identificador de la sesión.|  
|**SESSION_COMMAND_COUNT**|**DBTYPE_I4**||Número de comandos ejecutados desde el inicio de la sesión.|  
|**COMMAND_START_TIME**|**DBTYPE_DBTIMESTAMP**||Fecha y hora en que se inició el último comando, expresadas como la hora UTC en el servidor.|  
|**COMMAND_ELAPSED_TIME_MS**|**DBTYPE_I8**||Tiempo transcurrido, en milisegundos, desde el inicio del comando.|  
|**COMMAND_CPU_TIME_MS**|**DBTYPE_I8**||Tiempo de CPU, en milisegundos, consumido por el comando desde el inicio de su ejecución.|  
|**COMMAND_READS**|**DBTYPE_I8**||Número acumulado de lecturas de disco desde el inicio del comando.|  
|**COMMAND_READ_KB**|**DBTYPE_I8**||Valor acumulado de los datos leídos del disco desde el inicio del comando, en kilobytes.|  
|**COMMAND_WRITES**|**DBTYPE_I8**||Número acumulado de escrituras en disco desde el inicio del comando.|  
|**COMMAND_WRITE_KB**|**DBTYPE_I8**||Valor acumulado de los datos escritos en el disco desde el inicio del comando, en kilobytes.|  
|**COMMAND_TEXT**|**DBTYPE_WSTR**||El texto del comando.|  
|**COMMAND_END_TIME**|**DBTYPE_DBTIMESTAMP**||Fecha y hora UTC del servidor en que el comando finaliza su ejecución.|  
  
 Este conjunto de filas de esquema no está ordenado.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Usar ADOMD.NET para devolver el conjunto de filas  
 Cuando se utilizan ADOMD.NET y el conjunto de filas de esquema para recuperar metadatos, puede utilizar el GUID o una cadena para hacer referencia a un objeto de conjunto de filas de esquema del método GetSchemaDataSet. Para obtener más información, vea [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 La tabla siguiente proporciona el GUID y los valores de cadena que identifican este conjunto de filas.  
  
|Argumento|Valor|  
|--------------|-----------|  
|GUID|a07ccd34-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|Comandos|  
  
## <a name="see-also"></a>Vea también  
 [XML para conjuntos de filas de esquema de análisis](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
