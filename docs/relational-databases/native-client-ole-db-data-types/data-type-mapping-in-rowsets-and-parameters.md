---
title: Asignación de tipos de datos en parámetros y conjuntos de filas | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- mapping data types [OLE DB]
- DBTYPE_SQLVARIANT data type
- SQL Server Native Client OLE DB provider, data types
- rowsets [OLE DB], data type mapping
- data types [OLE DB]
- GetColumnInfo function
- parameters [OLE DB]
- SSPROP_ALLOWNATIVEVARIANT property
- GetParameterInfo function
- OLE DB, data types
ms.assetid: 3d831ff8-3b79-4698-b2c1-2b5dd2f8235c
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: ea9322153c59e3d83e07504236df82b0aa7b3272
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2018
ms.locfileid: "37413964"
---
# <a name="data-type-mapping-in-rowsets-and-parameters"></a>Asignar tipos de datos en conjuntos de filas y parámetros
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  En los conjuntos de filas y como valores de parámetro, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] representa el proveedor OLE DB de Native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] datos mediante el uso de las siguientes DB OLE definen los tipos de datos, notificados en las funciones **IColumnsInfo:: GetColumnInfo** y  **ICommandWithParameters:: GetParameterInfo**.  
  
|Tipo de datos de SQL Server|Tipo de datos de OLE DB|  
|--------------------------|----------------------|  
|**bigint**|DBTYPE_I8|  
|**binario**|DBTYPE_BYTES|  
|**bit**|DBTYPE_BOOL|  
|**char**|DBTYPE_STR|  
|**datetime**|DBTYPE_DBTIMESTAMP|  
|**datetime2**|DBTYPE_DBTIME2|  
|**decimal**|DBTYPE_NUMERIC|  
|**float**|DBTYPE_R8|  
|**imagen**|DBTYPE_BYTES|  
|**int**|DBTYPE_I4|  
|**money**|DBTYPE_CY|  
|**nchar**|DBTYPE_WSTR|  
|**ntext**|DBTYPE_WSTR|  
|**numeric**|DBTYPE_NUMERIC|  
|**nvarchar**|DBTYPE_WSTR|  
|**real**|DBTYPE_R4|  
|**smalldatetime**|DBTYPE_DBTIMESTAMP|  
|**smallint**|DBTYPE_I2|  
|**smallmoney**|DBTYPE_CY|  
|**sql_variant**|DBTYPE_VARIANT, DBTYPE_SQLVARIANT|  
|**sysname**|DBTYPE_WSTR|  
|**texto**|DBTYPE_STR|  
|**timestamp**|DBTYPE_BYTES|  
|**tinyint**|DBTYPE_UI1|  
|**UDT**|DBTYPE_UDT|  
|**uniqueidentifier**|DBTYPE_GUID|  
|**varbinary**|DBTYPE_BYTES|  
|**varchar**|DBTYPE_STR|  
|**XML**|DBTYPE_XML|  
  
 El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de Native Client admite conversiones solicitadas por el consumidor de datos tal como se muestra en la ilustración.  
  
 El **sql_variant** objetos pueden contener datos de cualquier [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de tipos de datos, excepto el texto, ntext, image, varchar (max), nvarchar (max), varbinary (max), xml, timestamp y common language runtime (CLR) de Microsoft .NET Framework tipos definidos por el usuario. Una instancia de datos sql_variant no puede tener sql_variant como tipo de datos base subyacente. Por ejemplo, la columna puede contener **smallint** valores para algunas filas, **float** valores en otras filas y **char**/**nchar**valores en el resto.  
  
> [!NOTE]  
>  El **sql_variant** tipo de datos es similar al tipo de datos Variant en Microsoft Visual Basic® y DBTYPE_VARIANT, DBTYPE_SQLVARIANT de OLEDB.  
  
 Cuando **sql_variant** los datos se capturan como DBTYPE_VARIANT, se incluyen en una estructura VARIANT en el búfer. Pero los subtipos de la estructura VARIANT no se pueden asignar a los subtipos definidos en el **sql_variant** tipo de datos. El **sql_variant** datos se deben capturar como DBTYPE_SQLVARIANT en orden para todos los subtipos coincidan.  
  
## <a name="dbtypesqlvariant-data-type"></a>Tipo de datos DBTYPE_SQLVARIANT  
 Para admitir la **sql_variant** tipo de datos, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de Native Client expone un tipo de datos específico del proveedor denominado DBTYPE_SQLVARIANT. Cuando **sql_variant** en los datos se capturan como DBTYPE_SQLVARIANT, se almacena en una estructura SSVARIANT específica del proveedor. La estructura SSVARIANT contiene todos los subtipos que coinciden con los subtipos de los **sql_variant** tipo de datos.  
  
 La propiedad SSPROP_ALLOWNATIVEVARIANT de la sesión también debe estar establecida en TRUE.  
  
## <a name="provider-specific-property-sspropallownativevariant"></a>Propiedad SSPROP_ALLOWNATIVEVARIANT específica del proveedor  
 Al capturar los datos, puede especificar explícitamente qué clase de tipo de datos se debería devolver para una columna o para un parámetro. **IColumnsInfo** también puede utilizarse para obtener la información de columna y usarla para crear el enlace. Cuando **IColumnsInfo** se usa para obtener información de columna para fines de enlace, si la sesión SSPROP_ALLOWNATIVEVARIANT la propiedad es FALSE (valor predeterminado), se devuelve DBTYPE_VARIANT **sql_variant**columnas. Si la propiedad SSPROP_ALLOWNATIVEVARIANT es FALSE, no se admite DBTYPE_SQLVARIANT. Si la propiedad SSPROP_ALLOWNATIVEVARIANT está establecida en TRUE, el tipo de columna se devuelve como DBTYPE_SQLVARIANT, en cuyo caso el búfer contendrá la estructura SSVARIANT. En la captura de **sql_variant** datos como DBTYPE_SQLVARIANT, la propiedad SSPROP_ALLOWNATIVEVARIANT de sesión debe establecerse en TRUE.  
  
 La propiedad SSPROP_ALLOWNATIVEVARIANT forma parte del conjunto de propiedades DBPROPSET_SQLSERVERSESSION específico del proveedor y es una propiedad de sesión.  
  
 DBTYPE_VARIANT se aplica a todos los demás proveedores OLE DB.  
  
## <a name="sspropallownativevariant"></a>SSPROP_ALLOWNATIVEVARIANT  
 SSPROP_ALLOWNATIVEVARIANT es una propiedad de sesión y forma parte del conjunto de propiedades DBPROPSET_SQLSERVERSESSION.  
  
|||  
|-|-|  
|SSPROP_ALLOWNATIVEVARIANT|Tipo: VT_BOOL<br /><br /> L/E: de lectura/escritura<br /><br /> Valor predeterminado: VARIANT_FALSE<br /><br /> Descripción: determina si los datos se capturan como DBTYPE_VARIANT o DBTYPE_SQLVARIANT.<br /><br /> VARIANT_TRUE: el tipo de columna se devuelve como DBTYPE_SQLVARIANT, en cuyo caso el búfer contendrá la estructura SSVARIANT.<br /><br /> VARIANT_FALSE: el tipo de columna se devuelve como DBTYPE_VARIANT y el búfer contendrá la estructura VARIANT.|  
  
## <a name="see-also"></a>Vea también  
 [Tipos de datos &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-types/data-types-ole-db.md)  
  
  
