---
title: Conjunto de filas DISCOVER_LOCATIONS | Documentos de Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 63a3f01b25b189f34df3f328c1709255752f7210
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="discoverlocations-rowset"></a>Conjunto de filas DISCOVER_LOCATIONS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Devuelve información sobre el contenido de un archivo de copia de seguridad. Debe tener permiso de acceso a la ubicación del archivo de copia de seguridad.  
  
## <a name="rowset-columns"></a>Columnas del conjunto de filas  
 El conjunto de filas **DISCOVER_LOCATIONS** contiene las siguientes columnas.  
  
|Nombre de columna|Indicador de tipo|Restricción|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**LOCATION_BACKUP_FILE_PATHNAME**|**DBTYPE_WSTR**|Requerido, vea más abajo.|La ubicación del archivo de copia de seguridad.|  
|**LOCATION_PARTITION_OBJECTPATH**|**DBTYPE_WSTR**||La ruta de acceso a la partición relativa a la carpeta de datos.|  
|**LOCATION_PARTITION_DATASOURCEID**|**DBTYPE_WSTR**||El identificador de origen de datos usado para procesar la partición.|  
|**LOCATION_PARTITION_DATASOURCENAME**|**DBTYPE_WSTR**||El nombre del origen de datos utilizado para el procesamiento.|  
|**LOCATION_PARTITION_NAME**|**DBTYPE_WSTR**||El nombre de la partición.|  
|**LOCATION_PARTITION_SIZE**|**DBTYPE_WSTR**||El tamaño aproximado de la partición.|  
|**LOCATION_CONNECTION_STRING**|**DBTYPE_WSTR**||La cadena de conexión para el origen de datos que se utiliza en el procesamiento.|  
|**LOCATION_PARTITION_FOLDER**|**DBTYPE_WSTR**||La ubicación original de esta partición cuando se ha generado el archivo de copia de seguridad.|  
  
 Este conjunto de filas de esquema no está ordenado.  
  
## <a name="restriction-columns"></a>Columnas de restricción  
 El conjunto de filas **DISCOVER_LOCATIONS** puede tener restricciones en las columnas que se muestran en la tabla siguiente.  
  
|Nombre de columna|Indicador de tipo|Estado de restricción|  
|-----------------|--------------------|-----------------------|  
|**LOCATION_BACKUP_FILE_PATHNAME**|**DBTYPE_WSTR**|Obligatorio|  
|**LOCATION_PASSWORD PF_DBTYPE**|**DBTYPE_WSTR**|Requerido si se especificó durante la copia de seguridad. Esta restricción no se utiliza para limitar las filas devueltas. Se utiliza para proporcionar la contraseña para tener acceso a la ubicación.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Usar ADOMD.NET para devolver el conjunto de filas  
 Cuando se utilizan ADOMD.NET y el conjunto de filas de esquema para recuperar metadatos, puede utilizar el GUID o una cadena para hacer referencia a un objeto de conjunto de filas de esquema del método GetSchemaDataSet. Para obtener más información, vea [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 La tabla siguiente proporciona el GUID y los valores de cadena que identifican este conjunto de filas.  
  
|Argumento|Valor|  
|--------------|-----------|  
|GUID|a07ccd92-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|Ubicaciones|  
  
## <a name="see-also"></a>Vea también  
 [XML para conjuntos de filas de esquema de análisis](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
