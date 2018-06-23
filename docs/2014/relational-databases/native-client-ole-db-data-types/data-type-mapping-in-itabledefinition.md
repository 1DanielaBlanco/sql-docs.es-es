---
title: Asignación de tipo de datos en ITableDefinition | Documentos de Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- mapping data types [OLE DB]
- SQL Server Native Client OLE DB provider, data types
- ITableDefinition interface
- DBCOLUMNDESC structure
- data types [OLE DB]
- CreateTable function
- OLE DB, data types
ms.assetid: 13292d1f-c17e-4d11-bf98-3460a10cbb18
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c09ac0e561f06236a9580ae7a84ed892ca1fcd31
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36110922"
---
# <a name="data-type-mapping-in-itabledefinition"></a>Asignación de tipos de datos en ITableDefinition
  Cuando se crean tablas utilizando la **ITableDefinition:: CreateTable** función, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consumidor del proveedor OLE DB de Native Client puede especificar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipos de datos de la *pwszTypeName* miembro de la matriz DBCOLUMNDESC que se pasa. Si el consumidor especifica el tipo de datos de una columna por su nombre, los datos de OLE DB escriba asignación, representada por la *wType* miembro de la estructura DBCOLUMNDESC, se omite.  
  
 Al especificar los nuevos tipos de datos de columna con tipos de datos de OLE DB mediante la estructura DBCOLUMNDESC *wType* miembro, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor de OLE DB de Native Client asigna tipos de datos OLE DB como se indica a continuación.  
  
|Tipo de datos de OLE DB|SQL Server<br /><br /> tipo de datos|Información adicional|  
|----------------------|------------------------------|----------------------------|  
|DBTYPE_BOOL|**bit**||  
|DBTYPE_BYTES|**binario**, **varbinary**, **imagen,** o **varbinary (max)**|El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de Native Client inspecciona el *ulColumnSize* miembro de la estructura DBCOLUMNDESC. Según el valor y la versión de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instancia, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de Native Client asigna el tipo a **imagen**.<br /><br /> Si el valor de *ulColumnSize* es menor que la longitud máxima de un **binario** columna de tipo de datos, la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de Native Client inspecciona el miembro  *rgPropertySets* miembro. Si DBPROP_COL_FIXEDLENGTH es VARIANT_TRUE, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de Native Client asigna el tipo a **binario**. Si el valor de la propiedad es VARIANT_FALSE, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de Native Client asigna el tipo a **varbinary**. En cualquier caso, el miembro *ulColumnSize* miembro determina el ancho de la columna de SQL Server creada.|  
|DBTYPE_CY|**money**||  
|DBTYPE_DBTIMESTAMP|**datetime**||  
|DBTYPE_GUID|**uniqueidentifier**||  
|DBTYPE_I2|**smallint**||  
|DBTYPE_I4|**int**||  
|DBTYPE_NUMERIC|**numeric**|El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de Native Client inspecciona los miembros *bPrecision* y *bScale* miembros para determinar la precisión y escala para la **numérico** columna.|  
|DBTYPE_R4|**real**||  
|DBTYPE_R8|**float**||  
|DBTYPE_STR|**char**, **varchar**, **texto,** o **varchar (max)**|El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de Native Client inspecciona el *ulColumnSize* miembro de la estructura DBCOLUMNDESC. Según el valor y la versión de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instancia, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de Native Client asigna el tipo a **texto**.<br /><br /> Si el valor de *ulColumnSize* es menor que la longitud máxima de una columna de tipo de datos de caracteres multibyte, la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de Native Client inspecciona el miembro *rgPropertySets*miembro. Si DBPROP_COL_FIXEDLENGTH es VARIANT_TRUE, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de Native Client asigna el tipo a **char**. Si el valor de la propiedad es VARIANT_FALSE, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de Native Client asigna el tipo a **varchar**. En cualquier caso, el miembro *ulColumnSize* miembro determina el ancho de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] columna creada.|  
|DBTYPE_UDT|**UDT**|La siguiente información se usa en `DBCOLUMNDESC` estructuras **ITableDefinition:: CreateTable** cuando se requieren columnas UDT:<br /><br /> -   *pwSzTypeName* se omite.<br />-   *rgPropertySets* debe incluir un `DBPROPSET_SQLSERVERCOLUMN` propiedad establecida tal y como se describe en la sección sobre `DBPROPSET_SQLSERVERCOLUMN`, en [Defined Types](../native-client/features/using-user-defined-types.md).|  
|DBTYPE_UI1|**tinyint**||  
|DBTYPE_WSTR|**nchar**, **nvarchar**, **ntext,** o **nvarchar (max)**|El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de Native Client inspecciona el *ulColumnSize* miembro de la estructura DBCOLUMNDESC. En función del valor, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de Native Client asigna el tipo a **ntext**.<br /><br /> Si el valor de *ulColumnSize* es menor que la longitud máxima de una columna de tipo de datos de caracteres Unicode, la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de Native Client inspecciona el miembro *rgPropertySets*miembro. Si DBPROP_COL_FIXEDLENGTH es VARIANT_TRUE, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de Native Client asigna el tipo a **nchar**. Si el valor de la propiedad es VARIANT_FALSE, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de Native Client asigna el tipo a **nvarchar**. En cualquier caso, el miembro *ulColumnSize* miembro determina el ancho de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] columna creada.|  
|DBTYPE_XML|**XML**||  
  
> [!NOTE]  
>  Cuando se crea una nueva tabla, el proveedor OLE DB de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client solamente asigna los valores de enumeración del tipo de datos de OLE DB especificado en la tabla anterior. Al intentar crear una tabla con una columna de cualquier otro tipo de datos de OLE DB, se genera un error.  
  
## <a name="see-also"></a>Vea también  
 [Tipos de datos &#40;OLE DB&#41;](data-types-ole-db.md)  
  
  