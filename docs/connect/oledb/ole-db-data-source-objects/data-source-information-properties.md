---
title: Propiedades de información del origen de datos | Microsoft Docs
description: Propiedades de información de orígenes de datos
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-data-source-objects
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, data source properties
- properties [OLE DB]
- data source properties [OLE DB]
- information properties [OLE DB]
- OLE DB data source properties [OLE DB Driver for SQL Server]
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 06a6f4152876f123d1e7fc7ecaf009061d10aa59
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "43031958"
---
# <a name="data-source-information-properties"></a>Propiedades de información de orígenes de datos
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  En el conjunto de propiedades específico del proveedor DBPROPSET_SQLSERVERDATASOURCEINFO, el controlador OLE DB para SQL Server define las siguientes propiedades de información del origen de datos.  
  
|Id. de propiedad|Descripción|  
|-----------------|-----------------|  
|SSPROP_COLUMNLEVELCOLLATION|Tipo: VT_BOOL<br /><br /> L/E: Lectura<br /><br /> Valor predeterminado: VARIANT_TRUE<br /><br /> Descripción: Se utiliza para determinar si se admite la intercalación de columnas.<br /><br /> VARIANT_TRUE: Se admite la intercalación de columnas.<br /><br /> VARIANT_FALSE: No se admite la intercalación de columnas.|  
|SSPROP_UNICODELCID|Tipo: VT_I4 L/E: Lectura<br /><br /> Descripción: Id. de configuración regional de Unicode.<br /><br /> Se trata de la configuración regional utilizada para ordenar datos Unicode.|  
|SSPROP_UNICODECOMPARISONSTYLE|Tipo: VT_I4 L/E: Lectura<br /><br /> Descripción: Estilo de comparación Unicode.<br /><br /> Las opciones de ordenación utilizadas para ordenar datos Unicode.|  
  
 En el conjunto de propiedades específico del proveedor DBPROPSET_SQLSERVERSTREAM, el controlador OLE DB para SQL Server define la propiedad adicional siguiente.  
  
|Id. de propiedad|Descripción|  
|-----------------|-----------------|  
|SSPROP_STREAM_XMLROOT|Tipo: VT_BSTR L/E: Lectura/escritura<br /><br /> Descripción: El resultado de una consulta FOR XML podría no ser un documento bien formado. Cuando se especifica esta propiedad, el resultado de un ' Seleccionar... para XML' consulta se ajusta en la etiqueta proporcionada por esta propiedad para devolver un documento XML bien formado. Si la consulta se ejecuta en el explorador, puede hacer que el explorador muestre los errores de análisis al cargar el resultado. Para evitar el error, SQL ISAPI admite la palabra clave ROOT. Esta palabra clave se asigna a la propiedad SSPROP_STREAM_XMLROOT.|  
  
## <a name="see-also"></a>Ver también  
 [Objetos de origen de datos &#40;OLE DB&#41;](../../oledb/ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
