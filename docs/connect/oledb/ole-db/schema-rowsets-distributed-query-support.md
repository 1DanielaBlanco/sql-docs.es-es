---
title: Compatibilidad con consultas de conjuntos de filas de esquema distribuidas | Documentos de Microsoft
description: Compatibilidad con la consulta en conjuntos de filas de esquema distribuido
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- DBPROPSET_SQLSERVERSESSION property
- schema rowsets [OLE DB]
- distributed queries [SQL Server], OLE DB Driver for SQL Server
- OLE DB, schema rowsets
- OLE DB rowsets, schema
- rowsets [OLE DB], schema
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 26cf4847d1d4f9e6799b2751e81a44e9cc4bcc72
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2018
---
# <a name="schema-rowsets---distributed-query-support"></a>Conjuntos de filas de esquema - compatibilidad con consultas distribuidas
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Para admitir [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] consultas, el controlador OLE DB para SQL Server distribuidas **IDBSchemaRowset** interfaz devuelve los metadatos de servidores vinculados.  
  
 Si la propiedad SSPROP_QUOTEDCATALOGNAMES de DBPROPSET_SQLSERVERSESSION es VARIANT_TRUE, puede especificarse un identificador entrecomillado para el nombre del catálogo (por ejemplo, "my.catalog"). Al restringir los resultados de conjunto de filas de esquema por catálogo, el controlador OLE DB para SQL Server reconoce un nombre de dos partes que contiene el servidor vinculado y el nombre del catálogo. Para los conjuntos de filas de esquema en la tabla siguiente, especificando un nombre de catálogo de dos partes como *servidor_vinculado***.*** catálogo* restringe la salida al catálogo aplicable del servidor vinculado con nombre.  
  
|Conjunto de filas de esquema|Restricción de catálogo|  
|-------------------|-------------------------|  
|DBSCHEMA_CATALOGS|CATALOG_NAME|  
|DBSCHEMA_COLUMNS|TABLE_CATALOG|  
|DBSCHEMA_PRIMARY_KEYS|TABLE_CATALOG|  
|DBSCHEMA_TABLES|TABLE_CATALOG|  
|DBSCHEMA_FOREIGN_KEYS|PK_TABLE_CATALOG FK_TABLE_CATALOG|  
|DBSCHEMA_INDEXES|TABLE_CATALOG|  
|DBSCHEMA_COLUMN_PRIVILEGES|TABLE_CATALOG|  
|DBSCHEMA_TABLE_PRIVILEGES|TABLE_CATALOG|  
  
> [!NOTE]  
>  Para impedir que un conjunto de filas de esquema para todos los catálogos de un servidor vinculado, utilice la sintaxis *linked_server* (donde el separador punto forma parte de la especificación del nombre). Esta sintaxis equivale a especificar NULL para la restricción del nombre de catálogo y también se utiliza cuando el servidor vinculado indica un origen de datos que no admite catálogos.  
  
 El controlador OLE DB para SQL Server define el conjunto de filas de esquema LINKEDSERVERS y devuelve una lista de orígenes de datos OLE DB registrados como servidores vinculados.  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con el conjunto de filas de esquema &#40;OLE DB&#41;](../../oledb/ole-db/schema-rowset-support-ole-db.md)   
 [Conjunto de filas LINKEDSERVERS &#40;OLE DB&#41;](../../oledb/ole-db/schema-rowsets-linkedservers-rowset.md)  
  
  